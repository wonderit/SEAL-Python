cmake_minimum_required(VERSION 3.16)
project(seal)

set(CMAKE_GENERATOR_PLATFORM Win32 CACHE INTERNAL "Force 32-bit compilation")

add_subdirectory(pybind11)
pybind11_add_module(seal src/wrapper.cpp)

include_directories(SEAL/build)
include_directories(SEAL/build/native/src)
include_directories(SEAL/build/lib)

target_compile_definitions(seal PRIVATE VERSION_INFO=${EXAMPLE_VERSION_INFO})
link_libraries(seal-4.0.lib)
