project(gco)
cmake_minimum_required(VERSION 2.8)

if (NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Release")
endif()

set(lib_srcs
    GCoptimization.cpp
    GCoptimization.h
    LinkedBlockList.cpp
    LinkedBlockList.h
    block.h
    energy.h
    graph.h
    )

set(example_srcs
    example.cpp)

add_library(gco ${lib_srcs})
add_executable(example ${example_srcs})
target_link_libraries(example gco)

install(TARGETS gco
        ARCHIVE DESTINATION "${CMAKE_INSTALL_PREFIX}/lib"
        LIBRARY DESTINATION "${CMAKE_INSTALL_PREFIX}/lib"
        COMPONENT library)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
        DESTINATION "${CMAKE_INSTALL_PREFIX}/include"
        FILES_MATCHING PATTERN "*.h" PATTERN "*.inl")

