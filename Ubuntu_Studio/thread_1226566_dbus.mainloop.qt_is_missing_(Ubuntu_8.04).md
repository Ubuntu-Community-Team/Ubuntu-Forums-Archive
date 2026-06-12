---
title: "dbus.mainloop.qt is missing (Ubuntu 8.04)"
date: 2009-07-29
forum: Ubuntu Studio
---

### Post by h_howee on 2009-07-29
I'm trying to install frescobaldi on Ubuntu 8.04.
I fixed most of the errors with the help of [this thread]("http://ubuntuforums.org/showthread.php?t=1073049") but one remains:
```

CMake Error at cmake/modules/Python.cmake:11 (message):
  The following Python modules are missing:

    dbus.mainloop.qt

Call Stack (most recent call first):
  CMakeLists.txt:14 (python_test_script)


-- Configuring done

```
What do I need to get this working?

[edit]
Funny how I always figure it out right after posting..
I had to install python-qt4-dbus

---

