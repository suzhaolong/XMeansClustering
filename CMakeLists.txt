cmake_minimum_required(VERSION 2.6)

Project(XMeansClustering)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=gnu++0x")

include_directories(/media/portable/src/Eigen)

# Submodules

if(NOT TARGET KMeansClustering)
  add_subdirectory(KMeansClustering)
endif()

add_library(XMeansClustering XMeansClustering.cpp)
TARGET_LINK_LIBRARIES(XMeansClustering KMeansClustering)

ADD_EXECUTABLE(XMeansClusteringExample Example.cpp)
TARGET_LINK_LIBRARIES(XMeansClusteringExample XMeansClustering)
