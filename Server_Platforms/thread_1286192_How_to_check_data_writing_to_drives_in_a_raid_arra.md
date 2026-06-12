---
title: "How to check data writing to drives in a raid array?"
date: 2009-10-08
forum: Server Platforms
---

### Post by photoman355 on 2009-10-08
Hi 

I recently bought my first server (HP ML115 + P400 SmartArray with Ubuntu Server 8.04LTS) to install at my work. I've tinkered with PC's and software for years to a decent level but am fairly inexperienced on the server side of things.  I have 2 raid 1 arrays and want to check that the data is writing to both disks in each array as data integrity it critical.

What's the best way to test the data is writing to both disks?  Simulate a failure?  I've heard about disconnecting one of the disk cables to break the array then letting it rebuild after connecting.  This seems logical but there must be an easier way?

Thanks for your help.

---

### Post by rolnik on 2009-10-08
You could try to 'fail' a disk that you want to simulate failure on:
```

[COLOR=#000000]mdadm /dev/md0 --fail /dev/sdc1 --remove /dev/sdc1

```

Then you could add more data to the /dev/md0 to simulate some activity on the drive while you 'order' a replacement disk.

Later in the day, you can simulate getting the disk 'delivered' and 'installed', and simply use the --add option to add the disk back in.  The whole time, in reality, the disk never leaves your case and is never disconnected.

See this link for a short cheat-sheet of frequent mdadm commands:
[http://jazstudios.blogspot.com/2007/03/mdadm-software-raid-usage.html](http://jazstudios.blogspot.com/2007/03/mdadm-software-raid-usage.html) 

[/COLOR]

---

### Post by photoman355 on 2009-10-09
Thanks Rolnik. 

I think the mdadm command you're taking about only applies to the software raid options in ubuntu.  I'm trying to find out the best way to check the data is writing to the disks using hardware raid (I'm using an HP P400 raid controller).

Any ideas how to test?

---

### Post by trundlenut on 2009-10-10
have a look at [this]("http://ubuntuforums.org/showthread.php?t=1019045") thread and see if there is a package available for your raid controller, that should allow you to get more info on the status of the raid arrays.

---

