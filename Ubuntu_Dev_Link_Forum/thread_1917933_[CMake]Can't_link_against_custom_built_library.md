---
title: "[CMake]Can't link against custom built library"
date: 2012-01-31
forum: Ubuntu Dev Link Forum
---

### Post by Jordanwb on 2012-01-31
In my project, I have a bunch of files compiled into a shared library. I also have some other files that include files that were compiled into that library. So when the executable is compiled, a link is made against that library. This is my CMakeLists.txt:

```
cmake_minimum_required (VERSION 2.6)
project (my_project)

include_directories ("${PROJECT_SOURCE_DIR}/src")

add_library (tah SHARED src/library.c)
add_executable(Client src/client.c)
add_executable(Server src/server.c)

target_link_libraries (Server tah)
target_link_libraries (Server mysqlclient)
target_link_libraries (Server json)
target_link_libraries (Server config)
target_link_libraries (Server readline)
target_link_libraries (Server crypto)
target_link_libraries (Server iconv)

```

When I run "make Server" it compiles the library, then the Server as proper but it can't link against the library:

```
$ make Server
Scanning dependencies of target tah
[ 50%] Building C object CMakeFiles/tah.dir/src/library.c.o
Linking C shared library cygtah.dll
Creating library file: libtah.dll.a
[ 50%] Built target tah
Scanning dependencies of target Server
[100%] Building C object CMakeFiles/Server.dir/src/server.c.o
In file included from /home/Jordan/my_project/src/server.c:40:
/home/Jordan/my_project/src/client_responses.h: In function `client_job_results':
/home/Jordan/my_project/src/client_responses.h:114: warning: assignment from incompatible pointer type
/home/Jordan/my_project/src/server.c: In function `main':
/home/Jordan/my_project/src/server.c:103: warning: passing arg 1 of `logger_initialize' discards qualifiers from pointer target type
/home/Jordan/my_project/src/server.c:167: warning: passing arg 3 of `config_lookup_int' from incompatible pointer type
Linking C executable Server.exe
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x4de): undefined reference to `_arraylist_create'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x6f8): undefined reference to `_arraylist_add'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x857): undefined reference to `_arraylist_add'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x15b2): undefined reference to `_command_book_close'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x15bf): undefined reference to `_plugin_list_free'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x15cc): undefined reference to `_event_collection_free'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1634): undefined reference to `_command_book_get_at'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1777): undefined reference to `_plugin_load_plugin'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1e0f): undefined reference to `_command_book_create'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1e31): undefined reference to `_command_book_add'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1e4e): undefined reference to `_command_book_add'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1e6b): undefined reference to `_command_book_add'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1e88): undefined reference to `_command_book_add'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1ea0): undefined reference to `_event_collection_create'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1eba): undefined reference to `_event_create'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1ecf): undefined reference to `_event_create'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1ee4): undefined reference to `_event_create'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1ef9): undefined reference to `_event_create'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1f11): undefined reference to `_plugin_create_list'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1f37): undefined reference to `_plugin_load_plugins'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1f86): undefined reference to `_plugin_init_plugins'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1fba): undefined reference to `_command_parse'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x1fd8): undefined reference to `_command_book_get'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x21e7): undefined reference to `_event_trigger'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x2356): undefined reference to `_event_trigger'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x2420): undefined reference to `_event_trigger'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x2840): undefined reference to `_event_trigger'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x2a5e): undefined reference to `_arraylist_free'
CMakeFiles/Server.dir/src/server.c.o:server.c:(.text+0x2ac2): undefined reference to `_event_trigger'
collect2: ld returned 1 exit status
CMakeFiles/Server.dir/build.make:86: recipe for target `Server.exe' failed
make[3]: *** [Server.exe] Error 1
CMakeFiles/Makefile2:95: recipe for target `CMakeFiles/Server.dir/all' failed
make[2]: *** [CMakeFiles/Server.dir/all] Error 2
CMakeFiles/Makefile2:107: recipe for target `CMakeFiles/Server.dir/rule' failed
make[1]: *** [CMakeFiles/Server.dir/rule] Error 2
Makefile:119: recipe for target `Server' failed
make: *** [Server] Error 2

```

All those functions are in the library that was compiled.

---

### Post by Jordanwb on 2012-01-31
Neverfind I figured it out. In library.c there's #ifdef macros that control what was compiled into the library and I forgot to remove those, so nothing was compiled into the library.

---

