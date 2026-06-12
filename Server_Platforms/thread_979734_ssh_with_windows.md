---
title: "ssh with windows?"
date: 2008-11-12
forum: Server Platforms
---

### Post by bobyo134 on 2008-11-12
im running debina server 4 and it has ssh, i use ssh with my ubuntu desktop and remote location, but i was wondering if there was a way to ssh on windows with out installing a program or even with a program thx :):guitar:

---

### Post by kevdog on 2008-11-12
You need a program -- either need to install cygwin (which has ssh in the install) or use putty.  putty works great however you need one extra step of converting putty keys to openssh keys or vice versa. cygwn provides linux functionality to windows, is much more powerful, and if you have used linux before it should be a snap.

---

### Post by hictio on 2008-11-12
> **bobyo134 said:**
> im running debina server 4 and it has ssh, i use ssh with my ubuntu desktop and remote location, but i was wondering if there was a way to ssh on windows with out installing a program or even with a program thx :):guitar:

I don't understand, if you want to connect TO a linux (or what ever) server that has a running SSH server FROM a Windows box you can use [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html), a free program that will give a terminal emulator and a SSH client for Windows. There is no installer, simply drop the exe file somewhere and start using it.

If you want to transfer files, you can use PSCP (you can get it on teh PuTTY page too), but it doesn't have a graphical screen.
For that, transfering files using a graphical environment, you can use [FileZilla](http://filezilla-project.org/), it is free, BTW.

Now, if you want to SSH INTO your Windows box, you'll need to install either Cygwin, and enable the SSHD server, or get one of the [SSH servers for Windows](http://www.google.com.ar/search?q=SSH+server+for+Windows&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a).

---

### Post by koenn on 2008-11-12
> **hictio said:**
> 
For that, transfering files using a graphical environment, you can use [FileZilla](http://filezilla-project.org/), it is free, BTW.
or WinSCP

---

