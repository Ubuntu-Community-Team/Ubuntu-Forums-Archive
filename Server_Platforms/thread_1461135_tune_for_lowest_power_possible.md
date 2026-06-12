---
title: "tune for lowest power possible"
date: 2010-04-23
forum: Server Platforms
---

### Post by walden on 2010-04-23
I've got a VIA Nano mini-itx box that I use as an always-on headless download box and web server. I installed the Ubuntu Minimal install distro with the intention of having the system as streamlined as possible, no unnecessary processes using up CPU time and power, etc.

I believe the hard disk is always on as I can usually hear it spinning (If I listen carefully enough!). 

My questions are:

Is it a good idea to have the hard disk spinning permanently? Especially with regards to life-expectancy of the drive and power consumption...

and...

How can I run the server in the most power-efficient way? I've enabled laptop-mode-tools in an attempt to spin-down the HDD. Are there any other tricks I can use to reduce the power requirement?

I don't yet have a kill-a-watt so I can't measure exact power usage yet but I'm looking to buy one.

Thanks in advance

---

### Post by tgalati4 on 2010-04-23
Those via boxes are pretty efficient, 10 watts or so.  No way to get around the spinning hard disk for a server.  The operating system needs to be able to write log files and all devices in linux are treated as files.  With enough RAM, you can run completely in RAM, but this is awkward for a server and it makes upgrading difficult.

The biggest way to save power is to have the server shut itself off at night and have the BIOS power it back up in the morning.

The other way to do it is to have wake-on-lan enabled and put a WOL script on each machine's desktop.  When you need the server, double-click the wake icon and in a couple of minutes, your server will be up.

Here's a script that I use:

tgalati4@tpad-Gloria7 ~/Projects/scripts $ cat wake_server.sh
#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan xx:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan xx:0D:56:FE:B9:D6
sleep 3
/usr/bin/wakeonlan xx:0D:56:FE:B9:D6
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Booting"  "You'll be up in 3 minutes."
sleep 200
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "GC-Development Server is Alive" "You can login now."
exit 0

---

### Post by ian dobson on 2010-04-24
> **tgalati4 said:**
>  No way to get around the spinning hard disk for a server.  

Oh yes there is, just boot from a flash device (CF or USB), just setup the system to power down the HD when not required and make sure your log files are written to the flash.

I've been running my MythTV frontend system like this for about 1 1/2 years without any problems.

Regards
Ian Dobson

---

### Post by tgalati4 on 2010-04-24
Writing log files to flash will shorten a flash drive's life, but they are cheap.  The kernel bundles up writes to flash to reduce wear.  Flash boot is more cumbersome when setting up several server funtions.  A mythTV front end is a client.  Try running your mythTV backend with flash.  See how long it lasts.

---

### Post by ian dobson on 2010-04-25
> **tgalati4 said:**
> Writing log files to flash will shorten a flash drive's life, but they are cheap.  The kernel bundles up writes to flash to reduce wear.  Flash boot is more cumbersome when setting up several server funtions.  A mythTV front end is a client.  Try running your mythTV backend with flash.  See how long it lasts.

Please tell me what makes a server install so special? I have a Linux box in the company that boots from a IDE-Flash card that collects process data from a machine and it's been running since 2005 with out any problems.

On a server you should split off your application data to a seperate drive/partition anyway, so booting froma small HD or a CF makes no difference.

True flash drives don't live for ever (nether do harddisks) but if your running a server then you'll surely have good backups. I know I do for all my boxes.

Regards
Ian Dobson

---

