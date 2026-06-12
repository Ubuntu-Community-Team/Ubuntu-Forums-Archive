---
title: "64-bit Ubuntu, PHP, 32-bit SSH2..."
date: 2013-03-15
forum: Server Platforms
---

### Post by flyns on 2013-03-15
Hello!

I'm going mad with this one. It all started with a simple script in PHP. I need to connect to a ftp server. It looks like a need a secure connection, so I tried ssh2. Then: 

I'm trying to install ssh2 in my 64-bit ubuntu. I've had a lot of problems, but finally I got ssh2.so out. Now, when I restart lampp [ /opt/lampp/lampp restart], I get the next warning: 

- - - - - - - - - - - - - - - - - - - - - - - - - - - -

Stopping XAMPP for Linux 1.7.7...
XAMPP: Stopping Apache with SSL...


**Warning: PHP Startup: Unable to load dynamic library '/root/libs/ssh2.so' - /root/libs/ssh2.so: wrong ELF class: ELFCLASS64 in Unknown on line 0**
XAMPP: Stopping MySQL...
XAMPP: XAMPP-ProFTPD is not running.
XAMPP stopped.
Starting XAMPP for Linux 1.7.7...


**Warning: PHP Startup: Unable to load dynamic library '/root/libs/ssh2.so' - /root/libs/ssh2.so: wrong ELF class: ELFCLASS64 in Unknown on line 0**
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

- - - - - - - - - - - - - - - - - - - - - - - - - - - -

.... and, of course, my code still doesn't work:

[B]Fatal error: Call to undefined function ssh2_connect() in [B]........ .php on line [B]41

[/B][/B][/B]I guess that's because I'm trying to install a 32-bit program in a 64-bit Ubuntu, but... how can I fix this? I haven't found a 64-bit version of ssh2 and I'm an asbolutelly newbie. ...help!...

Thanks a lot!

Flyns.

---

### Post by flyns on 2013-03-20
...¿No one? ... :icon_frown:

---

### Post by flyns on 2013-03-20
I'll add something:

'file ssh2.so' returns:

ssh2.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=0x64accc42c4ebcddb0043a1da263e2e1418435600, not stripped

...

---

