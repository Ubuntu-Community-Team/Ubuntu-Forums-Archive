---
title: "start ssh earlier"
date: 2008-06-20
forum: Server Platforms
---

### Post by niko7865 on 2008-06-20
The only access I have to my server is through ssh, and for the most part it works fine. However, I would like ssh to start earlier (before checking root filesystems) so that I can monitor what is going on. I would like to be able to see that is checking the filesystem or whatever other errors might keep it from booting all the way. It is a real pain to take it out of the rack and drag a monitor and keyboard to it whenever something goes wrong.

[Hardy Server i386]

---

### Post by gtdaqua on 2008-06-21
OpenSSH server starts after basic networking starts. If you want to see what is the problem with your server in booting up, run 'dmesg' to see the errors listed or open the '/var/log/messages' file and analyse.

---

### Post by niko7865 on 2008-06-21
I want it and networking to start before the standard filesystem check then. When I power on the server and I can't ssh into it within 5 minutes I usually just hold the power button down, then throw in a video card/monitor/keyboard. I can't wait the hour it takes to scan a single 750GB disk. I'd like ssh so I can see that it is just fdsk and not an error.

---

### Post by gtdaqua on 2008-06-21
There's something wrong if your filecheck is happening everytime. Try to see wats wrong with your 750GB HDD. Ubuntu should straight boot you to the prompt. Also, filecheck is only checked once every 30 mounts.

Filesystem cant be scanned when it is mounted and SSH or network will not come up until filesystem is mounted!

---

### Post by niko7865 on 2008-06-21
There's nothing wrong with the drive, its just that there are 14 of them installed at different times so every few boots it scans one or two of them. The root file system is on a 6GB partition of one of the drives, and I don't mind when it has to scan that. Maybe if there was a way to mount/scan the other partitions and drives after networking and ssh starts?

---

### Post by windependence on 2008-06-21
Well unfortunately most Unix and Unixlike systems are not meant to be constantly rebooted. There should almost never be a reason to do this unless you are modifying a kernel or changing bad hardware. Why are drive being constantly changed?

-Tim

---

### Post by koenn on 2008-06-21
> **niko7865 said:**
> The only access I have to my server is through ssh, and for the most part it works fine. However, I would like ssh to start earlier (before checking root filesystems) so that I can monitor what is going on. I would like to be able to see that is checking the filesystem or whatever other errors might keep it from booting all the way. 

your networking software and the shell you need for your ssh session are files in a filesystem. There's no way you can load those before the OS has booted and the filesystem is mounted and ready to be used. 

The only way around this is with additional hardware in your server, eg something like HP "lights out" [http://h18013.www1.hp.com/products/servers/management/ilo/](http://h18013.www1.hp.com/products/servers/management/ilo/)

---

