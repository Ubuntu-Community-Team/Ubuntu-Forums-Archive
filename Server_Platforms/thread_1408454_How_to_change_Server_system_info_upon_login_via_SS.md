---
title: "How to change Server system info upon login via SSH?"
date: 2010-02-16
forum: Server Platforms
---

### Post by rippfx on 2010-02-16
Hi, I would like to know if there is any documentation on how to change the server system info display when logging in via ssh. example:
```
[jason@carbon ~]$ ssh xxx.xxx.xxx.xxx
jason@xxx.xxx.xxx.xxx's password: 
Linux relativity 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Tue Feb 16 09:23:08 PST 2010

  System load: 0.0                Memory usage: 17%   Processes:       132
  Usage of /:  7.4% of 219.83GB   Swap usage:   0%    Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Fri Feb 12 15:58:46 2010 from xxx.xxx.xxx.xxx
```

I would like to display the usage of other mounted drives when logging in. If you can point me to right direction, I would appreciate it. TIA.

---

### Post by cdenley on 2010-02-16
Have a look at the files in the directory "/etc/update-motd.d".

[https://help.ubuntu.com/9.10/serverguide/C/update-motd.html](https://help.ubuntu.com/9.10/serverguide/C/update-motd.html)

---

### Post by rippfx on 2010-02-16
thank you cdenley.

---

