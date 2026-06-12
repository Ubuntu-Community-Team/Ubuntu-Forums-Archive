---
title: "Ubuntu Server For OSX Lion"
date: 2011-07-26
forum: Server Platforms
---

### Post by gibsonc1 on 2011-07-26
Hi (Im new to Ubuntu and to this forum so sorry if this is in the wrong place or I have done something new!) 

I have a old pc and am planning on turning it into a file/print server for my mac. I use a Macbook Pro running Lion, which I want to connect to the server wirelessly. 

I want the server to be set up so I can access my external hard drives and use one of them for Time Machine. 

It would be good if it could also be able to act as a print server for my HP printer so I get wireless printing from my mac. 

Do I need to use Ubuntu server for this or will the desktop version work? I have found a few blog posts about this online although they are not very clear. How can I go about setting this up? 


Thanks 
Chris

---

### Post by arrrghhh on 2011-07-26
Well Ubuntu Server is good for old hardware - assuming you're OK with no GUI (command-line **only**) Ubuntu Server is great!

If you feel you need a full desktop environment (DE) and the rig can handle it, go for Ubuntu Desktop.

All the other stuff you mentioned is trivial.  Assuming the server is connected via cabled ethernet, and it's plugged into your wireless router the server will have no problem being accessed by your mac wirelessly.

I'd think samba would take care of all the file/printer sharing you need.  CUPS is probably overkill for your purposes.

---

### Post by gibsonc1 on 2011-07-26
OK I think I will go with Desktop, its a P4 machine running at 2.6ghz I think with about 512mb of ram I think. Should be good, thanks a lot for the help.

Chris

---

### Post by ratcheer on 2011-07-26
Make sure Time Machine will work with your disk partition format.

Tim

---

### Post by rubylaser on 2011-07-26
Timemachine will work fine with any partition type/filesystem.  You just to share it out via AFP with Netatalk.  I share via NFS, and AFP to (2) Macbook Pro's with Lion in my house with no problems at at (including Timemachine backups).  This is off an mdadm array, with an EXT4 filesystem.

---

### Post by Tylerjd on 2011-07-26
That should work great ( basically the same as what I do).

For a great tutorial on setting up an AFP server in ubuntu, take a look at [this]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

There is one step that needs to be slightly changed in the newer Ubuntu releases (slips my mind which one). You should be able to find it in the numerous comments though.

*And I would urge you to use AFP over Samba, as Samba kills the specific permissions that Apple has on the files backed up by TimeMachine. Your backups will become corrupted if you use Samba*

---

### Post by arrrghhh on 2011-07-26
> **Tylerjd said:**
> That should work great ( basically the same as what I do).

For a great tutorial on setting up an AFP server in ubuntu, take a look at [this]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

There is one step that needs to be slightly changed in the newer Ubuntu releases (slips my mind which one). You should be able to find it in the numerous comments though.

*And I would urge you to use AFP over Samba, as Samba kills the specific permissions that Apple has on the files backed up by TimeMachine. Your backups will become corrupted if you use Samba*

Heh, I guess I don't use Mac very often...(wait... at all :p) I definitely prefer NFS over samba when I'm dealing with Linux boxes, I forget that Mac's can handle that protocol as well.

Ok, scratch samba.  What would you guys recommend to him for printer sharing?  NFS works great for file sharing...  I guess CUPS would be the only option, unless you want to use samba just for printer sharing (which I'm sure works just fine).

---

### Post by ratcheer on 2011-07-27
> **rubylaser said:**
> Timemachine will work fine with any partition type/filesystem. 

Really?

I wanted to back up my 13-year old son's MacBook Pro before upgrading to Lion, this past weekend. I have a 2 TB external drive with plenty of available space, so I connected it directly (USB) to the MacBook Pro and started Time Machine. It wanted to erase the disk drive and reformat it. I said No and searched for ways to do what I needed. Apple's Support web site confirmed that it could not be done.

> **Note:** Every available disk that can be used to store backups is  listed. If you’ve partitioned a disk, the available partitions are  listed. Time Machine can’t back up to an external disk that's connected  to an AirPort Extreme, or to an iPod, iDisk, or a disk formatted for  Microsoft Windows (NTFS or FAT format).  If you select an NTFS or  FAT-formatted disk, Time Machine prompts you to reformat the disk.  Choose a different disk or reformat the disk in Mac OS Extended  (Journaled) format. Because reformatting erases any files on the disk,  only do this if you no longer need the files or if you have copies of  them on a different disk.


[http://support.apple.com/kb/HT1427](http://support.apple.com/kb/HT1427)

Tim

---

### Post by volkswagner on 2011-07-27
> **ratcheer said:**
> Really?

I wanted to back up my 13-year old son's MacBook Pro before upgrading to Lion, this past weekend. I have a 2 TB external drive with plenty of available space, so I connected it directly (USB) to the MacBook Pro and started Time Machine. It wanted to erase the disk drive and reformat it. I said No and searched for ways to do what I needed. Apple's Support web site confirmed that it could not be done.



[http://support.apple.com/kb/HT1427](http://support.apple.com/kb/HT1427)

Tim

I think what rubylaser was referring to was specific to using the file share protocols mentioned.  When using SAMBA, AFP, NFS, etc. the file system is not read directly and therefore nearly irrelevant.

When connecting the drive directly to the MAC, yes file system is gonna be dictated by TimeMachines requirement.


As for the Server in question, I'd stick with the server version with only 512MB RAM, performance will be much better with no GUI.

---

### Post by rubylaser on 2011-07-27
> **volkswagner said:**
> I think what rubylaser was referring to was specific to using the file share protocols mentioned.  When using SAMBA, AFP, NFS, etc. the file system is not read directly and therefore nearly irrelevant.

When connecting the drive directly to the MAC, yes file system is gonna be dictated by TimeMachines requirement.


As for the Server in question, I'd stick with the server version with only 512MB RAM, performance will be much better with no GUI.

Yes, I was talking about via sharing protocol :)  You could open the disk utility on the mac and resize the existing partition and then add a new HFS+ partition at the end for TimeMachine if you'd like to use the drive without reformatting.

---

