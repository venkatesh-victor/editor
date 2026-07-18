cmake_minimum_required(VERSION 3.20)

project(sharanga LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(OpenGL REQUIRED)

add_subdirectory(external/glfw)

add_library(glad external/glad/src/gl.c)

target_include_directories(glad PUBLIC external/glad/include)

add_executable(sharanga
  src/main.cpp
)

target_link_libraries(sharanga PRIVATE 
  glfw
  glad
  OpenGL::GL
)