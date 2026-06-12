---
title: "Noob wanting help for ubuntu server for classroom"
date: 2007-10-19
forum: Server Platforms
---

### Post by jdm2 on 2007-10-19
I have convinced my teacher to install ubuntu server on a computer this year.  He is thinking about doing it soon, but before he does it I have some question.  He is a teacher at my school and he teaches basic programming, advance programming, ap computer science, and general music.  He has all windows based computer in the lab.  He would like to be able to setup different folder for each of his period and in those folder have each person folder.  He would like for only that person the folder belongs to to be able to access it besides himself. I don't know what else he would like to do with it yet, but can you help me?  Thanks

---

### Post by tkharris on 2007-10-19
Tell him to use Samba, this will be accessable through the Windows computers the students are using, and can have per directory permissions.

[http://us4.samba.org/samba/](http://us4.samba.org/samba/)

---

### Post by jdm2 on 2007-10-22
I aprreciate it.  Do you have any other suggestions.  I'm still new to linux and he is brand new to linux.  Thanks for the help.

---

### Post by oly on 2007-10-22
if its on a server why not use edubuntu, you can pxe boot the rest of the machine in the classroom into ubuntu complete with all the apps you need. 

you just install them on the server and they are available to the clients, you can also setup groups and users on the server and set rights to various folders this way.

much easier to manage and maintain, plus then everyone can try ubuntu :)

---

### Post by jdm2 on 2007-10-22
He had a copy of ubuntu dapper server and he wanted to try it out.  I don't think eubuntu is what he is looking for any way, because he teaches visual basics and other stuff that only runs on windows.  He just want s to mess with it and have a place where he can set up folders with permissions like he has in windows server 2003.  Thanks for the help.

---

### Post by HermanAB on 2007-10-22
If the machine is actually in a room with a keyboard and screen attached, then rather install regular U/K/Xubuntu.

The server edition is meant to run headless.  If it is going to have a head, then you need X.

---

### Post by jdm2 on 2007-10-23
It has a mouse, keyboard, and moniter.  It is running ubuntu 6.06 server.  We just installed ubuntu-desktop for it.  I believe when he installed it he installed LAMP.

---

