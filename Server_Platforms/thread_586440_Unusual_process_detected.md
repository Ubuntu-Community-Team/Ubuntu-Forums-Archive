---
title: "Unusual process detected"
date: 2007-10-22
forum: Server Platforms
---

### Post by bg11 on 2007-10-22
I just ran ps aux as root and found the following process running on my machine:


root      2826  0.0  0.2   4176  1488 ?        S    10:44   0:00   -:0


Is that anything to worry about?  Seems a bit strange a process calling itself "-:0".

---

### Post by kosmic on 2007-10-22
do a "lsof -p PIDNUMBER" 
To see what files is that program using.

lsof -p 2826

---

### Post by bg11 on 2007-10-22
```

>lsof -p 2826
COMMAND  PID USER   FD   TYPE     DEVICE    SIZE   NODE NAME
kdm     2826 root  cwd    DIR        8,6    4096      2 /
kdm     2826 root  rtd    DIR        8,6    4096      2 /
kdm     2826 root  txt    REG        8,6  120660 359323 /usr/bin/kdm
kdm     2826 root  mem    REG        8,6  220764 667852 /lib/libsepol.so.1
kdm     2826 root  mem    REG        8,6   21912 667825 /lib/libcrypt-2.6.1.so
kdm     2826 root  mem    REG        8,6   11024 895994 /lib/libcap.so.1.10
kdm     2826 root  mem    REG        8,6   12692  97798 /lib/security/pam_limits.so
kdm     2826 root  mem    REG        8,6   48268  97819 /lib/security/pam_unix.so
kdm     2826 root  mem    REG        8,6   38420 667888 /lib/libnss_files-2.6.1.so
kdm     2826 root  mem    REG        8,6   34352 667902 /lib/libnss_nis-2.6.1.so
kdm     2826 root  mem    REG        8,6   83712 667882 /lib/libnsl-2.6.1.so
kdm     2826 root  mem    REG        8,6   30436 667884 /lib/libnss_compat-2.6.1.so
kdm     2826 root  mem    REG        8,6   83512 667854 /lib/libselinux.so.1
kdm     2826 root  mem    REG        8,6   11600  97789 /lib/security/pam_env.so
kdm     2826 root  mem    REG        8,6 1335536 667823 /lib/libc-2.6.1.so
kdm     2826 root  mem    REG        8,6    9700 667918 /lib/libutil-2.6.1.so
kdm     2826 root  mem    REG        8,6   67408 667913 /lib/libresolv-2.6.1.so
kdm     2826 root  mem    REG        8,6    9684 667826 /lib/libdl-2.6.1.so
kdm     2826 root  mem    REG        8,6   37476 895978 /lib/libpam.so.0.81.6
kdm     2826 root  mem    REG        8,6   16704 393330 /usr/lib/libXdmcp.so.6.0.0
kdm     2826 root  mem    REG        8,6    7220 393319 /usr/lib/libXau.so.6.0.0
kdm     2826 root  mem    REG        8,6  965952 393315 /usr/lib/libX11.so.6.2.0
kdm     2826 root  mem    REG        8,6    4276  97806 /lib/security/pam_nologin.so
kdm     2826 root  mem    REG        8,6   14396 393334 /usr/lib/libXfixes.so.3.1.0
kdm     2826 root  mem    REG        8,6   29808 392017 /usr/lib/libXrender.so.1.3.0
kdm     2826 root  mem    REG        8,6   32764 392025 /usr/lib/libXcursor.so.1.0.2
kdm     2826 root  mem    REG        8,6  117340 667820 /lib/ld-2.6.1.so
kdm     2826 root    0r   CHR        1,3           1145 /dev/null
kdm     2826 root    1w   REG        8,6    9832 769158 /var/log/kdm.log
kdm     2826 root    2w   REG        8,6    9832 769158 /var/log/kdm.log
kdm     2826 root    3u  unix 0xdddec180           9673 socket
kdm     2826 root    4u  unix 0xde328080          10023 socket
kdm     2826 root   10r  FIFO        0,6           9669 pipe
kdm     2826 root   13w  FIFO        0,6           9670 pipe
kdm     2826 root   14r  FIFO        0,6           9671 pipe
kdm     2826 root   17w  FIFO        0,6           9672 pipe

```

---

