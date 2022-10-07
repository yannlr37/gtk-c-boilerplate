cmake_minimum_required(VERSION 2.8)

project( app )
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/build)

find_package( PkgConfig REQUIRED )
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

include_directories( ${GTK3_INCLUDE_DIRS} )
link_directories( ${GTK3_LIBRARY_DIRS} )

add_definitions( ${GTK3_CFLAGS_OTHER} )

file(GLOB all_SRCS
	"${PROJECT_SOURCE_DIR}/sources/*.h"
	"${PROJECT_SOURCE_DIR}/sources/*.c"
)

add_executable( ${PROJECT_NAME} main.c ${all_SRCS} )

target_link_libraries( ${PROJECT_NAME} ${CMAKE_THREAD_LIBS_INIT} ${GTK3_LIBRARIES} )
