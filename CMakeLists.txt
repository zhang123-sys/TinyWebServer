cmake_minimum_required(VERSION 3.8) #最低CMake版本

project(TinyWebServer)


set(SOURCES main.cpp ./timer/lst_timer.cpp ./http/http_conn.cpp ./log/log.cpp 
./CGImysql/sql_connection_pool.cpp  webserver.cpp config.cpp)

option(BUILD_DEBUG_MODE "build server with debug mode?" OFF)

if(BUILD_DEBUG_MODE)
    add_compile_options(-g)
endif()

add_compile_options(-O2)

set(TARGET server)
add_executable(${TARGET} ${SOURCES})
# LINK_FLAGS(-lpthread -lmysqlclient)
target_link_libraries(${TARGET} -lpthread -lmysqlclient)

