---
title: "Forensics on NTFS drive"
date: 2015-03-25
forum: Security
---

### Post by trenien2 on 2015-03-25
Hi all.
Although I'm in no way a windows specialist, I've been asked to perform a kind of minimal forensics on a computer running under windows XP (or maybe Vista, but very probably not). The idea is to know whether files within a specific directory have either been moved, copied, deleted or accessed after a given date.
I intend to boot under a live distro and to get as many informations as possible.
I assume a simple global ls (ls -Ralh) will tell all I need to know about moved/modified files as it would under linux, but after that I am kind of stumped. So my questions are : Is there anyway, and if so how to :
- See whether and when a file as been accessed without being modified (I understand NTFS filesystems at least sometime keep track of such information)?
- Know if and when some files have been deleted from the directory?

Thanks

---

### Post by TheFu on 2015-03-25
You are not prepared for this.

Specialized hardware and signaling control is needed with the write signaling completely removed.  Even mounting a partition as read-only can modify it. You can google for the cable pins to be removed.

If this is to be used for any legal or employee action, please use a certified forensics provider. Once you touch the disk, it is too late.

---

### Post by trenien2 on 2015-03-25
I'm aware of that. That said, the computer can have been used at any time after the date of starting interest. That tend to make such a level of caution kind of a moot point. We mostly expect very crude actions, such moving files around and the like.

---

### Post by TheFu on 2015-03-25
atime, mtime, ctime and daily backups should show changes from day to day. On servers, daily file checksums to compare would be helpful too. 

A Windows forensics expert will know 1000x more. I can recommend [http://www.forensicstrategy.com/](http://www.forensicstrategy.com/)  . Scott knows his stuff and is licensed.  You can find his talks on youtube and at Defcon.

---

### Post by bashiergui on 2015-03-25
Thefu made an excellent point. As soon as you touch the files you're interested in, you'll modify the records. And some of those records only contain the most recent date so you'll effectively erase the details you're interested in.

You need to mount the Ntfs drive write-blocked.

Beyond that you can search [http://forensicswiki.org/wiki/Main_Page](http://forensicswiki.org/wiki/Main_Page) for things to look for.

---

### Post by bardo2 on 2015-03-26
Wow, excellent posts in here. While this is a non-issue for me, how i would go at it is this:
never mount the drive in any way. instead copy the entirety /dev//sd(n) into an image file. loop mount it and look around. if you still need some more real info, you'd still have the original data untouched. If it were me, i'd even move the image to some COW filesystem and snapshot it before loop mounting, thus having an easy way back. But.. i am no forensics expert, just an old aged computer geezer. :-)

edit:
next idea: Windows has better tools to look around an NTFS filesystem, so i would consider mounting the image from a virtual machine running some windows

---

### Post by TheFu on 2015-03-26
As soon as someone unlicensed touches the disk, you've broken the chain of custody, the drive is "tainted" and cannot be used for evidence. The chain of control is critical. If the company takes action based on tainted evidence, it is asking for a lawsuit. Check with legal council.

As soon as a regular cable is connected to the HDD, you don't know it hasn't been modified. Get/make a read-only cable to connect the suspect disk.

You need an exact bit-for-bit copy - the missing parts are just as important as the still allocated stuff. COW will loose those, right?

---

### Post by bardo2 on 2015-03-26
> **TheFu said:**
> 
You need an exact bit-for-bit copy - the missing parts are just as important as the still allocated stuff. COW will loose those, right?

No.
```

sudo dd if=/dev/sdx of=/mnt/cow/sdx.img # copy everything
# now, make a snapshot  like so: zfs snapshot mypool/cow@original
sudo kpartx -arv /mnt/cow/sdx.img
for i in /dev/mapper/lo*;do I=`basename $i`;mkdir -p /mnt/tmp/loop/$I; sudo mount -o ro $i /mnt/tmp/loop/$I;done
# investigate from linux

```
And if something needs changing, just do it and rollback later

---

### Post by Kenneth_Benson on 2015-03-27
On GitHub(or Sourceforge, one of the two) there is a project called Katana. It includes software specifically designed for forensics. You may want to take a look at that. I believe it includes docs, I'm not sure
as I haven't played with it.

---

