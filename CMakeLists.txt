cmake_minimum_required(VERSION 2.8)

project(pt_grey_ros_driver)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  image_transport
)

include_directories(
  include
  /usr/include/flycapture
  ${catkin_INCLUDE_DIRS}
)
add_definitions(-g)

add_executable(pgr_camera_node 
  src/pgr_camera.cpp 
  src/pgr_camera_node.cpp)


target_link_libraries(pgr_camera_node
                      flycapture
                      ${catkin_LIBRARIES}
                      ${image_transport_LIBRARIES})

catkin_package(
    CATKIN_DEPENDS tf
)

#	install(PROGRAMS
#		flytest
#		DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
#	)
install(TARGETS 
        RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
