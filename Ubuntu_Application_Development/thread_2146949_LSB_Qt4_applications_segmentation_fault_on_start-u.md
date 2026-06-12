---
title: "LSB Qt4 applications segmentation fault on start-up"
date: 2013-05-20
forum: Ubuntu Application Development
---

### Post by sdc395 on 2013-05-20
Hello all

I'm encountering a segmentation fault when running a simple Qt4 application that I've built on Ubuntu 12.04 using the LSB SDK.
The source couldn't really be any simpler...

```
#include <QApplication>

int main(int argc, char **argv)
{
    QApplication app(argc, argv);
    return app.exec();
}
```

I use CMake 2.8.7 for configuration. Here's my CMakeLists.txt...

```
cmake_minimum_required(VERSION 2.8)

project(lsb_test)

find_package(Qt4)

include(${QT_USE_FILE})

add_definitions(${QT_DEFINITIONS})

add_executable(lsb_test
    main.cpp)

target_link_libraries(lsb_test ${QT_LIBRARIES})
```

GDB says...

```

Program terminated with signal 11, Segmentation fault.
#0  0x08048771 in _start ()
```

I'm running 32-bit Ubuntu 12.04.2 3.5.0-30-generic on a VirtualBox 4.2.12 VM with GCC 4.6.3, LSB SDK 4.1.6-2.  Hopefully that's all the information needed to recreate the problem. Please let me know if more is needed.

Any and all help greatly appreciated.

Thanks

Simon

---

### Post by sdc395 on 2013-05-30
OK, then perhaps someone could suggest how to contact those that might be able to help.  To be honest, it's looking as if LSB might be dying a death anyway.  Perhaps it's time to abandon it and hope for the best in the fragmented development hell that is Linux.

---

