---
title: "Remote sleep/wake"
date: 2008-06-18
forum: Server Platforms
---

### Post by weryl on 2008-06-18
Hi,

I'm currently running a ubuntu server 24/7 on which i backup my other winxp computers using samba and a simple batch script (robocopy /m...).

What I'd like to do is to keep my server sleeping until i want to run the backup script. Then I want to wake it up, backup, and put it back to sleep. Can that be done through the batch script or do I have to use a specific software? And how?

Thanx alot,
Mike

---

### Post by artesvida on 2008-06-19
Who's running the script?  (If you're running robocopy, I would guess a Windows box, but I'm just checking to be sure.)

If you want the Ubuntu box to wake itself up, I don't know how you could do that -- I don't think you can.  But I'm pretty sure you could use the system's wake-on-lan feature (if available) to turn it on from another system.

---

### Post by weryl on 2008-06-19
> **artesvida said:**
> Who's running the script?  (If you're running robocopy, I would guess a Windows box, but I'm just checking to be sure.)

Yes the winxp machine is running the script from a .bat

> **artesvida said:**
> If you want the Ubuntu box to wake itself up, I don't know how you could do that -- I don't think you can.  But I'm pretty sure you could use the system's wake-on-lan feature (if available) to turn it on from another system.

I want the xp machine to wake and put the server (ubuntu) to sleep. How do I use that wake-on-lan? Is it from the BIOS?

Thank you,

Mike

---

### Post by artesvida on 2008-06-19
If you have a reasonably new motherboard with a built-in NIC, it should support Wake-on-LAN.  Make sure this option is enabled in the BIOS.

To "turn on" a sleeping machine, you need to send a "magic packet."  How?  I'm not sure -- since I've had no need for WoL, I've always disabled it on my networks.  Suggested reading:
[http://en.wikipedia.org/wiki/Wake-on-LAN]("http://en.wikipedia.org/wiki/Wake-on-LAN")

Now, putting the Linux system back to sleep, I think that's a bit trickier.  Never done that on a server -- you might need to install a power mgmt package to get it to sleep/hibernate in the first place.  Then I would experiment with rsh and see if I can issue the appropriate command from a remote workstation.

Good luck!

---

### Post by weryl on 2008-06-19
Thanx alot for the info.

I tried what you recommended and the WoL is indeed an option in the BIOS. I enabled it and used a few scripts (from wiki) to wake my server up but it didnt work. I'll try to update the BIOS and run more tests.

What does work and is quite easy to do is to put the server back to sleep after a few minutes of inactivity. This can also be done by setting the BIOS.

Neway i'll give more feedback when i get it working. I'd be a great feature since i wont be using the server very often, and always remotely.

Mike

---

### Post by Spiny Norman on 2008-06-19
Just a thought My dell systems (not server platforms) have a wake up @ feature. I default mine to midnight in case I have a power outage so as to get the machine up to do it's backup cron at 0100

---

### Post by weryl on 2008-06-20
> **Spiny Norman said:**
> Just a thought My dell systems (not server platforms) have a wake up @ feature. I default mine to midnight in case I have a power outage so as to get the machine up to do it's backup cron at 0100

Yea that's not a bad idea either. My WoL doesn't seem to work so I think I'll just use that for now (scheduled powerup/backup).

---

### Post by flamacue on 2008-08-17
> **weryl said:**
> I tried what you recommended and the WoL is indeed an option in the BIOS. I enabled it and used a few scripts (from wiki) to wake my server up but it didnt work. I'll try to update the BIOS and run more tests.
You will probably need to use ethtool to enable WOL in the driver config*.  See [[COLOR="Blue"]_this thread[/color]_]("http://ubuntuforums.org/showthread.php?t=460894").

> What does work and is quite easy to do is to put the server back to sleep after a few minutes of inactivity. This can also be done by setting the BIOS.
Now *this* is where I'm stumbling.  I have a desktop machine running Ubuntu Server 8.04 (Hardy Heron), and I can't find any way to suspend to RAM (STR/S3/sleep/standby).  In my searching, it seems that info on how to STR from the command line in Linux is scarce, and in Ubuntu scarcer still.  It seems** like the Ubuntu devs have this assumption that a *server* must be always on, so there's no need to be able to do this.  However, for a single user or family wanting a headless NAS, using Ubuntu Server (no unneeded GUI) with webmin, and STR with WOL makes a heck of a lot of sense, don't you think?

[/rant]

Anyway, I tried installing uswsusp from the repos (universe/utils).  It ordinarily includes a command called "s2ram", but apparently it's removed from the Ubuntu build.  (Why?)

I thought I read somewhere that Ubuntu's build of powersaved included s2ram, so I installed that, but doing
```
sudo find / -name "s2ram*"
```
yields no results, so apparently it's not in there.  (Or the package didn't install properly, since I have a CPU (AMD Sempron 2800+) that doesn't support CnQ..?)

I'm at a loss.  Can anyone shed some light here?  As I said, my CPU is an [[COLOR="Blue"]_AMD Sempron 2800+[/color]_]("http://en.wikipedia.org/wiki/Amd_sempron#Semprons_without_Cool.27n.27Quiet"), motherboard is a [[COLOR="Blue"]_Gigabyte GA-K8N[/color]_]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1701").


* I'm not sure "driver config" is the proper term, just trying to come up with a term that seems to fit my theory of how it works...see that other thread.

** I could be mistaken.



EDIT:  I've made some progress, but still having some trouble.

I believe the package I want is acpi-support, which includes the script /etc/acpi/sleep.sh.  Running this script appears to put my machine into suspend to RAM, and it almost wakes up when I push the power button (or the keyboard).  When it comes up, the screen is blank, except for a blinking cursor in the upper left corner.  It seems the only thing it responds to from the keyboard in this state is Ctrl-Alt-Del.

So for a while I didn't have much idea how to even find out what the trouble was; I don't know of any logfiles for acpi-suspend issues.  Eventually, I realized that the network does come back up, so I was able to see some error messages by executing the command from a remote terminal with ssh.

So, running
sudo /etc/acpi/sleep.sh
remotely shows the following before it finishes suspending:
```
me@mynas:/etc/acpi$ sudo ./sleep.sh 
There is already a pid file /var/run/dhclient.eth0.pid with pid 4557
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:85:d3:16:f5
Sending on   LPF/eth0/00:14:85:d3:16:f5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
```
And after restore, once the network came back up, the following showed in my ssh window:
```
 * Saving the system clock
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
 * Setting the system clock
ifup: interface eth0 already configured
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
```

Since it said that one of the problems is /etc/acpi/resume.d/17-video-restore.sh, here is the contents of that file:
```
#!/bin/sh

# Attempt to restore some video card state
if [ x$SAVE_VBE_STATE = xtrue ]; then
  vbetool vbestate restore <$VBESTATE
  if [ $VBEMODE != "3" ]; then
    vbetool vbemode set $VBEMODE;
  else
    vbetool vgamode set 3;
  fi
fi

# Restore video PCI state
if [ x$SAVE_VIDEO_PCI_STATE = xtrue ]; then
  for x in /sys/bus/pci/devices/*; do
    if [ -f /var/run/vga-pci-`basename $x` ]; then
        cat /var/run/vga-pci-`basename $x` >$x/config;
    fi
  done
fi
```

Can anyone help me figure out how to fix this?

Thanks in advance.



EDIT2:  Further investigation reveals that I remain at the command line on the local console, despite no feedback to the screen.  I was able to shutdown from the local console after resuming to a blank screen with cursor only, despite no echoing to the screen.

So, I guess this is a video issue.  Perhaps the following info will be relevant..?

```
me@mynas$ lspci |grep VGA
01:06.0 VGA compatible controller: S3 Inc. 86c325 [ViRGE] (rev 06)
```
(It's just an available PCI video card I had lying around.)

---

