---
title: "NAS stalls &quot;smbd blocked ... 120 seconds&quot;"
date: 2011-11-05
forum: Server Platforms
---

### Post by farproc on 2011-11-05
I'm running an Ubuntu Server based NAS as a media server.
Recently, my media player has started to stall while streaming movies off of it, and when I check the console there is typically a message like

  [23456.6893939] INFO: Task smbd:1566 blocked for more than 120 seconds.

Other than that message I really don't know where to start to try and diagnose an issue like this on ubuntu. [https://help.ubuntu.com](https://help.ubuntu.com) is all very helpful on how to get things set up, but trying to diagnose issues is not covered at all.

My hardware is a HP Proliant Microserver, with Ubuntu 11.4 installed on a 4GB usb thumbstick. My media drive is a 2TB Seagate Green disk, formatted with ext4, that I've mounted via fstab:

  UUID=.... /mnt/media1 auto defaults 0 2

Ive googled this issue and have not found much clarity: Some people had a similar issue with a 1TB Western Digital drive that parked its heads agressivly. Others had a similar message caused by problems in the schedulers of earlier Linux builds.

I don't know how to verify that the disk is actually healthy, or even that its caused by the disk at all and might not be an issue with samba or something.

---

### Post by farproc on 2011-11-08
Seriously? Nothing at all?
Are there relevant log files to look at or tools I should be running to try and diagnose this?
Windows has a system event log. And a disk manager gui app that sometimes shows some SMART stats of disks.
I don't know where to start on Linux, and [http://help.ubuntu.com](http://help.ubuntu.com), while a useful resource initially when setting a linux server up for the first time, just doesn't seem to have any "And now, when things have gone wrong, these are the tools you might want to know about..." type articles.

---

### Post by rubylaser on 2011-11-08
Sounds like the drive is either delaying after resuming from spinning down the platters, or that you might want to check the status of your hard drive.

```
sudo apt-get install smartmontools
```
```
smartctl -a /dev/sd<device_letter_here>
```

Checking iotop
```
sudo apt-get install iotop
```
Check the activity
```
iotop
```

Finally, check the logs for your device...
```
dmesg | grep /dev/sd<device_letter_here>
```
```
cat /var/log/syslog | grep /dev/sd<device_letter_here>
```

That's a start.

---

### Post by farproc on 2011-11-09
That was just the sort of diagnostic info I was looking for. thanks.

---

### Post by bab1 on 2011-11-09
> [23456.6893939] INFO: Task smbd:1566 blocked for more than 120 seconds
This format looks like the output of dmesg.  This is the log from /var/log/messages.  From the command line you can issue the command like this```
you@there$ dmesg
```

The last little bit of mine looks like this ```
[COLOR="Red"][   12.700080][/COLOR] CPU1 attaching sched-domain:
[COLOR="Red"][   12.700082][/COLOR]  domain 0: span 0-1 level MC
[COLOR="Red"][   12.700085][/COLOR]   groups: 1 0
[COLOR="Red"][   18.450039][/COLOR] eth0: no IPv6 routers present

```

You might take a look at all the logs (kern, syslog, etc) located at /var/log/.  I use the command *tail *to look at the last part of the log.  See the man pages for a description ```
man tail
```

---

