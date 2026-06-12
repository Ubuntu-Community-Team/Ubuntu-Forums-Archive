---
title: "Logon back into an existing session."
date: 2009-06-06
forum: Server Platforms
---

### Post by jhj614 on 2009-06-06
I have been playing with Ubuntu desktop version for quite a while and have just started trying out server version.  Getting a bit lost with some pretty basic issues using command lines.

I use Putty to connect to my server remotely.  Am running an upgrade which will take about an hour due to limited broadband speed.  Got to go out now and resume work later.  I understand the session should still run if I close Putty.

How do I logon back into this session to continue other tasks?

Be grateful for any hints!

---

### Post by netztier on 2009-06-06
> **jhj614 said:**
> 
How do I logon back into this session to continue other tasks?


Yet another use case for screen.

Install **screen** and run it after login, it will open one or more virtual terminals/shells from your login shell.

[LIST]
[*]start screen from your login shell:```
user@host:~$** screen**

Screen version 4.00.03jw4 (FAU) 2-May-06

Copyright (c) 1993-2002 Juergen Weigert, Michael Schroeder
Copyright (c) 1987 Oliver Laumann

This program is free software; you can redi... *snipped*


```


[*]From any virtual terminal, create a second/n-th virtual terminal with **Ctrl+a c** [SIZE="1"](hit "Ctrl+a", then type "c")[/SIZE]
[*]Switch between terminals with **Ctrl+a <number>**, where <number> is from 0 to n.
[*]run all your "disconnectable" apps within a screen virtual terminal, e.g. your long-running "sudo aptitude safe-upgrade"
[*]just like with a login shell, type **exit** to terminate a virtual terminal. You'll be dropped to another virtual terminal or screen will exit to your login shell.
[*]To disconnect (screen speech: "detach") from screen and it's virtual terminals use **Ctrl+a d**. This drops you back to your login shell, but keeps the virtual terminals alive in the background.
[*]To reconnect to your virtual terminals, login to the system (at the local keyboard or remotely via SSH) and use **screen -r** to "reattach".
[/LIST] 


That's just the very basics, of course. Read screen's man page, it can do a lot more!

I use it to run some text-mode applications on my server that I don't want to run as s service/deamon, like rtorrent as a very simple bittorrent client; I don't want to run a mySQL instance and a Web GUI for an occasional torrent download. Screen comes in very handy there.

Another suggestion: if you want some form of "console based GUI" to handle files, take a look at **mc** (Midnight Commander), a clone of the venerable Norton Commander that already was a very good program when DOS-based sabre tooth tigers walked the computing earth. Runs withing a virtual terminal provided by screen as well.


[I]Edit:
and then there's always: [https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)
[/I]
regards

Marc

---

### Post by jhj614 on 2009-06-06
Wow!  Thanks so much Marc! This is a very detailed guide on Screen.  I will try it out right away.

---

### Post by netztier on 2009-06-07
> **jhj614 said:**
> Wow!  Thanks so much Marc! This is a very detailed guide on Screen.  I will try it out right away.

If you are running Ubuntu 9.04, make sure that **screen-profiles** is installed as well. It will display sort of a "status bar" at the bottom of your terminal window, with some information about the system, which virtual terminal you are currently in etc. 

I'm just discovering it, seems pretty cool.

regards

Marc

---

### Post by grantemsley on 2009-06-08
screen-profiles (now known as byobu) can be gotten from [https://launchpad.net/byobu](https://launchpad.net/byobu)

My favorite thing is that you can set it to automatically start screen whenever you login, so you don't forget to start it before doing some long running task.  And if you get disconnected, you'll be right back where you were when you log back in.

---

