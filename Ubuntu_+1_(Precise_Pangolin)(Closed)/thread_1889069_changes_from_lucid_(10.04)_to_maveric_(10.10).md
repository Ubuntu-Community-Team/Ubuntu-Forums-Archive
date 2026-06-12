---
title: "changes from lucid (10.04) to maveric (10.10)"
date: 2011-11-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ronacc on 2011-11-30
where can I find a list of the changes from lucid (10.04 ) to maveric (10.10 ) ? I am trying to chase down a difference in the way network drives are mounted . I know this is off topic for this forum but I think this is the best place to ask .

---

### Post by BC59 on 2011-11-30
You can compare the packages list of each version:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by ronacc on 2011-11-30
thanks but I was hoping to narrow things down to a bit less than all available packages .

---

### Post by cariboo on 2011-11-30
The only thing I can see is that smbfs is deprecated, and cifs is used in its place, according to [this]("https://help.ubuntu.com/community/Samba/SambaClientGuide") wiki page. Assuming you're talking about Samba of course.

**Edit:** Macs also do NFS, at least my old iMac running OSX 10.4 does.

---

### Post by ronacc on 2011-11-30
Thanks cariboo907 , I think that may be it , atleast it gives me something to try .

---

### Post by ventrical on 2011-11-30
My parts supplier set up a Samba server but I can't sell him on Ubuntu because he tried to set up a RAID drive and there was no way he could get it going, causing him a lot of downtime. If I find anything ronacc I'll chime in.

---

### Post by ronacc on 2011-11-30
thanks , I'll be a little more specific about what I am trying to do / find . I got an apple timecapsule to use for backups of my apples and took the usb drive that I had been using for that and reformated it to fat32 and attached it to the timecapsule via usb as network storage , from anything later than lucid I can see the storage drive but not mount it UNLESS it has been first accessed by a system running lucid . So I am trying to figure out why first accessing it with lucid makes it available to later releases ( even if the lucid install is no longer running ). I'm thinking it either has to be a permission difference or the way that network drives are accessed .

---

### Post by cariboo on 2011-11-30
Have you tried NTFS, because vfat has that 4GiB file size limit.

---

### Post by effenberg0x0 on 2011-11-30
> **ventrical said:**
> My parts supplier set up a Samba server but I can't sell him on Ubuntu because he tried to set up a RAID drive and there was no way he could get it going, causing him a lot of downtime. If I find anything ronacc I'll chime in.

My home-office server is a Ubuntu Server with two mdadm RAIDs:
- One RAID 1 for the OS itself (2x1500GB=1.5TB): Mounted /
- One RAID 6 for storage (6x1500GB SATA=6TB)? mount /media/home-office

I run smbd normally in the server. My desktop, other devices (laptops, smartphone, HTPC, etc) see and use the samba shares normally. I also have laser/inkjet printers and a scanner on this server, which are normally seen by users via CUPS over cifs.

This small server runs a bunch of other stuff: VPN, FTP, Apache, Postfix, Git, Usenet / Torrents, etc. Installing / settin-up daemons in Ubuntu is a breeze compared to what it was in the past.  

There's a lot of instructions and tutorials, including Ubuntu documentation, on how to get a RAID up on Ubuntu. It's easy. samba/cifs installing requires one apt-get install. It's really no trouble at all. If you show him, he won't believe it can be so easy and quick.

---

### Post by effenberg0x0 on 2011-11-30
> **ronacc said:**
> thanks , I'll be a little more specific about what I am trying to do / find . I got an apple timecapsule to use for backups of my apples and took the usb drive that I had been using for that and reformated it to fat32 and attached it to the timecapsule via usb as network storage , from anything later than lucid I can see the storage drive but not mount it UNLESS it has been first accessed by a system running lucid . So I am trying to figure out why first accessing it with lucid makes it available to later releases ( even if the lucid install is no longer running ). I'm thinking it either has to be a permission difference or the way that network drives are accessed .

Ronacc, how are you mounting? I ask because if you try via command line we should be able to get some feedback, like the specific error that is happening. I mean, if you try to mount it like:
```
sudo mkdir /media/mynas
sudo chown ronacc:root /media/mynas -R
sudo chmod 775 media/mynas -R
sudo mount -t cifs //192.168.1.101/"Ronacc's Time Capsule"/ronacc_share /media/mynas -o username=someUsername,password=somePassword,iocharset=utf8,file_mode=0777,dir_mode=0777

```Then it will output some cifs error code we can check to see whats happening. You can also check dmesg.

---

### Post by ronacc on 2011-11-30
> **cariboo907 said:**
> Have you tried NTFS, because vfat has that 4GiB file size limit.

I was about to do that when I accidentally discovered that I could access it from lucid and that made it accessible from later releases , why that was so got me curious so I have been chasing that , The access persists for a few hours but after that it has to be reaccessed with lucid . accessing from my macs does not make it accessible like from lucid .

---

### Post by ronacc on 2011-12-02
following a suggestion from cariboo907 I reformated the drive , but instead of NTFS I went whole hog and formatted it to Mac extended os , I didn't think Ubuntu would read this but either it will or the timecapsule translates it because now I can access read and write to it without first accessing it with lucid .

---

