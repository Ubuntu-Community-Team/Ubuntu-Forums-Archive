---
title: "how to add 2nd HD to my server?"
date: 2010-12-09
forum: Server Platforms
---

### Post by Bushcraft Bill on 2010-12-09
I have one 80 gig HD and have installed a 40 gig HD to my server computer the 40 gig drive has old windows on it, I want to format it for the server and have it as a partition.. in the end I want to use clonezilla to backup the main HD to the 2nd HD if that is possible or should I forget about that and set it up as a raid drive <- that is a backup of the first HD right?

yes I am kind of new to all this so need detailed info on how to do this!
love having the server now I don't want to loose what I have setup so reason to backup now....running 10.04 and I am using putty to access server...

Bill

---

### Post by James78 on 2010-12-09
> **Bushcraft Bill said:**
> I have one 80 gig HD and have installed a 40 gig HD to my server computer the 40 gig drive has old windows on it, I want to format it for the server and have it as a partition.. **in the end I want to use clonezilla to backup the main HD to the 2nd HD if that is possible** or should I forget about that and **set it up as a raid drive <- that is a backup of the first HD right?**

yes I am kind of new to all this so need detailed info on how to do this!
love having the server now I don't want to loose what I have setup so reason to backup now....running 10.04 and I am using putty to access server...

Bill
1. Ya, it's possible, it's a good idea (bad idea if you want to protect against drive crashes), because the backup would be static, and your server is ever changing (if you mess something up, you still have the backup). (See below points)
2. Ya, it's a "backup", if you set it up on RAID1, but this generally only protects you against hard drive failure type of data loss. (See below points)

Some things to consider..
If 1 hard drive fails and you have a RAID1, you haven't lost your data (it's mirrored on the other drive).
If you mess up your OS by any means whatsoever, delete files, change permissions that shouldn't be changed, etc, that WILL BE mirrored on the other drive, so you can't go to the other drive and expect it to be a backup from 5 minutes ago, before you wrecked something.

Now, if you have a backup, because it's static, if you mess anything up in the OS, delete something, it'll still be there, it may be a little old, or new, but it's there nonetheless.
However, if your OS's hard drive fails, there goes 100% of your data.

Considering these things, it's best to do a RAID1 to mirror your drives, and it's a good idea to periodically (via automated tasks) backup your important files (apache configuration, website data, BIND configuration ..)

My personal configuration is. I have periodic backups of important information going to /var/backups, and I have a RAID5 across 3 drives. Now, because the data is striped, if a drive fails you've lost all your data, but because RAID5 uses parity striping too, you actually would loose nothing if 1 drive fails (I've started up from 2 drives, which is a degraded array, even though the 3rd drives data was completely lost, wrecking the stripes)

---

### Post by Bushcraft Bill on 2010-12-09
> **James78 said:**
> 1. Ya, it's possible, it's a good idea (bad idea if you want to protect against drive crashes), because the backup would be static, and your server is ever changing (if you mess something up, you still have the backup). (See below points)
2. Ya, it's a "backup", if you set it up on RAID1, but this generally only protects you against hard drive failure type of data loss. (See below points)

Some things to consider..
If 1 hard drive fails and you have a RAID1, you haven't lost your data (it's mirrored on the other drive).
If you mess up your OS by any means whatsoever, delete files, change permissions that shouldn't be changed, etc, that WILL BE mirrored on the other drive, so you can't go to the other drive and expect it to be a backup from 5 minutes ago, before you wrecked something.

Now, if you have a backup, because it's static, if you mess anything up in the OS, delete something, it'll still be there, it may be a little old, or new, but it's there nonetheless.
However, if your OS's hard drive fails, there goes 100% of your data.

Considering these things, it's best to do a RAID1 to mirror your drives, and it's a good idea to periodically (via automated tasks) backup your important files (apache configuration, website data, BIND configuration ..)

My personal configuration is. I have periodic backups of important information going to /var/backups, and I have a RAID5 across 3 drives. Now, because the data is striped, if a drive fails you've lost all your data, but because RAID5 uses parity striping too, you actually would loose nothing if 1 drive fails (I've started up from 2 drives, which is a degraded array, even though the 3rd drives data was completely lost, wrecking the stripes)

OK thanks...forget the raid thing..what I want to do is format the 2nd drive as a partion then first off how do I do it?

I found this on how to backup: [http://ubuntuforums.org/showthread.php?t=35087&highlight=add+drive+server](http://ubuntuforums.org/showthread.php?t=35087&highlight=add+drive+server)


Bill

---

### Post by James78 on 2010-12-09
What I'd actually suggest is doing a RAID with automated backups. That way you have backups of the data you need, and if 1 hard drive fails you haven't lost anything. If only 1 drive being used, that's a 100% risk of loosing your data if the drive goes bad.

What you could do is partition your 2nd drive into 2 parts. The first partition could be the RAID1 mirror, and the 2nd you could do periodic system backups too.

Using rsync (link provided), you could auto mount the backup partition at runtime via /etc/fstab, and then write a cronjob to call rsync to send the backup data to your mounted backup disk.

And regarding your link. I've done that before, it takes a really long time, and if you don't exclude all the correct directories (/var/run being one of them, and there's a lot more), your archive could become totally useless, then when you need it, you'd find out it's no good. It's probably best to just periodically backup the crucial parts of your information to your backup drive, and do the RAID1 in case of drive failure. It's ok to replace an OS, but important information is irreplaceable.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Bushcraft Bill on 2010-12-09
> **James78 said:**
> What I'd actually suggest is doing a RAID with automated backups. That way you have backups of the data you need, and if 1 hard drive fails you haven't lost anything. If only 1 drive being used, that's a 100% risk of loosing your data if the drive goes bad.

What you could do is partition your 2nd drive into 2 parts. The first partition could be the RAID1 mirror, and the 2nd you could do periodic system backups too.

Using rsync (link provided), you could auto mount the backup partition at runtime via /etc/fstab, and then write a cronjob to call rsync to send the backup data to your mounted backup disk.

And regarding your link. I've done that before, it takes a really long time, and if you don't exclude all the correct directories (/var/run being one of them, and there's a lot more), your archive could become totally useless, then when you need it, you'd find out it's no good. It's probably best to just periodically backup the crucial parts of your information to your backup drive, and do the RAID1 in case of drive failure. It's ok to replace an OS, but important information is irreplaceable.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

OK I can go for doing both the raid and then the partion also for backup I would like having those options thanks..

thanks for the help I have been through all 10 pages on the server forum now with no info found for doing this so this could be good help post in the future for others...

so were do I/we start then?

---

### Post by James78 on 2010-12-09
I forgot to say. It's a good idea to also do your backups to the same drive. That'd be fairly easy, as all you need to do is another cron to copy and tar the files to /var/backups, that way your other drive isn't the only backup you have.

Where do you start? Well, [this]("https://help.ubuntu.com/community/Installation/SoftwareRAID#Configuring the RAID") guide on software RAID mentions how to do it, however it only shows how to do it while installing the OS. So [this]("http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server") other one might also come in handy, which claims to show how to install RAID on a server already installed. I skimmed over it really quickly, but it appears to have some good information.

Hopefully that helps you out.

---

### Post by Bushcraft Bill on 2010-12-09
OK I got this far and have no clue what so ever LOL...

 '''cat /proc/diskstats'''

cant imbed screen shot into forum how sad..had to put pic on server

[IMG]http://192.168.0.103/survival/stuff/1.jpg[/IMG]

 - (I could not do copy past from putty?)<-do you know how to do?

---

### Post by James78 on 2010-12-09
When you execute commands he has listed, just strip the '''

So
```
'''cat /proc/diskstats'''
```
Is really
```
cat /proc/diskstats
```

---

### Post by Bushcraft Bill on 2010-12-09
> **James78 said:**
> When you execute commands he has listed, just strip the '''

So
```
'''cat /proc/diskstats'''
```
Is really
```
cat /proc/diskstats
```

ya figured that out already but cant get things working with those help files... some of the commands just did not work...

I even played around in webmin but that did not get me any were ether...

---

