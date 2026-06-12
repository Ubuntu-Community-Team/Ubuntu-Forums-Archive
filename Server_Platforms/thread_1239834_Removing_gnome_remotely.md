---
title: "Removing gnome remotely"
date: 2009-08-14
forum: Server Platforms
---

### Post by thegrilledcheese on 2009-08-14
I recently built a new machine and loaded ubuntu 9.04 server on it.  I wanted to remain using CLI without gnome for a learning experience but I ended up installing gnome to get SSH setup which I was struggling with.  

I now have SSH completely setup and running so I want to remove gnome desktop now.  I don't want to have a reboot and be stuck with the graphical login and have to hook up a monitor and everything.

The server currently has gnome running.  Can I log into server via SSH and uninstall gnome?  What steps do I need?  Should I reboot after?  The only post I could find that was somewhat helpful is [http://ubuntuforums.org/showthread.php?t=772120](http://ubuntuforums.org/showthread.php?t=772120)

It says to: 

[FONT=monospace]
sudo apt-get remove ubuntu-desktop

sudo apt-get remove xorg


The post is older so I want to make sure this is the correct commands for my system.  Will doing this return the server to CLI only without any other steps needed?  Will removing ubuntu-desktop and xorg remove the graphical login on the next reboot?

Thanks ahead of time!
[/FONT]

---

### Post by Vegan on 2009-08-14
If you install TELNET, you can log in from remote, although this is not secure, its adequately simple to manage a machine.

```
sudo apt-get install telnetd
```

then you can login from port 23 which is the standard TELNET port.

Alternatives are available but are more work to setup as you need to setup SSL etc.

---

### Post by thegrilledcheese on 2009-08-14
So the commands listed will work to remove the gnome desktop and return the system to CLI only?

I'm not sure if your saying I HAVE to use telnet to make this work.  Can it not be done through SSH?

---

### Post by y@w on 2009-08-14
Uh yeah, you definitely don't need telnet. Those commands should do it, though I've not done it myself.

---

### Post by thegrilledcheese on 2009-08-14
Should I stop gnome-desktop first?  What is the command?  I used "startx" to load it.

---

### Post by HermanAB on 2009-08-14
Change the runlevel to 3 then Gnome won't be running.

---

