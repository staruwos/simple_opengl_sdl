cmake_minimum_required(VERSION 3.10)

project(SimpleOpenGLApp)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(OpenGL REQUIRED)

find_package(GLEW REQUIRED)

find_package(SDL2 REQUIRED)

# Find all .cpp files in the src/ directory
file(GLOB SRC_FILES "src/*.cpp")

# Create the executable from the collected source files
add_executable(simple_gl_app ${SRC_FILES})

# Allows source files in src/ to #include headers also in src/
target_include_directories(simple_gl_app PRIVATE src)


file(COPY
	${PROJECT_SOURCE_DIR}/data/
	DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/data/
)

target_link_libraries(simple_gl_app
PRIVATE
OpenGL::GL
GLEW::GLEW
SDL2::SDL2
)

message(STATUS "OpenGL include dirs: ${OPENGL_INCLUDE_DIR}")

message(STATUS "GLEW include dirs: ${GLEW_INCLUDE_DIR}")

message(STATUS "SDL2 include dirs: ${SDL2_INCLUDE_DIRS}")
