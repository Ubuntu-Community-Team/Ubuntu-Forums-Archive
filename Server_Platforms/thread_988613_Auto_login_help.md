---
title: "Auto login help"
date: 2008-11-20
forum: Server Platforms
---

### Post by lostinhell on 2008-11-20
I'm trying to get a console based server to auto login with a specified user name. I found a couple of tutorials, but I can't seem to get them to work. 

I found this one [http://ubuntuforums.org/showthread.php?t=31310](http://ubuntuforums.org/showthread.php?t=31310) and one with the exact some instructions, but I can't get them to work. When I get to the 
     sudo gcc -o autologin autologin.c
it gives me the following errors:
     autologin.c: In function ‘main’:
     autologin.c:2: warning: incompatible implicit declaration of built-in function ‘execlp’
     autologin.c:2: warning: missing sentinel in function call

I'm no coder, so I'm not sure what exactly I'm looking at, or what might be causing the error. I have gcc-4.3 installed on 32bit 8.10 Ubuntu Server Edition computer.

Edited to fix spelling error.

---

### Post by adaptr on 2008-11-20
Perhaps if you explain WHY you need a server system to auto-logon a user at a console, we can tell you how to avoid that.
Auto-logon on a server system is the epitome of insecurity.

---

### Post by Thirtysixway on 2008-11-20
On a server you shouldn't need to have anything run when a user logs in.  Things like Apache, mysql, etc start with the computer.

If you need to run something as a specific user I'd suggest setting up some type of cronjob.

---

### Post by lostinhell on 2008-11-20
> **adaptr said:**
> Perhaps if you explain WHY you need a server system to auto-logon a user at a console, we can tell you how to avoid that.
Auto-logon on a server system is the epitome of insecurity.

I'm not worried about security of the system, not only is it not a critical server (never would think of this if it was), but it is hooked up to a LAN with no WAN access, with 5 people who don't know how to do anything without a GUI, and me.

I set this server up as a headless local web (Wiki)/samba server for the hotel I work in. Now the bosses want to use the server to also display a slide show in the lobby. It's not a powerful computer, so I don't want to run Gnome or KDE on it. What I was going to do was set the computer up to auto login with a limited account, and at login bring up Blackbox, which would auto start gthumb. Not exactly the most elegant solution, but I figure it should work. Of course if anyone has any better ideas, I'm listening.

Man I hope that rambling made sense.

---

### Post by Thirtysixway on 2008-11-20
Ah that makes sense.  With some googling, I've found this

[http://ubuntuforums.org/showpost.php?p=2835989&postcount=2](http://ubuntuforums.org/showpost.php?p=2835989&postcount=2)

It doesn't autologin a user but it does run a command at startup, which could start your slideshow.

---

### Post by lostinhell on 2008-11-20
> **Thirtysixway said:**
> Ah that makes sense.  With some googling, I've found this

Thanks, that worked nicely. Everything is up and running as it should be.

---

