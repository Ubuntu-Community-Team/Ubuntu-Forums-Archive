---
title: "Ubuntu Server Partition Scheme for owncloud"
date: 2017-06-09
forum: Server Platforms
---

### Post by bdboy on 2017-06-09
Hello Expert!
I am new ubuntu user.
I have install ubuntu server 17.04 in my 500GB HDD and the folowing partition scheme 

60 GB for Root/
28 GB for /boot
400 GB for /home 
12 GB for /swap but swap partition did not correctly cause i made the filesystem ext4 for swap. Is there any way to change the swap file system ext4 to swap?
after that i have installed the ubuntu server 17.04 .
Actually i made this server for cloud storage thats why i have installed lamp server, owncloud .
now everything configured correctly. but my question is where will be stored my owncloud user data?
i want user data will be store on 400 GB /home partition. i dont know by default where is store owncloud data. 
how to check owncloud data directory & how to select the partition 400 GB /home for owncloud user data store?

please help me :(

---

### Post by wildmanne39 on 2017-06-09
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2017-06-09
To create a swap partition run 
```
sudo mkswap device
```
where "device" is a partition like /dev/sda5.  You then need a corresponding entry in /etc/fstab
```

/dev/sdaX     none     swap     sw     0 0

```

I don't know anything about Owncloud.  Did you read the documentation?  Surely there is a directive to tell the application where the data are stored.

---

### Post by bdboy on 2017-06-09
can I reopen partition manager from command line?

---

### Post by SeijiSensei on 2017-06-11
You cannot repartition the drive that is in use.  To do that you must boot from an Ubuntu DVD image, then pick "Try Ubuntu" at the prompt.  You can than use either parted or gparted (parted plus a GUI) to repartition the drive.

---

### Post by LHammonds on 2017-06-14
The data storage for ownCloud does not "tie-in" with users defined in your operating system so no real need to associate to /home

My "data" storage is simply a folder under my owncloud web install called "data" which is in the /var volume.  This is also where most of my storage space is utilized (using LVM)

I wouldn't recommend running a server in anything other than an LTS version for stability reasons...which is currently 16.04.2 LTS

I did document [how I install a 16.04 LTS]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220") for long-term use as well as [how I install ownCloud]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=219") too in case you'd like to look it over.

**EDIT:** If you want to move the data folder around, edit owncloud/config/config.php and change the "datadirectory" variable.  However, I'd strongly recommend reading through my owncloud install thread since there are several things you should do to tighten security to reduce the risk of your personal files being compromised.

LHammonds

---

