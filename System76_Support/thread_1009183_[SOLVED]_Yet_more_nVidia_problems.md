---
title: "[SOLVED] Yet more nVidia problems"
date: 2008-12-12
forum: System76 Support
---

### Post by ewg on 2008-12-12
Sys 76 Sable
Ubuntu 8.10

I had a recent post about correct resolution settings for a new monitor. It was solved by choosing the new nVidia driver from the 'hardware drivers' pull down menu. My resolution and refresh rate are still OK, BUT...when I try to configure nVidia x server I get this message:

 "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." 

AND I notice that if I go to the hardware driver pull down again, there is no nVidia driver selected. This seems to be a popular problem, judging by the many posts on various forums with lots of solutions offered. Just wondering the the System 76 guys have dealt with this and have a recommended solution.

Thanks,

---

### Post by thomasaaron on 2008-12-12
I've not seen it yet.

So, run this command...

sudo apt-get --reinstall install nvidia-glx-177
sudo nvidia-xconfig

Then, go see if you can select the right driver in System > Administration > Hardware Drivers.

If so, select it (if it's not already selected) and reboot.

---

### Post by ewg on 2008-12-12
Installing the glx 177.80 driver went OK, but then I ran the second command and got this:
ewg@ubuntu:~$ sudo nvidia-xconfig
[sudo] password for ewg: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

But, the System>Administration>nVidia X server settings does perform now and identifies my monitor by model # with correct resolution and refresh rate. Oddly, System>preferences>screen resolution pull down still shows "unknown" monitor with the correct resolution but refresh rates of 50, 51 or 107. Odd! 

Anyway, it looks good so I'm happy.

Thanks,

---

