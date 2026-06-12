---
title: "Setting Quotas to FOLDERS"
date: 2011-09-15
forum: Server Platforms
---

### Post by kembar4 on 2011-09-15
Hello,

I am a newbie to linux. I plan to run unbuntu on a server, where users can store and download their files to a specific folder via a torrent client. Each user would receive an individual folder which only they can access.

My question is, How do i impose a quota on the folder? I've read about quotas on disks and user profiles but I dont think those would be for me, since i would be running multiple instances of the torrent client in one user profile.

How would i go about imposing quotas on folders? Would I be able to use a windows based software with wine? Or is there another way?

---

### Post by rubylaser on 2011-09-15
AFAIK, folder quotas in EXT4 don't work.  Quotas work on a filesystem level.  You could either use a filesystem that supports folder quotas (zfs), or create a virtual filesystem like [this]("http://ext3vsext4.com/2011/06/linux-directory-quota-howto/").  I'd be interested to know if someone else says that I'm wrong, or has other ideas.

---

