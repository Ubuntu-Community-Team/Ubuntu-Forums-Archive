---
title: "[SOLVED] Boot to login prompt / edit greeting message"
date: 2008-02-25
forum: Server Platforms
---

### Post by Arthur Archnix on 2008-02-25
I've gone over this bug[ here]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230"), but I'm afraid I'm not sure I understand it, and I don't know how to apply patches in any case.

The problem is that I have to hit enter (or any key really) to get a login prompt. I just want it to go straight to the login prompt.

My second question is if there is anyway to change that greeting message after a successful login.

Many thanks

EDIT: Ubuntu Gutsy

---

### Post by Arthur Archnix on 2008-02-25
Part of the problem is solved. First, regarding that bug above, the fix is real easy:
```
sudo nano /etc/event.d/tty1
```
and change 
```
start on runlevel 2
```
to
```
start on stopped rc2
```
That drops you into a login prompt cleanly. Now to figure out how to clear the screen, put the host name above the login, and remove that whole "ubuntu comes without legal" mumbo jumbo.

---

### Post by Brazen on 2008-02-25
you'll need to edit /etc/motd
(that stands for Message Of The Day, in case you were wondering)

---

### Post by Arthur Archnix on 2008-02-26
Oops. I can't seem to edit that file. I can open /etc/motd  and edit it, and save it. But when I log in.... there it is back again. And if I try and use sudo nano, instead of sudo gedit, it won't let me save changes.

EDIT: ok, I found that there are three motd files. I edited them all and now it's good. Also, I added "clear" to /etc/rc.local to clear the screen before login. Beauty!

Cheers Brazen. :guitar:

---

