---
title: "best backup solution for my scenario"
date: 2016-03-09
forum: Server Platforms
---

### Post by NotQuiteSU on 2016-03-09
I'm running Ubuntu Server off of a 40 GB SSD (sda), with 2 other drives for my media storage (sdb/sdc) and home directories. I've installed several applications and made some configuration changes.  I don't need to back up sdb/sdc as they're backed up to the cloud. What is the best way to backup my server/setup so I can restore in the event of a drive failure. I know with stuff like FreeNAS, it was easy to just backup the config. I know Ubuntu isn't modular like that.

Can I just make a copy of the drive somehow as an image and store it somwhere for easy restoration?

---

### Post by howefield on 2016-03-09
Thread moved to the "*Server Platforms*" forum.

---

### Post by ian-weisser on 2016-03-09
Were it me, I would simply backup the config files with my /home backup. But that is what is easiest for me.

You can indeed clone your drive as a form of backup using remastersys, if you so wish. [http://www.remastersys.org](http://www.remastersys.org)
There are a myriad of other backup/restore options.

---

### Post by ScorpioTiger on 2016-03-09
I have pretty much the same question. I'd add an extra question; how do you do the server backup when your backup is going to exceed the available disk space on the server? How can you create and encrypt an image on the fly and upload to say Amazon S3? This must be a very common requirement. A server can easily have more than 50% of it's disk space used, therefore making it impossible to create an image on the server's disk.

---

### Post by mastablasta on 2016-03-10
> **NotQuiteSU said:**
> 
Can I just make a copy of the drive somehow as an image and store it somwhere for easy restoration?

clonezilla, remastersys, redobackup, dd etc. however during cloning the server will (should) go down.

another option is to backup only config files and a few main directories. you could use some automated backup service (rsync, rdiff-backup...) for that.

> **ScorpioTiger said:**
> I have pretty much the same question. I'd add an extra question; how do you do the server backup when your backup is going to exceed the available disk space on the server? How can you create and encrypt an image on the fly and upload to say Amazon S3? This must be a very common requirement. A server can easily have more than 50% of it's disk space used, therefore making it impossible to create an image on the server's disk.


how would that be a backup? backing up to same disk. and if disk fails or is corrupted then what? all you need is config files and software that was used. easiest way is to have automatic incremental backups that get transferred to another place (cloud, external hard drive, remote storage etc).

one can also use BTRFS or ZFS4linux file system which create snapshots. this is more of a backup meant for restoring some user action. e.g. if you accidentally deleted something or to restore the OS into previous state (bad update...). they also guard against data corruption a bit, but not against disk failure (RAID is for that)

---

### Post by NotQuiteSU on 2016-03-10
> **mastablasta said:**
> clonezilla, remastersys, redobackup, dd etc. however during cloning the server will (should) go down.

another option is to backup only config files and a few main directories. you could use some automated backup service (rsync, rdiff-backup...) for that.

I'm still an amateur, what directories do I back up? It would encompass all my applications, settings, accounts, etc?

> **mastablasta said:**
> 
how would that be a backup? backing up to same disk. and if disk fails or is corrupted then what? all you need is config files and software that was used. easiest way is to have automatic incremental backups that get transferred to another place (cloud, external hard drive, remote storage etc).

one can also use BTRFS or ZFS4linux file system which create snapshots. this is more of a backup meant for restoring some user action. e.g. if you accidentally deleted something or to restore the OS into previous state (bad update...). they also guard against data corruption a bit, but not against disk failure (RAID is for that)

As I mentioned, my core OS is on a 40 GB drive. My home, data, etc, are on additional drives.  I don't mind taking an imagine, (offline or not) and saving that somewhere that would be stored. Just a matter of the best tool. I'm familiar with Windows. If drive space is unused, then it isn't captured in an image. Would it be the same in Linux?

---

### Post by ScorpioTiger on 2016-03-15
I'm seeing a lot of talk, but not a single concise answer to the question at hand; "Can I just make a copy of the drive somehow as an image and store it somwhere for easy restoration?"

I wasn't suggesting backing up to the same volume, but merely pointing that you can't just create an image on the same volume and then upload that elsewhere when you have less than 50% disk available. It seems to me that there must be a way of encapuslating everything on the server, encrypting it, and uploading to a backup target on the fly.

I can't believe that there isn't a way to do this.

I currently have database and file backups for critical applications, but in a DR scenario where the server is unrecoverable, the time to build a new server; reinstall and configure everything before doing database and file restores is a problem. Taking an image of the server once and then doing regular database and file backups makes recovery much faster and less error prone.

---

### Post by wellsilva-email on 2016-03-15
> **NotQuiteSU said:**
> I'm running Ubuntu Server off of a 40 GB SSD (sda), with 2 other drives for my media storage (sdb/sdc) and home directories. I've installed several applications and made some configuration changes.  I don't need to back up sdb/sdc as they're backed up to the cloud. What is the best way to backup my server/setup so I can restore in the event of a drive failure. I know with stuff like FreeNAS, it was easy to just backup the config. I know Ubuntu isn't modular like that.

Can I just make a copy of the drive somehow as an image and store it somwhere for easy restoration?

Hi NoteQuiteSU!

There's this tool called [mondo rescue]("http://www.mondorescue.org/") that creates images of your you operating system as it is right now. Some things that I find important to keep in mind:

1 - You have to have an image that you know to work (golden image). Sometimes the process might not go as expected, you will have a image that doesn't install. You will still have files inside there to restore, so if you have one that works, you can use the other to get the different files.

2 - By default, it will backup the entire system so make sure to configure to backup only your OS, so add the pertinent config to ignore database files. Some log files might make your image unecessarily big as well.

I found this [ubuntu guide for mondo]("https://help.ubuntu.com/community/MondoMindi#For_Trusty_.28Ubuntu_14.04_LTS.29") and this [other that talks about Centos as well]("http://www.tecmint.com/how-to-clone-linux-systems/").

Hope to have helped. Let us know if it solved your issue or if you need any more clarification.

---

### Post by ian-weisser on 2016-03-15
> **ScorpioTiger said:**
> I'm seeing a lot of talk, but not a single concise answer to the question at hand; "Can I just make a copy of the drive somehow as an image and store it somwhere for easy restoration?"
I see one (very good) concise answer at the beginning of Post #5.


> **ScorpioTiger said:**
> you can't just create an image on the same volume and then upload that elsewhere when you have less than 50% disk available. It seems to me that there must be a way of encapuslating everything on the server, encrypting it, and uploading to a backup target on the fly.
Creating and storing images requires plenty of storage capacity. No way to 'just' around it.
Either add more local storage and build your image locally, or backup across the network to a remote machine with adequate storage and build your image there.
You get to choose the complexity you wish to maintain.

---

### Post by mastablasta on 2016-03-16
> **NotQuiteSU said:**
> I'm still an amateur, what directories do I back up? It would encompass all my applications, settings, accounts, etc?

it depends what you want. some would do:
/usr
/home
/var
/etc
/root

some would do:
/etc, /opt, /var, /home

depends on restore methods. some would backup only data and program's list so they can reinstall. maybe some config file and that is it.
> 
As I mentioned, my core OS is on a 40 GB drive. My home, data, etc, are on additional drives.  I don't mind taking an imagine, (offline or not) and saving that somewhere that would be stored. Just a matter of the best tool. I'm familiar with Windows. If drive space is unused, then it isn't captured in an image. Would it be the same in Linux?

if you don't mind taking an image (you will need to remember to take it) then Redo backup has a nice GUI and is very easy to use. under the gui same program does the cloneing as in clonezilla.  clonezilla more up to date and is also a bit more complicated (bad GUI in my opinion) but they have good step by step guides. free space is compressed and basically doesn't exist. image is an image and these programs work for taking windows images as well as image of other OS. they would do a bit by bit copy of the disk and then compress it.

image also means that any data corruption is imaged. for example I had a system image done from my server when I set it up. through about 4, 5 months I added a few things, changed some config files, removed some things, so I though it would be a good idea to create another image. and so I then did another one. 2 months after I did another one and just a couple of weeks after that server started to behave strangely. on closer inspection I found out that the USB stick with the OS started to fail. no problem I thought I have a recent image. got a new USB stick and started with restoring. most data was corrupted on the image. so I thought I have a 2 months image and all I did was updates. easy enough. I started to restore that one. turns out it was also corrupted (though less, so I was able to save some things from it). moral of this story - if disk has corrupted data, image will also have corrupted data. and also having more images than a couple is a good idea :)

---

