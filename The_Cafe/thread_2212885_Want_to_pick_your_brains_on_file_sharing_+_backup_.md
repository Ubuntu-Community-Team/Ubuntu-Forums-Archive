---
title: "Want to pick your brains on file sharing + backup strategy for multi-OS set-up"
date: 2014-03-23
forum: The Cafe
---

### Post by PartisanEntity on 2014-03-23
I have the following computer landscape at home:

1x Ubuntu machine
2x OSX machines

I want to achieve the most harmonious:

a) file sharing solution
b) backup solution

I have identified HFS+ (unjournaled) as a good file system to use to share files between the two operating systems. I am currently testing a HDD being shared by both systems with read/write capabilities from both.

For backups at the moment it's quite chaotic, the OSX machines backup to a dedicated HDD.

The Ubuntu machine backsup to a different dedicated HDD.

I am torn between two set-ups:

a) 1 HDD using HFS+ to share files between all systems. 1 HDD per system for dedicated backups (i.e. 3 HDDs for backups).

or

b) Set up a 4th machine. An old laptop running Ubuntu, to which I attach several HDDS and this then serves as a NAS for file sharing and backups over the network.

I cannot decide which option makes more sense. I think option b) would be the least stressful method, but any drawbacks to it?

---

### Post by sandyd on 2014-03-23
> **PartisanEntity said:**
> I have the following computer landscape at home:

1x Ubuntu machine
2x OSX machines

I want to achieve the most harmonious:

a) file sharing solution
b) backup solution

I have identified HFS+ (unjournaled) as a good file system to use to share files between the two operating systems. I am currently testing a HDD being shared by both systems with read/write capabilities from both.

For backups at the moment it's quite chaotic, the OSX machines backup to a dedicated HDD.

The Ubuntu machine backsup to a different dedicated HDD.

I am torn between two set-ups:

a) 1 HDD using HFS+ to share files between all systems. 1 HDD per system for dedicated backups (i.e. 3 HDDs for backups).

or

b) Set up a 4th machine. An old laptop running Ubuntu, to which I attach several HDDS and this then serves as a NAS for file sharing and backups over the network.

I cannot decide which option makes more sense. I think option b) would be the least stressful method, but any drawbacks to it?

a) has no redundancy and will cause you to loose all your backups when HDD fails
b) will allow you to build a RAID array which allows for some level of redundancy depending on what level you decide to use. Also allows you to add more HDD space as you go on, providing your using LVM partitioning

---

### Post by coffeecat on 2014-03-23
> **PartisanEntity said:**
> I have identified HFS+ (unjournaled) as a good file system to use to share files between the two operating systems.

I used to use a Mac Mini regularly as well as my Ubuntu machines and did use unjournalled HFS+ for a time for backups but there were some irritations. The main one was different UIDs in Ubuntu and in MacOS - 1000 in Ubuntu and 501 in MacOS if I remember correctly, and I had to fiddle about with permissions. There was also one time that Ubuntu refused to mount the partition possibly because of filesystem damage, which I was able to fix from the MacOS disk utility, but the incident made me nervous about backing up to an unjournalled filesystem.

I rely on NAS devices now, so my vote would be for some sort of NAS solution.

---

### Post by CharlesA on 2014-03-23
I vote for NAS as well. It's what I use. :)

---

### Post by PartisanEntity on 2014-03-24
Thanks so much for the feedback.

Just brainstorming: if I decide to take the NAS approach, is the file-system on the NAS itself relevant anymore?

I assume I would be sharing files and folders through smb and afp protocols for example. So does my NAS have to have HFS+ partitions for the Macs specifically? I guess not right?

---

### Post by CharlesA on 2014-03-24
File system doesn't matter. I'm currently serving stuff off my server running ext4 to a few Windows boxes and a few Linux boxes via Samba.

---

### Post by PartisanEntity on 2014-04-05
I came across an article today in a german Linux magazing about NAS4free ( [http://www.nas4free.org/](http://www.nas4free.org/) ) and so I decided to give it a try.

Without knowing anything about typical NAS packages and performance, my first impression is a positive one. Was very easy to install on my ancient Asus laptop, and all the subsequent management is done through a web interface.

Seems to have a nice range of services, among others: CIFS/SMB, NFS, AFP, FTP. SSH, Rsync, DLNA/UpnP, iTunes/DAAP, UPS, Webserver, Bittorrent, etc..

Anyone have any experiences with it? Does it have a good reputation and is it stable? I need something I can rely on long term.

---

