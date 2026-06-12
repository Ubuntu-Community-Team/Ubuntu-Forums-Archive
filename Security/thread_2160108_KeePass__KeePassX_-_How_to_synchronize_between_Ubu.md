---
title: "KeePass / KeePassX - How to synchronize between Ubuntu and Windows?"
date: 2013-07-05
forum: Security
---

### Post by cforput on 2013-07-05
I have a work computer running windows (don't shun me, they make me us it) and my laptop at home runs Ubuntu 13.10 currently. I have a bunch of passwords at work and a bunch of personal ones both in a single DB file but have 2 copies of the DB, one at work and one at home. I try to keep them in sync manually. When I make a change at work, I update my DB at home, etc. I've read that KeepassX has a sync option but it isn't listed in any of my menus (version 0.4.3). I've also tried exporting and manually syncing but that wasn't too successful and was very time consuming. I don't really want to use the USB method for fear of losing the USB drive and also I don't need to sync that often so I would end up spending more time pulling out the USB drive when ever I needed to look up a PW.  

I'm not stuck on KeePassX, I'm just looking for a program that runs on Ubuntu and Windows that will let me sync 2 different db files to keep them up to date.

---

### Post by Hungry Man on 2013-07-05
Just put the database on a USB drive and keep a backup at home? The thing is, even if you lose the USB, if you've set up a strong password the worst that happens is you lose the databaes, which is why backing it up is important. No one's getting into KeyPass if you use a strong password.

Or look into LastPass.

---

### Post by CharlesA on 2013-07-05
> **Hungry Man said:**
> Just put the database on a USB drive and keep a backup at home? The thing is, even if you lose the USB, if you've set up a strong password the worst that happens is you lose the databaes, which is why backing it up is important. No one's getting into KeyPass if you use a strong password.

Or look into LastPass.

Pretty much nailed it. You will probably want to keep the key backed up as well.

---

### Post by cforput on 2013-07-06
The other reason I don't want to go down the USB path is that there are rumors at work that they may take away our ability to use a USB on our laptops. Then I have a process that doesn't work at all.

---

### Post by Hungry Man on 2013-07-06
Well, you could use DropBox to sync the KeyPass file, but I would consider LastPass more secure, especially because it supports multi-factor auth, and a lot of encryption.

---

### Post by Bashtard on 2013-07-06
I wouldn't recommend Dropbox for storing sensitive data.
[http://securityaffairs.co/wordpress/15944/hacking/dropbox-account-hacking.html](http://securityaffairs.co/wordpress/15944/hacking/dropbox-account-hacking.html)
But the idea isn't terrible to sync it with some *slightly more secure* cloud service. Just make sure your company doesn't block the service you want to use.

---

### Post by CharlesA on 2013-07-06
Sounds like dropbox needs to fix that flaw in their account system. FWIW, I've seen the same thing happen with other software, mostly forums and the like that allowed a user to access another user's information/PM/etc.

---

### Post by Hungry Man on 2013-07-06
I wouldn't really suggest dropbox either, but I know people use it. LastPass is the way to go I think.

---

### Post by trundlenut on 2013-07-08
I use Spideroak to sync the database between ubuntu, windows and Android.

---

