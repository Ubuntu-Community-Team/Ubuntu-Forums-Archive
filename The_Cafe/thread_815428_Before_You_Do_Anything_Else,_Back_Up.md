---
title: "Before You Do Anything Else, Back Up"
date: 2008-06-01
forum: The Cafe
---

### Post by starcannon on 2008-06-01
Before you ever consider installing another Operating System, whether it be Linux, another version of Windows, a Hackintosh:

***[SIZE="4"]BACKUP ALL OF YOUR IMPORTANT DATA![/SIZE]***

I've read too many heartbreaking posts of someone messing up a partition, generally a windows partition, that contains important data. This problem does not have to exist, it is insanity to mess with your hard drive partitions before you back up your important data.

So here is how you go about messing with your hard disk drive:
[LIST=1]
[*]Back Up everything that may now or in the future be of importance to you.
[*]Leave the restore partition alone, just don't mess with it.
[*]Double Check that your data is backed up, be sure its readable from another computer somewhere in the house or at work or where ever you have to go to check that the data is truly there and faithfully represented.
[*]Be prepared to start over from scratch, you may mess up and have to do a complete full reinstall of windows. You'll be glad you didn't mess with the restore partition if you decide to put it back to OEM
[*]If and only if you are certain that you backed up everything of importance to you, then proceed to move forward with your new Operating System Install.
[/LIST]

If your new to Linux, or Operating System Installs in general, you will find that sanity will thrive in this method. If you've never partitioned, or resized partitions, or messed with the mbr or grub, then I can almost guarantee your going to foul it up at least once while your in the learning process. While this can be frustrating if your trying to learn it fast, it can be devastating if you did not back up mission critical data, family photo's and movies, mp3 collections, or whatever else you have of importance on your hard disk drive. Recovering lost data is possible, but it can be VERY time consuming, it can lead to only partial results, and it can lead to a life time of misery and binge drinking.

If you have read this post, you have been sufficiently warned that not backing up your data may lead to trauma of biblical proportions.

---

### Post by Morty007 on 2008-06-07
Very valuable advice. What software do you recommend to backup ubuntu?

---

### Post by beercz on 2008-06-07
> **Morty007 said:**
> Very valuable advice. What software do you recommend to backup ubuntu?
[http://rsnapshot.org/](http://rsnapshot.org/)

I backup daily on a regular basis to another machine.  I have it automated, and write the backup operations to log files.  I don't have to worry about it.

Been doing this for year and never lost anything.  Even had to restore data "in anger" with no problems.

As someone once said to me:

> Back up or f**k up!

---

### Post by zmjjmz on 2008-06-07
And if you don't have another machine/hard drive etc., just use box.net or xs.to or filefront or whatever.

---

### Post by nick09 on 2008-06-07
> **zmjjmz said:**
> And if you don't have another machine/hard drive etc., just use box.net or xs.to or filefront or whatever.

Online severs are not an option, they can break, webpages changed, etc...

Just grab a External HDD that is your size of your HDD or more.

---

### Post by zmjjmz on 2008-06-07
> **nick09 said:**
> Online severs are not an option, they can break, webpages changed, etc...

Just grab a External HDD that is your size of your HDD or more.
Or dropbox.com
And what's to say that they break like that?
I mean, I read the story about lotsa servers dying a lot in datacenters, but they create backups every day too.
And a dedicated site isn't likely to change webpages around randomly.

---

### Post by Morty007 on 2008-06-08
I heard of one called Easy Backup. Is that ok to use?

---

### Post by Polygon on 2008-06-09
do you mean simple backup?

and personally i use rdiff-backup. Im still waiting for a good GUI program to hand backups though. Simple  backup and the other ones ive tried have various problems.....

---

### Post by starcannon on 2008-06-09
Theres always the drag-n-drop method as well.

---

### Post by gameryoshi600 on 2008-06-09
> **starcannon said:**
> Before you ever consider installing another Operating System, whether it be Linux, another version of Windows, a Hackintosh:

***[SIZE="4"]BACKUP ALL OF YOUR IMPORTANT DATA![/SIZE]***

I've read too many heartbreaking posts of someone messing up a partition, generally a windows partition, that contains important data. This problem does not have to exist, it is insanity to mess with your hard drive partitions before you back up your important data.

So here is how you go about messing with your hard disk drive:
[LIST=1]
[*]Back Up everything that may now or in the future be of importance to you.
[*]Leave the restore partition alone, just don't mess with it.
[*]Double Check that your data is backed up, be sure its readable from another computer somewhere in the house or at work or where ever you have to go to check that the data is truly there and faithfully represented.
[*]Be prepared to start over from scratch, you may mess up and have to do a complete full reinstall of windows. You'll be glad you didn't mess with the restore partition if you decide to put it back to OEM
[*]If and only if you are certain that you backed up everything of importance to you, then proceed to move forward with your new Operating System Install.
[/LIST]

If your new to Linux, or Operating System Installs in general, you will find that sanity will thrive in this method. If you've never partitioned, or resized partitions, or messed with the mbr or grub, then I can almost guarantee your going to foul it up at least once while your in the learning process. While this can be frustrating if your trying to learn it fast, it can be devastating if you did not back up mission critical data, family photo's and movies, mp3 collections, or whatever else you have of importance on your hard disk drive. Recovering lost data is possible, but it can be VERY time consuming, it can lead to only partial results, and it can lead to a life time of misery and binge drinking.

If you have read this post, you have been sufficiently warned that not backing up your data may lead to trauma of biblical proportions.

+1

I always back up my data every month :KS

---

### Post by Morty007 on 2008-07-04
> **beercz said:**
> [http://rsnapshot.org/](http://rsnapshot.org/)

I backup daily on a regular basis to another machine.  I have it automated, and write the backup operations to log files.  I don't have to worry about it.

Been doing this for year and never lost anything.  Even had to restore data "in anger" with no problems.

As someone once said to me:

I'm trying to install rsnapshot but as a noob I'm not sure how to extract it.

---

### Post by macogw on 2008-07-04
> **Morty007 said:**
> Very valuable advice. What software do you recommend to backup ubuntu?

rsync -av /home/morty/ /mnt/backup/

Replace /home/morty with your actual home drive and /mnt/backup with wherever you mount your backup drive.

---

### Post by Morty007 on 2008-07-04
Thanks Macogw. Do you know of any GUI based backup software. I just heard about Unison and linbaku.

---

### Post by macogw on 2008-07-04
> **Morty007 said:**
> Thanks Macogw. Do you know of any GUI based backup software. I just heard about Unison and linbaku.

NP, but I can't help on GUI stuff.  I've never really looked for one.  Someone was working on a Linux version of Time Machine, I think, though...

---

### Post by Redrazor39 on 2008-07-04
I suggest using a well written and screenshotted guide. That's what I did first and now I never screw anything up.

---

### Post by Lord Xeb on 2008-07-04
I wish some of the numbskulls that go around installing linux and then flaming it sayiing that it destroyed their computs would do this e_e



*pulls out shotgun* IF YOU DO NOT BACKUP YOU SYSTEM, THEN YOUR GOING TO REGRET IT!!!!

---

