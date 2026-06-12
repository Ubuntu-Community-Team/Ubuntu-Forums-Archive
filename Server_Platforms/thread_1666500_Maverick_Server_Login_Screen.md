---
title: "Maverick Server Login Screen?"
date: 2011-01-13
forum: Server Platforms
---

### Post by bryanfblareunion on 2011-01-13
I have a web server running Ubuntu Maverick (server) and I want to change the screen that I get when I login. After you enter username and pass. I think by default it says "Welcome to Ubuntu!" then gives a help page or something. I know there is a way to change this but I have no idea where this file is located.... Thanks in advance.

---

### Post by Thirtysixway on 2011-01-13
> **bryanfblareunion said:**
> I have a web server running Ubuntu Maverick (server) and I want to change the screen that I get when I login. After you enter username and pass. I think by default it says "Welcome to Ubuntu!" then gives a help page or something. I know there is a way to change this but I have no idea where this file is located.... Thanks in advance.

It's called the motd, message of the day

[http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html)

---

### Post by sj1410 on 2011-01-14
you can also change the text on the logon window, add some notices, etc.. just change the

/etc/issue  file

---

### Post by James78 on 2011-01-14
In addition, you can also tack anything you want to the very end by creating the file /etc/motd.tail and putting something in it. (Also mentioned briefly in the link given earlier I believe)

---

