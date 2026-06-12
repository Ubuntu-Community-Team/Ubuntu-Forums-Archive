---
title: "Open Office Ruined my Resolution"
date: 2008-09-10
forum: System76 Support
---

### Post by natibo on 2008-09-10
I had to force quit open office and reboot in order to open it again.  When I rebooted, my screen resolution changed to 1280x768.  I have no option to change it back to 1400x900.

I have a Sable runninh Hardy.

Help (Tom)?

---

### Post by thomasaaron on 2008-09-11
First, go to System > Preferences > Screen Resolution and see if you can select 1440 x 900.

If you are not offered that option, run your System76 driver (System > Admin > System76 Driver > Install Tab > Install Button) and then reboot your computer. Did that fix it?

If not, go to System > Administration > Hardware Drivers and see if your nVidia driver is enabled (if your Sable is one of the older, nvidia models). If not, enable it. Reboot.

Are you up and running?

---

### Post by natibo on 2008-09-11
None of this worked.  I am not given an option for 1440x900.  I even did a restore with the system76 drivers.

Whem I went to the Hardware Driver section it said no proprietary drivers were in use.

HELP!

---

### Post by Martje_001 on 2008-09-12
> **natibo said:**
> None of this worked.  I am not given an option for 1440x900.  I even did a restore with the system76 drivers.

Whem I went to the Hardware Driver section it said no proprietary drivers were in use.

HELP!
You can install the driver with 'Hardware Drivers' or EnvyNG.

---

### Post by thomasaaron on 2008-09-12
Try going to a command line and running...

sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig
sudo reboot now

---

### Post by natibo on 2008-09-13
That made it worse.

Here is the error I get.

natibo@ubuntu:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

[INDENT]VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/INDENT]

When I did a reboot, X would not start.  I had to do a reconfigure from the command prompt.  Now, visual effects will not work.

---

### Post by thomasaaron on 2008-09-15
OK, does the nVidia driver now show up in System > Admin > Hardware Drivers? If so, select it and reboot.

If not, contact me via email (support(at)system76(dot)com).

Question, did you try installing nvidia drivers from nvidia's website? If so, that would explain a lot.

---

