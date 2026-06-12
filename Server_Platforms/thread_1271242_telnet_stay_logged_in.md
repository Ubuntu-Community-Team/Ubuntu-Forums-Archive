---
title: "telnet stay logged in"
date: 2009-09-20
forum: Server Platforms
---

### Post by rmb938 on 2009-09-20
So I am running ubuntu server edition on one of my computers because I need to run a java program that works in the linux envio.

I connect to it using telnet and then I run it from that. But if I exit my telnet window it exits my java program. Is there a way to keep this program running after i exit telnet?

---

### Post by Ropetin on 2009-09-20
Is using screen an option at all?  I've never telnet'd into a Linux server (way too many security issues for me), but it definitely works for SSH connections.

---

### Post by rmb938 on 2009-09-20
no the java program is just out puts lines of text. Its a game server for this game I am making.

I haven't tryed SSH. I will look into that.

Ok well i just tryed SSH and the same thing happened. When you exit the window it exits the program.

---

### Post by jonallport on 2009-09-21
Suffix the command with & and it will fork to background and keep running (daemonise).

i.e. /bin/gameserver &

You can then quit the telnet/ssh session and the 'gameserver' will continue running.  When you need to stop it, use ps and kill.

---

### Post by rmb938 on 2009-09-21
ah ok perfect. thanks :)

---

### Post by howlingmadhowie on 2009-09-21
i'd recommend having a look at a program called GNU/screen (it should be installed by default.  This is a terminal multiplexer, allowing you to run many terminals at once and detach and reattach. An exampled session would be:

ssh -l <username> <host> -p <port>
<password>
screen

... do lots of work in screen ...
CTRL-A CRTL-D    #detach from screen
exit

... and later when you want to continue ...

ssh -l <username> <host> -p <port>
<password>
screen -r

... carry on working as if nothing had happened ...

---

