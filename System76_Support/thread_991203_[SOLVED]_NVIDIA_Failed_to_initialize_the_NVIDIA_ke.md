---
title: "[SOLVED] NVIDIA Failed to initialize the NVIDIA kernal module"
date: 2008-11-23
forum: System76 Support
---

### Post by Blacktalon on 2008-11-23
Hello,

I been having some issues getting my nvidia to work, right now all I have is just the basic simple settings.  I activated my driver 177, and have also tried 173.  But they don't show as active and keeps saying "No Proprietary are in use on this system."

I have also checked my rc.local for any commands of nvidia and there is none there.

I also have added RUN+="/sbin/modprobe nvidia" to the second to last line in /etc/udev/rules.d/90-modprobe.rules

But my results still remain the same, can anyone help me result this issue, please.

Thanks,
  ~BT

---

### Post by Vadi on 2008-11-24
Try uninstalling Ubuntu's driver package, then install drivers from nvidia website: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by thomasaaron on 2008-11-24
Vadi, we do not recommend loading the drivers from nVidia's site, as it can create problems after future upgrades that are very difficult to resolve.

Blacktalon, the following worked for another customer with the same problem. Please give it a shot.

Try this:

1. sudo gedit /etc/rc/local
-If there are any nvidia lines in there, comment them out
-Save and exit

2. sudo gedit /etc/udev/rules.d/90-modprobe.rules
- Add the following line *right above* the last line in the file.
RUN+="/sbin/modprobe nvidia"
- Save and Exit
- Reboot

Fixed?

---

### Post by Blacktalon on 2008-11-25
Ok thomasaaron,

I did what you suggested but still no change.

Here are the errors I am still getting at start up.

(EE) Nvidia (0): failed to load nvidia kernel module
(EE) Nvidia (0): ***Aborting***
(EE) Screens found, but none have a useable configuration.

---

### Post by thomasaaron on 2008-11-25
OK, Let's try this route...

#Completely remove nvidia module
sudo apt-get --purge remove nvidia-glx-177

#Back up your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Re-install nvidia
sudo apt-get install nvidia-glx-177

#Re-create your xorg.conf file. Use all defaults.
sudo dpkg-reconfigure xserver-xorg

Now, go to System > Administration > Hardware Drivers and enable 177.

Reboot.

Fixed?

---

### Post by Blacktalon on 2008-11-26
Nope still not fixed, I am still getting the same errors.

---

### Post by thomasaaron on 2008-11-26
1. What is your System76 model number?

2. What kernel version are you running... ```
uname -r
```

3. Does it work with a previous kernel? (When you see the grub countdown, press 'Esc'. Then select a previous non-recovery-mode kernel to boot from.)

---

### Post by Blacktalon on 2008-11-26
1. My system model is  wilp5

2. I am running kernel 2.26.27-7 server (shouldn't that be client, instead of server?)

3.  It use to work with Ubuntu 8.04, before I upgraded.  And it had work with 8.10 when I had first upgraded (for about 2 days then it just stopped and starting giving me errors).

---

### Post by Blacktalon on 2008-11-26
Ok, I changed the kernel to 2.26.27-7 generic and it starts up perfectly with no errors, and nvidia drivers working and being used.

---

### Post by thomasaaron on 2008-11-26
Yeah, that server designation is weird. I don't think you should be getting that (but I'm working from home until Monday, so I can't really check it). But I'm wondering if you still have the old nvidia module installed, which won't work with Intrepid.

Try this...

#Make sure the old nvidia driver was removed. It may be conflicting...
sudo apt-get --purge remove nvidia-glx-new

#Back up your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Re-install current nvidia module
sudo apt-get --reinstall install nvidia-glx-177

#Re-create your xorg.conf file. Use all defaults.
sudo dpkg-reconfigure xserver-xorg

Now, go to System > Administration > Hardware Drivers and enable 177.

---

### Post by Blacktalon on 2008-11-26
Ok, I tried all that and the problems came back, but if I change my kernel back to 2.26.27-7 Generic it works again.

---

### Post by thomasaaron on 2008-11-26
OK. I'll consider this one solved. 

Somehow you were running the wrong kernel. I'm running the *****-7-generic too. So, that is definitely the appropriate current kernel for your machine.

---

### Post by Blacktalon on 2008-11-26
Ok, thank you.

---

### Post by bruj0 on 2009-03-21
Hello!

I had a similar problem, when I decided to upgrade from NVIDIA 177 driver which worked fine to a newer 180 driver. I managed to solve it and come back to the good old 177 driver. I am using UBUNTU 8.10, kernel 2.6.27-11-generic, graphic card Nvidia GeForce 9300M GS (rev a1).

What I did:
1) I installed the new 180 driver taken from NVIDIA webside from command line using

sudo sh *pkg2.run

My error was that I did not previously uninstall the 177 driver.
After this, when booting, error appeared "Failed to initialize NVIDIA kernel module", "Fatal error: no screens found". And the low-graphics configuration loaded. Then, I tried to re-install 177 driver using jockey (Administration->Hardware drivers) - I activated the 177 driver there, but after reboot the same errors appeared.

2) Then I removed using Synaptic all packages that have something to do with nvidia drivers:
nvidia-settings, nvidia-180-kernel-source, nvidia-common, nvidia-71-modaliases, nvidia-173-modaliases, nvidia-177-modaliases, nvidia-glx-180, smartdimmer, nvidia-glx-177, nvidia-177-kernel-source

Then, the booting error changed to the following:
"Failed to load module "nvidia" (module does not exist, 0)"
"No drivers available"

3) I followed then advice from this thread:
> > **thomasaaron said:**
> OK, Let's try this route...

#Completely remove nvidia module
sudo apt-get --purge remove nvidia-glx-177

#Back up your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Re-install nvidia
sudo apt-get install nvidia-glx-177

#Re-create your xorg.conf file. Use all defaults.
sudo dpkg-reconfigure xserver-xorg

Since, nvidia-glx-177 was not present, it was not removed. The (Menu->Administration->Hardware drivers) said "no proprietary drivers in use" and nvidia driver was not in use after reboot.

4) Then, I did this
[QUOTE]
1. sudo gedit /etc/rc/local
-If there are any nvidia lines in there, comment them out
-Save and exit

2. sudo gedit /etc/udev/rules.d/90-modprobe.rules
- Add the following line *right above* the last line in the file.
RUN+="/sbin/modprobe nvidia"
- Save and Exit
- Reboot
After that, nvidia drivers still did not load and were not in use.

5) Then, I changed the xorg.conf file active at that moment

> Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


> To the earlier backup version that I realized to have:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

After that, the gui is loading properly and nvidia 177 driver is loaded and in use (compiz things work) and nvidia-settings also works. And the Administration->Hardware drivers menu sees the nvidia driver but refers to it just as "nvidia" but not "nvidia 177" as it was before the whole thing.
I consider it as a relative success, but I did many things that I did not understand =)
Hope it will be helpful for others.

---

