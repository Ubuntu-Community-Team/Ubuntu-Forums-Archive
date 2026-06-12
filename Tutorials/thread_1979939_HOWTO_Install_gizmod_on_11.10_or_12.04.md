---
title: "HOWTO: Install gizmod on 11.10 or 12.04"
date: 2012-05-14
forum: Tutorials
---

### Post by kebes on 2012-05-14
The information in this thread has been moved to [https://help.ubuntu.com/community/GizmodIn11.10and12.04](https://help.ubuntu.com/community/GizmodIn11.10and12.04)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062154#post12062154](http://ubuntuforums.org/showthread.php?p=12062154#post12062154)

Thread closed.


**[SIZE="3"]HOWTO: Install gizmod on Ubuntu 11.10+[/SIZE]**
[The Gizmo Daemon]("http://gizmod.sourceforge.net/") (gizmod) is a nice utility that lets you customize how various input devices (keyboards, mice, etc.) interact with Linux. In particular, it can be useful to recognize more exotic input devices that Linux doesn't natively understand. Example: it has support for the Griffin PowerMate dial, and you can then assign arbitrary actions to the dial (scroll, click, etc.).

As of 11.10, gizmod is no longer in the Ubuntu repositories. As such, you have to compile it manually. The [gizmod wiki]("http://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Installation") has some good information, but the instructions don't work on Ubuntu 11.10+.

Here I've collected the various tricks necessary to install gizmod on Ubuntu 11.10 (Oneric Ocelot) or 12.04 LTS (Precise Pangolin). You will need to make a small number of modifications to the source code, and compile it. Follow the official [compile-from-source instructions]("https://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Compile_from_Source") until the [Compiling and Installing]("https://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Compile_from_Source#Compiling_and_Installing") step:
[https://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Compile_from_Source](https://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Compile_from_Source)

 Before that step, you'll need to make the changes detailed in [this forum post]("http://sourceforge.net/projects/gizmod/forums/forum/467994/topic/4675015"). Specifically:

**[SIZE="2"]size_t errors[/SIZE]**
When attempting to run 'make' you will get errors like:
```
In file included from ./gizmod-3.5/libHAverage.cpp:31:0:
./gizmod-3.5/libH/Average.hpp:74:5: error: ‘size_t’ does not name a type

```
To fix these, make the following edits to the source code:
1. In file ./gizmod-3.5/libH/Average.hpp
    Add:
```
#include <stdlib.h>
```
2. In file ./gizmod-3.5/libH/DynamicBuffer.hpp
    Add:
```
#include <stdlib.h>
```

[SIZE="2"]**no member named string errors**[/SIZE]
When attempting to run 'make' you will get errors like:
```
gizmod-3.5/libGizmod/Processes.cpp: In static member function ‘static void Gizmod::Processes::updateProcessTree()’:
gizmod-3.5/libGizmod/Processes.cpp:157:27: error: ‘class boost::filesystem3::directory_entry’ has no member named ‘string’
```

To fix this, make the following change to the source code:
1. In the file ./gizmod-3.5/libGizmod/Proceses.cpp
[INDENT]On line 157, change:
        [INDENT]string StatPath = iter->string() + "/stat";[/INDENT]
    To:
        [INDENT]string StatPath = iter->path().string() + "/stat";[/INDENT][/INDENT]
2. In the file ./gizmod-3.5/gizmod/GizmoDaemon.cpp
[INDENT]    a. On line 1109, change:
        [INDENT]ret += "sys.path.insert(0, \"" + iter->string() + "\")\n";[/INDENT]
    To:
        [INDENT]ret += "sys.path.insert(0, \"" + iter->path().string() + "\")\n";[/INDENT]
    b. On line 1567, change:
        [INDENT]UserScripts.push_back(iter->path().leaf());[/INDENT]
    To:
        [INDENT]UserScripts.push_back(iter->path().filename().string());[/INDENT]
    c. On line 2192, change:
        [INDENT]if (iter->path().leaf().find("event") != 0)[/INDENT]
    To:
        [INDENT]if (iter->path().filename().string().find("event") != 0)[/INDENT]
    d. On line 2194, change:
        [INDENT]eventsFiles.push_back(mEventsDir + "/" + iter->path().leaf());[/INDENT]
    To:
        [INDENT]eventsFiles.push_back(mEventsDir + "/" + iter->path().filename().string());[/INDENT][/INDENT]
           
[SIZE="2"]**default_name_check error**[/SIZE]
When attempting to run 'make' you will get an error like:
```
gizmod-3.5/gizmod/Main.cpp: In function ‘int main(int, char**)’:
gizmod-3.5/gizmod/Main.cpp:57:2: error: ‘default_name_check’ is not a member of ‘boost::filesystem3::path’
```

To fix this, remove line 57 from ./gizmod-3.5/gizmod/Main.cpp

```
    // set filesystem to native filesystem checking
    // path::default_name_check(native); // Removed to eliminate compile error

```

[SIZE="2"]**boost error**[/SIZE]
When attempting to run 'make' you will get an error like:
```
Linking CXX executable gizmod
/usr/bin/ld: CMakeFiles/gizmod.dir/GizmoDaemon.o: undefined reference to symbol 'boost::system::system_category()'
/usr/bin/ld: note: 'boost::system::system_category()' is defined in DSO /usr/lib/libboost_system.so.1.46.1 so try adding it to the linker command line
/usr/lib/libboost_system.so.1.46.1: could not read symbols: Invalid operation

```

To fix, edit the file /gizmod-3.5/build/gizmod/CMakeFiles/gizmod.dir/link.txt
And add '''-lboost_system''' to the arguments:
/usr/bin/c++   -O3 -DNDEBUG    CMakeFiles/gizmod.dir/GizmoDaemon.o CMakeFiles/gizmod.dir/GizmoUtils.o CMakeFiles/gizmod.dir/GizmodEventHandlerInterface.o CMakeFiles/gizmod.dir/Main.o  -o gizmod -rdynamic ../libH/libH.a ../libGizmod/libGizmod.so.3.4.0 -lboost_program_options -lpython2.7 ../libH/libH.a -lboost_filesystem **-lboost_system** -lboost_thread -lboost_serialization -lboost_python -lasound -lSM -lICE -lX11 -lXext -lutil -lpython2.7 -Wl,-rpath,/home/user/tmp/gizmod/gizmod-3.5/build/libGizmod:

[SIZE="2"]**Finish compile**[/SIZE]
With those changes, you should be able to finish the [compile steps]("https://sourceforge.net/apps/mediawiki/gizmod/index.php?title=Compile_from_Source#Compiling_and_Installing"):
```
make
sudo make install
```

[SIZE="2"]**Excessive CPU usage**[/SIZE]
If you find that gizmod is using 100% of CPU on your machine, this may be due to how polling interacts with newer kernel versions. [The fix]("https://sourceforge.net/tracker/index.php?func=detail&aid=2847792&group_id=139428&atid=743549") is to edit ./gizmod-3.5/libH/FileEventWatcher.cpp line 232-236:

```
    case WATCH_INOUT:
        flags = O_RDWR;
        //events = POLLIN | POLLOUT; // This line causes 100% CPU usage on newer kernels
        events = POLLIN;// | POLLOUT;
        ModeString = "Read / Write";
        break;
```
Then re-compile and re-install:
```
make
sudo make install
```

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/GizmodIn11.10and12.04](https://help.ubuntu.com/community/GizmodIn11.10and12.04)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12062154#post12062154](http://ubuntuforums.org/showthread.php?p=12062154#post12062154)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

