---
title: "Image of an Encrypted Drive"
date: 2008-06-17
forum: Security
---

### Post by Tubes6al4v on 2008-06-17
Hello all,

Some faulty work on my original Hardy install presented me with the opportunity to reinstall with full system encryption. I am always a fan of protecting my privacy. However, I am still learning about Linux, and am very much enjoying exploring all of the amazing tasks I can do with it!

Onto the questions:

What is a good backup plan?

Can I create an exact drive image of my drive as it is now (I have configured all of the basics for hardware and whatnot, so I would like to just be able to go back to this if things get really hairy)? Mondo/Mindi, and Partimage do not say they cover encryption.


Any other suggestions are obviously welcome.

---

### Post by hyper_ch on 2008-06-18
I backup the individual files in another fully encrypted drive... so I make 4 backups a day using the power of rsync, ssh, hardlinks back for 90 days.

---

### Post by Tubes6al4v on 2008-06-18
> **hyper_ch said:**
> I backup the individual files in another fully encrypted drive... so I make 4 backups a day using the power of rsync, ssh, hardlinks back for 90 days.

Thanks for the advice. But my concern with using these is whether I can step back if (heaven forbid), my GRUB gets screwy. Would using rsync, ssh, and hardlinks be more adviseable than turning my second drive (currently running Vista Ultimate) into a RAID?

---

### Post by hyper_ch on 2008-06-18
you should have a backup at some remote place... imagine someone steals your computer or there's a fire in your apartement/house..... then all data is gone... that's why I also have a small box at my parents' home... also fully encrypted and make once a day backups there...

hardlinks are used to make snapshot-style backups that don't use too much space ;)

---

### Post by Tubes6al4v on 2008-06-18
I attempted to use Mondo to create a bootable recovery disk. It burned fine (though it seems to get caught in a loop of asking to burn the same disk over and over). Booting it up and running the compare app had some issues (since Mondo could not access my encrypted drive). No big deal I thought, and rebooted, well, now kernel 19 would not work. I just reinstalled it, and will reboot. Wish me luck

it looks like I will just be skipping the Bootable DVD and just go with the Tar/rsync method.

---

### Post by Tubes6al4v on 2008-06-18
Woa, so first the Kernel, then the restricted drivers, and finally Tor needed to be reinstalled. I think that got me back up though. Ok, so it was likely the Encrypted drive that is incompatible with Mondo/Mindi (though I am running 64 bit as well).


Any other suggestions?

---

### Post by Biochem on 2008-06-19
how about 
```
dd if=/dev/sdx | gzip >> /some/backup/path.imj.gz
```

This will create a compressed image of your encrypted drive. Then to restore

```
gunzip --stdout /some/backup/path.imj.gz | dd of=/dev/sdx
```

---

### Post by hyper_ch on 2008-06-20
should work.... however that just requires an awful lot of backup space... especially if you want to have more than one backup.

---

### Post by Biochem on 2008-06-21
> **hyper_ch said:**
> should work.... however that just requires an awful lot of backup space... especially if you want to have more than one backup.

Yes it does. But it is the safest way to make sure you have the luks/dm-crypt sectors backed up and all those little config files other backup scheme usually forget. You don't need many of those.

Beside you usually do disk images from a live cd  so it is not very convenient. For daily /home backup a good old tar piped trough gpg is more than adequate. but that is another mater since the OP asked

> Can I create an exact drive image of my drive as it is now

Personnally I have one dd image and a daily incremental weekly tower of Hanoï (5 folder) tar backup of /home/me.

If I screw up badly I can rapidly redeploy do the original state by restoring the dd image then the latest tar.

---

### Post by hyper_ch on 2008-06-21
but is there a reason you need to backup the drive as it is and not only the files within?

---

### Post by Tubes6al4v on 2008-06-21
Firstly, thanks for the help guys. I have been taring up my main files, and it seems to be working quite well.

I want to have a copy of my drive so that if it gets really hairy (I have a track record of making them so), I can just revert to my drive in a good configuration state.


Biochem, thank you for the suggestion, I will definitly give that a shot. Is GunZip the best safe compression platform for archiving the files?

---

### Post by Tubes6al4v on 2008-06-23
> **Biochem said:**
> how about 
```
dd if=/dev/sdx | gzip >> /some/backup/path.imj.gz
```

This will create a compressed image of your encrypted drive. Then to restore

```
gunzip --stdout /some/backup/path.imj.gz | dd of=/dev/sdx
```

Hmm, when I try to do this (changing sdx to sda, and /some/backup/path.imj.gz to /******/Downloads/backup.imj.gz), I get the response that there is "No such file or directory"

Any suggestions?

---

### Post by Biochem on 2008-06-24
@ Tubes6al4v:
 First I think Bzip2 is a safer compression algorithm for large file as it support some level of fixing. Though I've never tried them so I can't comment on their efficiency and ease of use. However bzip2 is slower. 

It is also good to mention that compressing such big files are always at risk of corruption and if their is too much of those the whole file will be lost. To the best of my knowledge, thats is true for all solutions available at the moment.

Also, Don't expect much if your compressing an encrypted drive. Since from the outside it looks like random data, it is not very compressible. If you have a 10% compression it is very good. There are ways to optimize the compression on non-encrypted drive though (or the /dev/mapper/decrypted volume).

As for your problem, it is hard to tell without the actual input of the console.

- Are you sure you have entered the right command:
```
dd if=/dev/sda | bzip2 --stdout >> /******/Downloads/backup.imj.bz2
```

Edit: reading my post I think it's because I forgot to write the --stdout argument. So gzip was trying to compress your not yet existant backup, Sorry.

- Make sure you are doing it from a live cd. If you write on the drive you are imaging it will most probably create an error.

- Obviously don't put the backup file on the drive being imaged. You will end up in a never ending loop.

@ hyper_ch:
There may be many reason why you want to image the drive istead of backing up indivdual file.
* Preservation of MBR
* Preservation of dm-crypt informations (Though I think with a little reading I could manage to be more selective)
* Complete backup of dual-boot or windows partition
* Create a restoration disk of Windows for Warranty purposes before formating to linux

Restoring an image is also often faster and simpler then recostumizing everything after a crash. Of course you could reinstall, with a fresh encrypted drive, than restore the file backup. But as long as I have enough backup space, I think a full image is better suited.

As I previously said there are ways to compress the image a lot if they are in clear by zeroing all un-used sector. My fresh install Windows dd image thake 3.3 GB from 160 GB drive. I probably can't a a smaller file.

---

### Post by hyper_ch on 2008-06-24
but how much space do you need to keep up full backups back for 90 days with 4 images a day? ;)

---

### Post by Biochem on 2008-06-24
Well, first, I don't backup that often!!!

Second, I never said it was for everyday use.

Finally, I never said it was for everyone.

But for arguments sakes...

suppose a 100 GB drive.

~12GB for the encrypted system images (10GB root + 2GB swap). The rest depends on how much stuff is on the separate encrypted /home which is incrementally backup at the files level.

OR 

~100GB for the first image. then the other backup are at the file level using the tool of your choice.

The image is just a quick restore point, not a full blown backup solution. Do you rsync your whole system (rsync / user@server:backup/) 4 times a day? If you do you are way more paranoid than me.

---

### Post by hyper_ch on 2008-06-24
Yes, I rsync ;) well, I just like to have backups (after one of my harddisk failed one day and after I accidentally formatted the wrong one....)

I don't rsync the whole file system, just /home /root /etc and a couple of folder in /var and my /mybu (mysql dbs get dumped in there)

---

