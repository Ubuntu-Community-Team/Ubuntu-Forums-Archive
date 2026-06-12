---
title: "Ubuntu 10.04 server edition not booting properly, monitor shutting down"
date: 2010-05-16
forum: Server Platforms
---

### Post by donnacha on 2010-05-16
Hi there,
I 10.04 32bit server edition on a box I had lying around, set it up for samba+upnp, and everything was going great. 

When rebooting, the server now turns the monitor off, and I'm not sure if anything's loading. I see the initial dell splash screen, and hear the hard drive start to run, and then the monitor goes into standby. Any ideas how to get it back? 

Thanks,
donnacha

---

### Post by ilynx on 2010-05-16
donnacha,

I am new to this Linux stuff, so you might want to wait for more experienced users to chime in.  However, I just put together a server myself with the 64bit version and had the exact same problem.  After two days of trying to figure out what happened, I decided to try it all again from the beginning.  I assure you I followed all of the exact same steps from beginning to end, but the second time, it just worked, and has worked flawlessly since.  So, if you have a basic installation going, it probably wouldn't take too much time to try it again just to see if the first time didn't work right for some reason.

Good luck,

ilynx

---

### Post by newbean on 2010-06-19
I just installed (twice) Ubuntu 10.04 Server and my monitor went to sleep on boot-up. 

I installed with:
  auto-login
  LAMP server
  DNS
  Java Tomcat Server

SSH works, 
Ctrl-Alt-F3 does not work.

My computer is an HP 1540n 
AMD X2 processor 
nVidia Graphics card
HP vs 17e 17" FlatPanel LCD Monitor

The Ubuntu Gutsy Server edition did'nt have this problem. (wink)

---

### Post by oldfred on 2010-06-19
when I installed desktop version monitor went to sleep. 

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Unless you installed desktop this will not work.
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

This may be the commands to install:
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

---

### Post by deep07004 on 2011-01-13
Hi 
I'm getting the same problem with ubuntu 10.04 server.
Monitor goes to sleep mode on boot up.
Anybody have a solution ?????

Thanks in advance

---

### Post by chrislynch8 on 2011-01-13
I have seen a problem with HP before not just for server installs but even installing windows XP. THe monitor going to sleep on Boot.

Shutdown it down remove power and cycle through the RAM one by one this has fixed it in the passed.

This is the second post re HP I see on the one page, plus it happened a Clients PC yesterday.

---

