---
title: "Backing up server before updating"
date: 2010-02-27
forum: Server Platforms
---

### Post by gyzer on 2010-02-27
I've been running my little server at home for a few months now, and I've noticed that Webmin has detected that I'm in need of over 100 updates. I'm a bit scared to run the updates because everything is working just fine right now, but a part of me still wants to run some of the updates.

Now I know backing up the server would be a good idea to do before this happens. This server is a media server with videos, music and pictures taking up the majority of the hard drive space on the server. I just have one partition on the server, outside of the swap partition. I would like to back up everything on the server except the videos, music, and pictures, because if even an update messes with the server, I could always retrieve those, and the external hard drive I'm going to back up to wont be big enough to hold everything anyways.

My main question is, if I were to backup up everything except for those directories that hold my videos, music, and pictures, and something were to go wrong, if I were to restore all of those, would I then be back to the state my system was at when I backed up? I've never done a back up and restore in a linux environment before. I just want to make sure that just doing that will be enough, because the last thing I want to do is hose my server after taking several weeks to get it to the working state that its at.

---

### Post by jfparis on 2010-02-27
You might want to look at rsync to do your backup. It has an exclude option which should be ok to do what you want to do 

```
rsync -az --progress --exclude=pictures/ --exclude=music/  /path/to/source/ /path/to/dest/
```jf

---

### Post by NullHead on 2010-02-27
Honestly, if it were mine, I would make an image of the whole hard drive and burn it onto DVDs for record keeping sake. I would use either clonezilla or partimage. 

I don't think you'll have an issue updating though. As long as you've got an ubuntu disk, you can most likely go back and fix or backup anything that might have gone wrong after the update.

---

### Post by gyzer on 2010-02-27
I've used clonezilla before and partimage. I like clonezilla alot more though.

I thought about doing an image, but I would want to exclude the videos, music, and pictures which are all on the same partition as the rest of the system. Are there some features of clonzilla that might be able to help with this?

So the os will have no problems with me copying files that are currently being used? Also if I copy all the needed directories in / and restore them later and restart the system I will have no problems? I'm just used to doing backups and restores in a windows environment, not a linux environment.

Thanks for the quick responses!!

---

### Post by NullHead on 2010-02-27
I don't really have experience with this type of backup, I can't say for sure, but I would think that critical files being used wouldn't be copied with the system running. You might need to boot a live cd and mount the hdd before you can copy the files.

---

### Post by gyzer on 2010-02-27
Yeah, that's what I figured.

---

### Post by gyzer on 2010-02-27
Actually, after reading an old post on these forums, it seems like you can just do a tarball, and that all files specified in the tarball will be copied over to the back up media, regardless of whether or not they are being used.

---

### Post by HermanAB on 2010-02-28
I would make tar balls of the data and of the /etc directory.  

Tar will save files that are open.  However, a file that is actively being written to while the tar ball is being made, will result in a corrupted tar ball.  For that reason, you need to use an export mechanism for active databases e.g. mysqldump, before making a tar of the dump.

---

### Post by ezacon on 2010-02-28
I have done this to convert my system disk from LVM to normal partitions.
Boot from live CD using same technology (1386, amd64...)
Configure your destination drive partitions and mount source and destination and then copy each partition with rsync:
```

rsync -av /mnt/src/ /mnt/dest/

```
This will copy your whole system and maintain permissions, owner an links.
Install grub2 on destination drive using this document:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
Use third method (using chroot).

I have tested this with Ubuntu server 9.10 and workstation
Next time, rsync will just trasfer the diferences and you have an updated backup disk in a few minutes.

---

### Post by spikyjt on 2010-02-28
If your system is so important to you that you are scared of running updates in case something breaks, you should be backing it up regularly anyway. What happens if your hard disk(s) die(s)? I've found that to be the most common hardware failure after power supplies. I use dirvish to backup my servers. It is in the repos and very easy to setup if you are just a little bit comfortable with the command line. It is very efficient and most importantly it is focussed on providing good archives to restore from, rather than just well compressed backups. It also does incremental backups, so if you update and something is borked, you can just restore the previous day's (or hour's!) backup and you're back where you were. The archives just appear as file trees, just like the real disk. I've been using it for years and am very comfortable with it, so happy to answer dirvish specific questions if anyone's interested.

---

### Post by gyzer on 2010-02-28
I am running a software linx RAID 1, so I'm covered when it comes to hard drive malfunctions. I'm getting a little confused and overwhelmed now with all of these options. I'm just looking for something that will copy my system with being able to do exclusions just in case if updates bork my system.

Will rsync be able to copy over all system files even if they are currently being used or written to?

---

### Post by gyzer on 2010-03-01
Ok, heres the deal. I'm used to running backups in a Windows environment with being able to select system files and run a backup using Volume Shadow Copy. Now here in a linux environment, this is very different.

I've been doing alot of searching on the net to see what all the options are out there for backing up a linux system. I've made images plenty of times using partimage and clonezilla. Now those would work for me except I've got files on the same partition that I don't want to be apart of the image. 

Does anyone have any idea on how to accomplish this?

---

