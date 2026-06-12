---
title: "Ubuntu 16.04(HyperV)-very large file in /tmp,keeps growing at about 1GB/h"
date: 2017-04-19
forum: Virtualisation
---

### Post by steeflemmens on 2017-04-19
I'm ICT coördinator at a high school and I'm running a Plex server on  an Ubuntu 16.04 machine in VMware. This one runs flawlessly. 
  
However, we're moving our servers to a data center, so I'm setting up  a Plex server there. I have installed everything on a HyperV machine in  the data center. 

This is my set-up:

  
[LIST]
[*]4 CPU's
[*]1TB of storage [[IMG]https://i.stack.imgur.com/Zel7T.png[/IMG]]("https://i.stack.imgur.com/Zel7T.png")
[/LIST]
  
I'm testing the server and I noticed some strange things, while I'm  doing nothing at the Ubuntu Machine, only accessing it via xrdp/RDP:

  
[LIST]
[*]There's a file in /tmp that grows at a rate of about 10GB per hour. I have no idea which process is responsible for this. (it's the big one: dup-e7e7...) [[IMG]https://i.stack.imgur.com/pOI8H.png[/IMG]]("https://i.stack.imgur.com/pOI8H.png")
[*]KSysGuard shows an almost constant CPU usage of over 30%
[*]KSysGuard also shows a constant stream of incoming network traffic at a rate of about 5MiB/s [[IMG]https://i.stack.imgur.com/tJ6qN.png[/IMG]]("https://i.stack.imgur.com/tJ6qN.png")
[/LIST]
  I'm currently running a identical Plex server on a VmWare setup and I  don't have any of these problems there, this one has been running  flawlessly for over 4 months now. 


  Any thoughts on what could be the problem or on how I could find what's causing this? 
  I've tried lsof, auditctl, no results...


  Thanks in advance!

---

### Post by TheFu on 2017-04-19
I run plex inside a KVM VM and don't see the issue either.  We only have 2 hidef streams at a time, so 1 Core and 1GB of RAM is plenty.  More CPU and more RAM isn't always better when it comes to Linux, especially with VMs.

So ... I'd start by assuming it is an issue with hyper-v.  I always assume issues with hyper-v.

Plus I'd purge Unity and compiz for a lighter GUI, like XFCE.  Over a remote connection, it just makes sense, if you even have **any** GUI at all. GUIs on Linux servers are generally considered a bad idea.

---

### Post by steeflemmens on 2017-04-20
We have 54 classrooms with a Apple TV each that can access the Plex Server at the same time. The teachers can access it via web as well. Hence the slight overkill in CPU and RAM, we can't afford it to have the media server not managing. I can always alter the number of CPU's and RAM if necessary. 

I know a GUI is considered bad practice in a Linux server, but I have a few not-Linux-minded coworkers who like to have a gui for file management and such. I used Unity because I wanted to use a Google Drive folder and couldn't get that to work in xfce ;) Most of the time I use ssh, Unity almost exclusively for Google Drive and file management.  

Unfortunately, we don't have access to the Hyper V Tools... So I'm first trying to find a solution in Ubuntu, if not possible, I'll just have to call the data center and see if they can find a solution in Hyper V.

---

### Post by TheFu on 2017-04-20
Which file system(s) are being used?  Any doing de-duplication?
Google found this: [https://bugzilla.redhat.com/show_bug.cgi?id=892063](https://bugzilla.redhat.com/show_bug.cgi?id=892063)  when I used "dup- files /tmp" for the query.  Deja Dup backups?

---

### Post by steeflemmens on 2017-04-21
These are the filesystems that are being used:
[ATTACH=CONFIG]274684[/ATTACH]

How can I see if any of these are doing de-duplication? 

I checked if automatic backups are enabled, they aren't. There is however a program installed that's called "Duplicati", this might be the cause? I've paused Duplicati, will report if there's any difference.

---

### Post by TheFu on 2017-04-21
Duplicity, deja-Dup, duplicati are all related. Duplicity is the CLI tool. The others are GUIs. You don't "need" them unless that is your backup method.  I found those tools to be too slow to be used when I tested them years ago.

File systems that do deduplication would have that enabled in the settings. ZFS, btrfs are the main ones I know that would do it.
Please don't post images. Use text to be nice to low-bandwidth visitors.

---

### Post by steeflemmens on 2017-04-21
Alright, it was related to backups. Logged in to Duplicati and stopped the automatic backup. It seemed it was constantly trying to backup my system, but never succeeding, as there are no finished backups.

With Duplicati stopped, the dup files don't grow anymore (well, they do, but nowhere near as fast), so it's definatley related to this. CPU percentage is dropped from around 30% to about 10%.

---

