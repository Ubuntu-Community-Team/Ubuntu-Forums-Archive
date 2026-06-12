---
title: "2x Ubuntu on VMware, access disk drive"
date: 2011-01-10
forum: Server Platforms
---

### Post by JBtje on 2011-01-10
Greetingz,
 
I'm the proud owner of a new 1U server, thought dont really know how to handle the next problem.
The server runs VMWare ESXi 4.x and currently contains two virtual machines with Ubuntu server 10.04 installed on them. Both the virual machines have 50GB of Harddrive, thought one had another 1TB to use.
 
One of these virtual machines is going to be a fileserver (and has the 1TB for that reason) while the other machine is purely going to be used as webserver.
The system uses one harddiskdrive of 1.5TB (hardware raid 1 configured)
 
The fileserver will contain images, which should be shown on the webserver. Therefor I need to setup a link between the images directory on the fileserver, so it can be accessed by the webserver. Now this is one and the same harddisk, but the partition is only availeble in the fileserver.
 
How can i configure this directory, so it can be accessed by the webserver automatically (e.g. that I dont have to remount the directory, after the fileserver has been down for whatever reason)
 
My best regards,
Jeffrey
 
p.s. I'm pretty much new to Ubuntu.... :o

---

### Post by arrrghhh on 2011-01-10
I'd recommend using NFS, unless there's some other method that I'm not aware of.

NFS is a very standard protocol, that I always recommend the use of between linux client/servers.

[NFS HowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by CharlesA on 2011-01-10
+1 to NFS.

You can use Samba too, but NFS would do want you want and is easier to setup then Samba.

---

### Post by JBtje on 2011-01-10
> **arrrghhh said:**
> I'd recommend using NFS, unless there's some other method that I'm not aware of.
 
NFS is a very standard protocol, that I always recommend the use of between linux client/servers.
 
[NFS HowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
 
Also, please don't post [duplicate threads]("http://ubuntuforums.org/showthread.php?t=1664168") asking the same question. I'm sure you just did something innocent like hit submit twice... Just try to avoid it in the future ;)
 
Thank you for the quick reply!
read food, time to consume some :D
 
Well.. I waited about 15 minutes b4 i pressed the "submit" button again... for some reason it acted lik it didn't do anything, while secretly it already posted my question the first time :S Also I dont see any option to delete a threath, right?
 
JB

---

### Post by arrrghhh on 2011-01-10
> **JBtje said:**
> Thank you for the quick reply!
read food, time to consume some :D
 
Well.. I waited about 15 minutes b4 i pressed the "submit" button again... for some reason it acted lik it didn't do anything, while secretly it already posted my question the first time :S Also I dont see any option to delete a threath, right?
 
JB

I think one of our kind moderators (thanks CharlesA :D) already cleaned up the other thread for you ;).

No worries on the dupe, it happens.  I've definitely done it before, exact same thing - hitting the submit button seems to do nothing, when the thread has in fact been submitted!

At any rate, let us know if you have problems with the NFS setup.  Like Charles said, much easier than samba - and if you're not using it to share files with any Windows machines, there's no need to mess with samba at all!

Heck, I prefer NFS so much, that I run both on my server - so I can do NFS with linux clients, and samba with win clients ;).

---

### Post by CharlesA on 2011-01-10
No worries. The forum has been acting funky lately.

---

### Post by JBtje on 2011-01-10
> **arrrghhh said:**
> Heck, I prefer NFS so much, that I run both on my server - so I can do NFS with linux clients, and samba with win clients ;).
Hehehe, thats what I shall do too. Since u guys tell me its way easier to use NFT i can use that to setup the webserver quickly, and go mess around with samba after that.
 
So far I have only worked with same through webmin(which I hate btw). Just wondering, is there some gui to controll samba users? perhaps even via an web interface (beside webmin) ?
 
Best regards,
Jeffrey

---

### Post by CharlesA on 2011-01-10
You can use webmin to set up samba users. I just use the terminal for that tho.

---

### Post by JBtje on 2011-01-10
> **CharlesA said:**
> You can use webmin to set up samba users. I just use the terminal for that tho.
I should read my posts b4 I press the submit button :|
I do love directadmin (and i dont even think it works with samba?) but I do hate webmin. This because I entirely miss the overfieuw with it :(
 
Are there other interfaces like webmin, but with a better overfiew of who having what access?
 
Best regards,
Jeffrey

---

### Post by CharlesA on 2011-01-10
I don't know, I used to use Webmin, but not anymore. There might be other frontends that can do what you want.

I know swat can do some things, but you need to run it as root and it's a graphical app.

---

### Post by Vegan on 2011-01-10
webmin is fine for most functions, although I still use the terminal for many things.

---

### Post by JBtje on 2011-01-13
ok, so while trying to get this working, I already got stuck on the most basic thing you can think of: Partitioning an harddisk :|
 
I have no clue what the best harddiskformat would be for the samba file disk (and with that, the disk that needs to get linked to the other system)
 
I'm not going to use this disk on a windows machine, so unless NTFS gives more preformance, I dont think that will be the type I'm looking for... but what type should I format the disk to?
 
its 1 TB of size, will never be attached to a windows machine. so ext2, 3, 4? fat?
 
Best regards,
Jeffre

---

### Post by CharlesA on 2011-01-13
I use ext4 for my data drives, but file system really doesn't matter. However, you'll want something with journaling (ext3 or ext4)

---

### Post by JBtje on 2011-01-13
well... even b4 I could do something I run into the next problem :(
 
I have a 1 TB harddisk
During the installation of Ubuntu, I told him to use 50GB for the partiotion to install Ubuntu on, so the rest should be unallocated.
 
System Monitor tells me there are two File Systems:
/dev/mapper/name-root....ext4..........44.5GiB
/dev/sda1.........................ext2..........227.7Mib
 
which is as I wanted.
 
Gparted tells me that:
Unallocated: 1.00 MiB
/dev/sda1.............ext2........../boot.........243.00MiB
/dev/sda2.............extended....................999.76 GiB
........../dev/sda5...lvm2..........................999.76 MiB
 
 
and sda5 gives me a warning: Logical Volume Management is not yet supported.
 
After searching the internet, I still have no idea why Gparted tells me this "extended" sda5 partition is 1TB of size, while I have made it only 50GiB.... Nor can i figure out why LVM isn't supported, since LVM2 is installed
 
Thank you for the help!
Jeffrey

---

### Post by CharlesA on 2011-01-13
Ah. You are using LVM. I think that's the default for Ubuntu server, but I don't use it.

Maybe this will help: [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by JBtje on 2011-01-13
thankx!
 
so.. is it correct to say that LVM subpartitionise the partition? And ifso, I guess there will be two partition tables, and therefor a higher risk on losing one of them and making the partition corrupt?
 
Best regards,
Jeffrey

---

### Post by CharlesA on 2011-01-13
I don't know. I just know that I've had problems with LVM when cloning disks, so I don't use it.

The general rule of thumb when dealing with partitions is to always make a backup before doing anything.

One problem and you've lost data.

---

