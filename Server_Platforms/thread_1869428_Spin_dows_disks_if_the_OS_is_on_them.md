---
title: "Spin dows disks if the OS is on them?"
date: 2011-10-25
forum: Server Platforms
---

### Post by darkod on 2011-10-25
Hello all.

I am planning to build myself a simple home file server with Ubuntu Server. Strictly low usage, just a central storage spot.

So far my plan is to use 2 x 1TB disks with software RAID1.

My problem: Because of the low usage expected I would like to spin down the disks when ever possible, like after 15mins or 30mins inactivity. But if the OS is on them can this be done? My common sense would say there is something written on the OS disk once in a while, so it will never go in sleep (spin down).

One idea was to use an ide-to-CF adapter and a CF card for the OS but that disappeared as soon as I realised that my board of choice has no IDE. I would have loved the CF card approach though.

Any chance of spinning down the array with the OS on it?

Thanks in advance.

---

### Post by HermanAB on 2011-10-26
Howdy,

Just stop the system log daemons.  That will allow the disks to spin down.

---

### Post by Demented ZA on 2011-10-26
> **HermanAB said:**
> Howdy,

Just stop the system log daemons.  That will allow the disks to spin down.

Really? My server with RAID acts as a gateway/firewall as well. I'd like to still keep logging functionality for security reasons. Can one change the location of logs to say a flashdrive, and still have the disks in the RAID array spin down?

Awesome tip. Thanks!

---

### Post by darkod on 2011-10-26
Thanks.

Another idea is just getting a 4GB or 8GB USB stick and use it as bootable OS disk. Is it worth it? Or will it die soon because of read/write cycles?

And in such a setup can sometimes with a reboot the device labels /dev/sda, /dev/sdb, etc get changed, thus messing up the array config?

---

### Post by Demented ZA on 2011-10-26
> **darkod said:**
> Thanks.

Another idea is just getting a 4GB or 8GB USB stick and use it as bootable OS disk. Is it worth it? Or will it die soon because of read/write cycles?

And in such a setup can sometimes with a reboot the device labels /dev/sda, /dev/sdb, etc get changed, thus messing up the array config?

I had two Flash disks pack-up this way. A 512mb one and and 8GB (over about a  year of running each). I'd say an HDD is best. If its just for testing, then its fine. Although its a lot of effort if everything works and you decide you want to keep running the current configuration.

As for the array and disks, they shouldn't get messed up. Just make sure your FSTAB entries are correct (should be correct by default) and use the UUID of each drive (will be unique to each drive). If you are running RAID with dmraid, it uses the UUID anyways, so you should be fine.

---

### Post by darkod on 2011-10-26
> **Demented ZA said:**
> I had two Flash disks pack-up this way. A 512mb one and and 8GB (over about a  year of running each). I'd say an HDD is best. If its just for testing, then its fine. Although its a lot of effort if everything works and you decide you want to keep running the current configuration.

As for the array and disks, they shouldn't get messed up. Just make sure your FSTAB entries are correct (should be correct by default) and use the UUID of each drive (will be unique to each drive). If you are running RAID with dmraid, it uses the UUID anyways, so you should be fine.

I am planning to use softraid, which I guess would be mdadm. The dmraid is for mobo raid (fakeraid) if I got it right.

I have little experience with the server version and hence not sure if UUID or sdX is used. UUID don't change, I know that. And sdX don't change also for HDDs unless you change the SATA port where it's connected. But when a USB stick is in play, I don't know if during some restart it can change the "order" of detecting the disks, hence the sdX letters.

I will probably go for the OS on the array anyway. The CF was an interesting idea but I want this board because of SATA3 ports (Atom mini-ITX boards don't have SATA3, at least not the budget ones), but on the other hand it doesn't offer IDE slot.

Because of the SATA3 my first choice is a board with AMD E-350 from Asrock or Sapphire. They pack 4 SATA3 ports, plenty even for further array upgrades/addtions.

---

### Post by Demented ZA on 2011-10-26
> **darkod said:**
> I am planning to use softraid, which I guess would be mdadm. The dmraid is for mobo raid (fakeraid) if I got it right.

If memory serves correctly, Fakeraid is not the same as software RAID. Fakeraid is what motherboard manufacturers advertise when they say a motherboard supports RAID 0, 1, 3, 5 etc. and then you need a driver for Windows to see the array, but the software and CPU is still doing all the work. Software RAID on the other hand, does exactly what a dedicated RAID card does, and is independent of hardware. Basically they are the same except Fakeraid is fake advertising, whereas software RAID, does what it says.

> 
I have little experience with the server version and hence not sure if UUID or sdX is used. UUID don't change, I know that. And sdX don't change also for HDDs unless you change the SATA port where it's connected. But when a USB stick is in play, I don't know if during some restart it can change the "order" of detecting the disks, hence the sdX letters.

MDRAID uses UUID's afik. It doesn't change, nor does mounts, even if detection order gets changed. Flash drives are usually mounted as /dev/sda1, and the raid array will be mounted as /dev/md0 (being a collection of the drives in the array). If your BIOS boots from your flashdrive, it will always be detected first. Other flash drives won't boot, as you probably won't have any master boot records on them.

> I will probably go for the OS on the array anyway. The CF was an interesting idea but I want this board because of SATA3 ports (Atom mini-ITX boards don't have SATA3, at least not the budget ones), but on the other hand it doesn't offer IDE slot.

Because of the SATA3 my first choice is a board with AMD E-350 from Asrock or Sapphire. They pack 4 SATA3 ports, plenty even for further array upgrades/addtions.Not sure what CF is. By SATA3, are you talking about SATA 6GB/s? No HDD's can attain SATA 6GB/s speeds yet, and they probably never will. Even the WD Caviar Black series with SATA6GB/s support don't reach this speed. Only SSD's are breaking the 3GB/s barrier at the moment.

I'm running my server on 3 WD Caviar black SATA6g drives, on an Asus motherboard. Everything is on the array, including virtual guest OS's. My CPU load is at 4% when running Windows 7 and Ubuntu desktop at the same time. But both were sluggish. Took me a while to figure out that the CPU, RAM, Mobo wasn't the problem. It was the sheer number of IO operations for each OS to the RAID array. Moved my guest OS's to a seperate old 120GB SATA HDD, and everything is happy.

If you are looking at an Atom based design, chanches are you probably won't run virtualization, and then having the os and everything on the RAID array is probably fine.

I used virtualization for a seedbox to download stuff, because I couldn't get decent headless linux alternatives at the time, but all that changed and the virtual machines are just for stuffing around now, as everything else is running linux native.

---

### Post by darkod on 2011-10-26
>  Not sure what CF is. By SATA3, are you talking about SATA 6GB/s? No  HDD's can attain SATA 6GB/s speeds yet, and they probably never will.  Even the WD Caviar Black series with SATA6GB/s support don't reach this  speed. Only SSD's are breaking the 3GB/s barrier at the moment. 

CF = Compact Flash memory card. They make IDE-to-CF adapters which you can plug into the IDE slot on your board, and then the card goes into the adapter. For the BIOS, that is like a small flash disk with capacity that depends on the card capacity.

I am aware SATA3 is useless for mechanical disks but I was hoping you get some speed advance. Anyway, these days prices are actually cheaper for SATA3 disks then for SATA2. And if I buy SATA3 disks I would rather get a board with SATA3 right away.

The chipset for the Atom (NM10) doesn't offer SATA3, so I switched to a mini-ITX board with integrated AMD E-350 cpu. It has a total of 18W so I hope spinning down disks will also help keep the power consumption at minimum.

---

### Post by darkod on 2011-10-26
After reading around and looking at my 10.04.1 test server, in the /etc/init folder the only daemon that looks like the system log is rsyslog.conf.

Is rsyslog what I have to disable and is it the only one?

I am slightly confused because on google there is also info about a daemon called syslogd. Has that been replaced by rsyslog?

Thanks.

---

### Post by HermanAB on 2011-10-27
Yes, syslogd has been replaced.  Names now vary.  So some sleuthing is required with top, ps -e and so on.

---

### Post by darkod on 2011-10-27
Thanks Herman, and sorry to be such a pain... :)

Yeah, it's the rsyslog allright. The content of the /etc/init/rsyslog.conf:

```

# rsyslog - system logging daemon
#
# rsyslog is an enhanced multi-threaded replacement for the traditional
# syslog daemon, logging messages from applications

description    "system logging daemon"

start on filesystem
stop on runlevel [06]

expect fork
respawn

script
    . /etc/default/rsyslog
    exec rsyslogd $RSYSLOGD_OPTIONS
end script

```

This is from my desktop version, on my server version it's little bit different but very similar. From reading around it says the best way to disable it is to comment out the start line. Is that right?

I did a quick test on my test server. First I ran:
ps aux | grep rsyslogd

and it was showing the daemon running. After commenting out the start line and rebooting, the daemon was not running any more.

Is this the proper way to disable it and is this the only daemon doing the logging? After disabling it the disks can spin down?

Thanks again.

---

