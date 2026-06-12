---
title: "[Software Raid] No option &quot;Physical volume for Raid&quot;"
date: 2008-10-06
forum: Server Platforms
---

### Post by --Sven on 2008-10-06
As mentioned in the topic title; i don't have the option  "Physical volume for Raid". Ofcourse this is while i (at least; i try) to install Ubuntu server 8.04.1. (I have downloaded the alternative CD)
The weird thing is that if i boot the CD in vmware that i can select "Physical volume for Raid" !
Also i have searched over the internet by using google and found [a topic](http://ubuntuforums.org/archive/index.php/t-611462.html) that is nearly my problem, only the user usses Ubuntu Desktop (7.10 in his case). The solutions mentioned in this topic didn't solved my problems.

The hardware i am using:
Acer Aspire with AMD athlon64 3400+/2GB RAM
2x 2,5" 60GB Sata HDD (wanted to use for Raid1 config)
2x 3,5" 1 TB Samsung Spinpoint HDD
Onboard VGA

I tried mdadm booting from a live CD, and that did the trick ! only when i rebooted the system with the Ubuntu Server 8.04.1 Disk it kindly "forgot" the complete Raid-1 array ! :(
Thanks in advance :)

---

### Post by fjgaude on 2008-10-06
If the raid1 array is assembled you can mount it, but first make a mountpoint. To auto load the array at boot time place a line in your **/etc/fstab** file:

```
sudo mkdir /home/raid
sudo mount /dev/md0 /home/raid
```

Add line at end of fstab file:

```
/dev/md0 /home/raid ext3 defaults 0 2
```

You might tell us what this shows:

```
sudo mdadm -D /dev/md0
```

I'm assuming your array name is /dev/md0. Use whatever mountpoint you wish.

To learn about software ware, some material to study:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Let us know how you are doing.

---

