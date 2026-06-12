---
title: "Server 10.04 LTS /dev/sda2 full"
date: 2010-09-19
forum: Server Platforms
---

### Post by mramsey on 2010-09-19
I have been running ubuntu server for quite some time without any issues until now. Please bear with my ignorance I know enough to be dangerous so I am asking before I continue any further. 

Here is some information on my setup:

I have an older Compaq ML330 G2 server that originally had windows server installed. I added my own raid controller and backup drive

sda is a 10000 rpm 15.4 gb scsi drive that contains a windows partition and a 9gb Ubuntu partition sda2.

raid consists of 4 250 gb drives in a raid 5 config
backup consists of WD green 1tb 5400 rpm that backs up the raid.

You can see some of the running system specs here [http://mramsey.homeip.net:8080](http://mramsey.homeip.net:8080)

You will see that sda2 is at 100% full and is creating havoc on my system.

How can I now go back and delete that original windows partition from the scsi drive? (without screwing up anything else) 

I also maintain the system with Webmin and am not the greatest with command line. Any help is appreciated or even a nudge in the right direction.

---

### Post by LightningCrash on 2010-09-19
Are you using GRUB to boot?


If so, get a GParted LiveCD and boot the server from that. Used GParted to delete the Windows partition and resize the Linux root partition.
Reboot and you should be golden.


[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by mramsey on 2010-09-19
Thanks... I am using grub so I will give it a .

---

### Post by mramsey on 2011-02-19
Whoa!! Reviving my old post - It has been a while. I initially fixed the issue by deleting the windows partition all together. That worked.

Now months later you can see the issue is back - I am at a loss as to figure out why it is filling up? Are there temp files somewhere I need to remove from updates or something. Please bear in mind that only the OS is running on sda2.  The main thing I use thixs for is file sharing. :confused::confused::confused:

You can see some of the running system specs here [http://mramsey.homeip.net](http://mramsey.homeip.net)

---

### Post by mramsey on 2011-02-19
[Solved]

After more research I see that I had somewhere around 7 GB of mail logs. Odd since I do not use the mail functions. Now to figure out why they were there to begin with :rolleyes:

---

### Post by kleverbear on 2011-09-26
mramsey I'm having a similar issue to you, losing space to an unknown source. Were where you able to find these mystery mail logs.

I am as well using 10.04LTS

---

