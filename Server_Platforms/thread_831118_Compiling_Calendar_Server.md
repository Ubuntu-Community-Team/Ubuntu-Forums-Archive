---
title: "Compiling Calendar Server"
date: 2008-06-16
forum: Server Platforms
---

### Post by sunstriker on 2008-06-16
Hi,

At home we have one XP user, one Vista user, one ubuntu user and one Mac user + 1 ubuntu server.
I thought it would be a good idea to sync our calendars. I read Apple's iCal server or Calendar Server uses Caldav which is compatible with many clients. So now i'm trying to compile/install it one my ubuntu hardy server. So far i'm not able to compile it. 
I'm getting following error:
```
Building memcached...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

Any thoughts are much appreciated!

---

### Post by cviniciusm on 2008-06-21
Hello,

There is eGroupWare. From the one site:
"
**eGroupWare is a [free]("http://www.egroupware.org/philosophy")  enterprise ready groupware software** for your network. It enables you to manage contacts, appointments, todos and many more for your whole business.
   
    **eGroupWare is a groupware server.** It comes with a native web-interface which allowes to access your data from any platform all over the planet. Moreover you also have the choice to access the eGroupWare server with your favorite groupware client (Kontact, Evolution, Outlook) and also with your mobile or PDA via SyncML.
   
    **eGroupWare is international.** At the time, it supports more than [25 languages]("http://www.egroupware.org/languages") including rtl support.
   
    **eGroupWare is platform independent.** The server runs on Linux, Mac, Windows and many more other operating systems. On the client side, all you need is a internetbrowser such as Firefox, Konqueror, Internet Explorer and many more.
"

It's a kind of Outlook + Exchange Server.

It's available on Ubuntu repositories.


Regards,
cviniciusm.

---

### Post by ibutho on 2008-06-21
To fix the error, you need to install a C compiler (in this case gcc). You can install it along with other useful development tools by running the command
```
aptitude install build-essential
```

---

