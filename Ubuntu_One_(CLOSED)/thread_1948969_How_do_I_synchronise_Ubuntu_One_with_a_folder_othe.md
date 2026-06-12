---
title: "How do I synchronise Ubuntu One with a folder other than ~/Ubuntu One"
date: 2012-03-29
forum: Ubuntu One (CLOSED)
---

### Post by t0p on 2012-03-29
I have recently got myself a Ubuntu One account so as to take advantage of the free 5GB storage.  Problem is, my HDD is very small (30GB, would you believe!  Yeah, stone age etc, but anyway...), if I move all the stuff I want to sync to ~/Ubuntu One, I'm gonna use up all the HDD room real quick.

Can I set Ubuntu One to sync with a directory on my external 1TB HDD?  If so, how?

Cheers!

---

### Post by nothingspecial on 2012-03-30
*Thread moved to **Ubuntu One**.*

---

### Post by fyfe54 on 2012-03-30
Deleted.  
Too early, not enough coffee.

---

### Post by t0p on 2012-04-02
Then drink more coffee, you rogue!

Seriously though, can't anyone help with this?  Syncing 5 GB of my home directory is about as much use to me as a chocolate teapot...

---

### Post by duanedesign on 2012-04-06
"Allowing users to select arbitrary folders outside of their home for syncing with Ubuntu One, which could potentially sync between multiple different computers, opens a large number of usability problems.

One of the problems that I remember off the top of my head is that if you try to sync a mount point of a removable device (and quite a few people try to do this), when you remove the device syncdaemon will delete everything; to make it work properly syncdaemon would have to know about devices, detect their removal, things like that. Quite a large effort, and a lot of potential for usability nightmares.

Another problem is if you try to sync a folder with special permissions, ownership or file types in it: think of /etc/, /tmp/ or /dev/ as some of the worst cases. Or any folder you don't own, really. We could simply disallow syncing folders you don't own, but we know for a fact some people are running syncdaemon as root (despite our warnings).

A workaround for you would be to mount (via /etc/fstab, so you're reasonably sure the partition is mounted every time -- otherwise you risk losing your synced data) the /data folder into your home. You could simply move /data to ~/data or, if you have things that have the /data path hardcoded (quite likely), or if you're already used to /data yourself (also quite likely), symlink or bind mount /data to the mount point in your home. If you don't want to see it in your home at all, just make it ~/.data."[1]

[1] [http://askubuntu.com/questions/51362/why-not-sync-folders-outside-home-with-ubuntu-one](http://askubuntu.com/questions/51362/why-not-sync-folders-outside-home-with-ubuntu-one)

---

### Post by growingneeds on 2012-04-18
Ubuntu One synchronizes all of the items in the Ubuntu One folder into the cloud. Similarly, all of the items uploaded into the web interface of Ubuntu One will be downloaded to all your computers.

After signing in to Ubuntu One, right-clicking on any folder should bring up the synchronization option.

---

