---
title: "Ubuntu 8.10 Server - Had to add vncserver to startup"
date: 2009-01-28
forum: Server Platforms
---

### Post by UberGTI on 2009-01-28
Hi all,

I'm trying to add a vncserver script to start when my server boots.  However, I can't seem to get it working.  I read about upstart and how it replaces the inittab.  However, also read that the rc#.d directory scripts will still be executed depending on the fictitious run level.  However, it doesn work when I link to an init.d script from rc2.d.

Here is what I did.  I create a script in /etc/init.d called vncserver.  Then I linked to it from rc2.d and rebooted.  Didn't work, nothing loaded.  I don't have to do it this way.  I just want to get my script to load a boot.

Thanks for your help.

I should also mention that when I manually execute /etc/init.d/rc 2 all works as expected.

---

### Post by bluefrog on 2009-01-28
you ave a gui on the server?

---

### Post by UberGTI on 2009-01-29
Yes I do have a GUI.  However, I would prefer to make the changes via the command line.

Thanks.

---

### Post by bluefrog on 2009-01-29
then use ssh not vnc

---

### Post by Johnsie on 2009-01-29
I agree, ssh is a much better solution.

---

### Post by HermanAB on 2009-01-29
On Linux, VNC is almost always the wrong solution.  Install the openssh-server package, then connect to the server like this:
$ ssh user@server gnome-panel

Cheers,

Herman

---

### Post by UberGTI on 2009-01-30
Thanks for your answers.  I think I might have made things confusing with my responses.  I do currently have openssh running and it works well when I want to log in at the command line level.  However, at times I will want to login and use the GUI.  It is here that I'm having trouble.  I have vnc installed, however it doesn't startup at boot automatically.  Where can I make changes manually at the command line to start vnc when my system boots.  BTW, my server automatically boots into Gnome.

Thanks.

---

