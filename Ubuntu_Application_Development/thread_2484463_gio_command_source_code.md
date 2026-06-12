---
title: "gio command source code"
date: 2023-02-27
forum: Ubuntu Application Development
---

### Post by artist-wavenet on 2023-02-27
I need to step through the gio command using gdb. For this I need its source code, and symbols. To get these I followed the directions at:

[https://wiki.ubuntu.com/Debug%20Symbol%20Packages](https://wiki.ubuntu.com/Debug%20Symbol%20Packages)

duginfod did not work on my Ubuntu 22.04 system. It was therefore necessary to manually down load these. I followed the directions under the heading "Getting -dbgsym.ddeb packages", and then "Automatic Resolution / Installation of necessary packages", on that page. All went well until the find command. This is the command, and the response I got:

```
stephen@stephen:~$ find-dbgsym-packages /usr/bin/gio
dpkg-query: no path found matching pattern /lib/x86_64-linux-gnu/libgmodule-2.0.so.0
W: Cannot find debug package for /lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (991a9f61e69c30ef8ab73761c300ae51249ede63)
dpkg-query: no path found matching pattern /lib/x86_64-linux-gnu/libglib-2.0.so.0
W: Cannot find debug package for /lib/x86_64-linux-gnu/libglib-2.0.so.0 (137458a0f7846a084270bf5bb03df075a578db6d)
dpkg-query: no path found matching pattern /lib/x86_64-linux-gnu/libgobject-2.0.so.0
W: Cannot find debug package for /lib/x86_64-linux-gnu/libgobject-2.0.so.0 (44f60e584780daaeb1880ead5dd00f12ffd423d2)
dpkg-query: no path found matching pattern /lib/x86_64-linux-gnu/libgio-2.0.so.0
W: Cannot find debug package for /lib/x86_64-linux-gnu/libgio-2.0.so.0 (9b52271b63917542ba10ffb8a82b97befd2c238f)
dpkg-query: no path found matching pattern /lib/x86_64-linux-gnu/libpcre2-8.so.0
W: Cannot find debug package for /lib/x86_64-linux-gnu/libpcre2-8.so.0 (184a841c55fb7fe5e3873fcda8368c71016cd54c)
libblkid1-dbgsym libffi8-dbgsym libglib2.0-bin-dbgsym libmount1-dbgsym libpcre3-dbg libselinux1-dbgsym zlib1g-dbgsym
```

Where did this go wrong? Why does it not seek the right debug package?

I need to step through the gio command because it fails, and in this thread of mine, no one has come up with a solution:
[https://askubuntu.com/questions/1427431/how-to-set-a-launcher-as-trusted](https://askubuntu.com/questions/1427431/how-to-set-a-launcher-as-trusted)

---

