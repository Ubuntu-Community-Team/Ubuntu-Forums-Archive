---
title: "How to ACTUALY boot in CLI???"
date: 2010-12-15
forum: Server Platforms
---

### Post by dansimon on 2010-12-15
I whant to boot my system directly in CLI, bypassing the graphical splash screen and
gdm. The traditional (aka debian) way of doing this is to run "sudo update-rc.d gdm remove" in a  terminal, then to replace "quiet splash" in /boot/grub/grub.cfg with "text"
followed by "sudo update grub".

Neither of these operatins work in Ubuntu 10.10 however, and i am having a hard time understanding why?? Can anyone help?

---

### Post by kevinthecomputerguy on 2010-12-15
You can install webmin. Then once in webmin navigate to the "bootup and shutdown module", select gdm, and press the "disable now and at startup" button. Then reboot.
 
Or better, start orver and download the ubuntu server cd, which has no gui.

---

### Post by msandoy on 2010-12-15
What you need to do, is to change the default runlevel to 3. See this page for some info regarding runlevels. Runlevel 3 is text mode, and 5 gui, if I'm not mistaken. 
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)
May be someone with more knowlege on the matter can give some input. :-)

---

### Post by dansimon on 2010-12-16
These methods might work for Ubuntu 9 or something, but they do not work on Ubuntu 10.10 (hence the question, how to *actu*a*ly *boot in CLI). First in the Webmin solution, the gdm *is *turned off. I guess this is because of the "update-rc.d gdm remove" command i
did urlier. But even so, gdm still starts...
Secound there is no /etc/inittab file in Ubuntu 10.10 (the walkthroug you referd to sugested to alter the init value in that file). 

The simple solution would probably be to switch distro (Ubuntu server, or better yet Debian), but this shouldnt be necessary. There has to be some way of booting in CLI in Ubuntu 10.10... (PS! do you still boot in CLI if you install a DE in Ubuntu server?)

---

### Post by kevinthecomputerguy on 2010-12-16
Is there another display manager running, like "unity" or something.

---

### Post by lykwydchykyn on 2010-12-16
The simplest and least destructive way to disable gdm in maverick is to rename /etc/init/gdm.conf to /etc/init/gdm.conf.noexec.

Ubuntu has been moving away from the old sysv init system for some time, and with Maverick a lot of the main services are now moved away, so it's best to get out of the habit of maintaining things with sysv tools (for example, using "sudo service foo restart" instead of "sudo /etc/init.d/foo restart").  I know Debian Squeeze is moving to some new kind of init system, though I don't know if it's upstart or not.  I just remember something about it when I upgraded some of my lenny systems.

Basically, /etc/init/ (not /etc/init.d) is where configuration data for services is stored.  It's more complicated than just "which runlevel do I start on" now -- there are other events that can trigger a service to start/stop/restart (which is why they moved away from sysv init).

But, yeah, just rename that file and it shouldn't start anymore.

---

### Post by arrrghhh on 2010-12-16
> **dansimon said:**
> (PS! do you still boot in CLI if you install a DE in Ubuntu server?)

Why would you install a full-blown DE on ubuntu-server?  Kinda defeats the purpose...

---

### Post by dansimon on 2010-12-17
Thax! That did it :D
The reason i whant to boot in CLI, and still have a DE (or WM), is partly because
i whant to have X available when i need it, and partly because of increased geek
cred ;)

---

