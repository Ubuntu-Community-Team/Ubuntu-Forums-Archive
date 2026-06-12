---
title: "Lubuntu 12.04 not booting...any ideas?"
date: 2011-11-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MG&amp;TL on 2011-11-14
hi guys-now I don't mind breakage in development releases, but I tried the most recent Lubuntu 12.04 and it booted and installed fine, but when I rebooted, It boots to a blank screen, and stays there. Any ideas to get it working?

---

### Post by 2F4U on 2011-11-14
Can you get to a console and look at the log files? May be graphics related, so could you give some information about your hardware?

---

### Post by ronacc on 2011-11-14
I haven't been able to get any of the 12.04 lubuntu daily's to boot to desktop after install , you may be able to get to a terminal with ctrl>alt> Fx ( where x= 1 to 6 ) when I mounted my latest install from another partition I found that the installer created a blank ( except for 4 hidden files ) /home/<me> no /Downloads /Documents no /desktop nothing except those 4 hidden files . Thats what is probably hanging the boot sequence it can't find a useable /home/<user> directory .

---

### Post by MG&amp;TL on 2011-11-14
Can't get to console at all, just boots from grub to blank screen. Recovery mode spits out a few bits of text and hangs. Maybe I'll try  bit later.

---

### Post by jerrylamos on 2011-11-14
> **MG&TL said:**
> Can't get to console at all, just boots from grub to blank screen. Recovery mode spits out a few bits of text and hangs. Maybe I'll try  bit later.
Have hope.  I've got a Thinkpad T40 running Lubuntu 12.04 after some valuable hints from Lucazade on the other Lubuntu 12.04 thread.  Running quite nicely.  Do note that's a 1.5 GHZ Pentium, 784 MB memory (less what the video screen uses.

The T40 with Firefox and Flash on Lubuntu 12.04 runs full screen BBC flash videos at full speed. Nice.

This is a Thinkpad R31, 1.0 GHZ Celeron, 512MB memory (less what the video screen uses).  Lubuntu 11.10 Full Screen BBC internet video a bit jerky.

When booting, try to do e on the grub line, and add nomodeset to the linux line.  If you ever get it to boot, sudo leafpad /etc/default/grub an add nomodeset just after quiet splash.  Then sudo update-grub.

What hardware are you using?

Jerry

---

### Post by P-I H on 2011-11-14
Happened to me too. To get it to boot, I booted into recovery mode. Selected the root mode, just typed exit and then selected normal boot. Now the login screen was presented. After login I used Additional Drivers to install the proprietary Nvidia driver. After this the system boots OK.
However this is with the Ubuntu and Unity login.

---

### Post by MG&amp;TL on 2011-11-14
Hmmm...have had problems with my graphics card in the past. Nasty nvidia one, which conflicts periodically with un-disablable intel in-built-one. I could try the nomodeset workaround.

Nvidia GeForce FX5200.

---

### Post by effenberg0x0 on 2011-11-14
If you want to try the proprietary nvidia driver, it uses dkms at each kernel update. 

(on recovery, press ctrl+alt+f6, login, get to a prompt)
mount -o remount,rw /
cd
mkdir nvidia_drivers
cd nvidia_drivers
wget [ftp://download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg0.run]("ftp://download.nvidia.com/XFree86/Linux-x86/290.06/NVIDIA-Linux-x86-290.06.run")
sh NVIDIA-Linux-x86-290.06.run
(answer yes to ALL questions)
reboot now

---

### Post by MG&amp;TL on 2011-11-14
I have wireless internet....wget ain't gonna work. I'll try recovery again, I think it hung last time because I knocked it over (don't even ask, my desk is a bit cramped).

---

### Post by effenberg0x0 on 2011-11-14
> **MG&TL said:**
> I have wireless internet....wget ain't gonna work.

Why?

**EDIT:**Oh, I see, you mean you need network-manager GUI to find a network, connect, etc. Is that it?
You can do it from console, it's just a little boring. Something like:

iwconfig (get the name or your wireless card - eth1 for example)
sudo iwlist eth1 scanning (view the available networks)
iwconfig eth1 essid TheNetworkYouJustChoseFromCommandAbove key "12345ABCDEFGH"
sudo iwconfig eth1 (see info about the network you chose - signal, security type, etc)
sudo dhclient eth1 (To get an IP from it)
nano /etc/resolv.conf (throw a DNS there, like Google's 8.8.8.8/4.4.4.4 - fast and easy to remember lol, or OpenDNS, etc)

That's it.

---

### Post by MG&amp;TL on 2011-11-14
my wireless is a pain to configure by command-line, and my router sucks. Network manager is the only way I've managed to do it successfully (actually, I did do it once, but it took two weeks).

---

