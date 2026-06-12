---
title: "VirtualBox Upgrade - Safe?"
date: 2009-01-28
forum: Virtualisation
---

### Post by fishman78 on 2009-01-28
Hi All,

   I got a message saying I should upgrade my Vbox yesterday.  I would like to upgrade as I would like to give Windows 7 a try.  My question is, should I backup my virtual drive or will it upgrade without changing my current guest?  If I should back it up, how would I go about doing that.  I heard just backing up the .vdi is a no go.  Any help is greatly appreciated!  Thanks!

fishman78

---

### Post by RomeReactor on 2009-01-28
Hi. You shouldn't have any problem upgrading. I updated a half hour ago and it's running OpenSolaris 2008.11 flawlessly.

---

### Post by HotShotDJ on 2009-01-28
> **fishman78 said:**
> My question is, should I backup my virtual drive or will it upgrade without changing my current guest?It is always a very good idea to backup your data before upgrading.  You can back up your VirtualBox directory using the following:```
mkdir ~/Backup && cp -a ~/.VirtualBox ~/Backup
```You can find the backup of your VirtualBox settings and VDI in ~/Backup/.VirtualBox.  If you want to back up to another location, leave off the "mkdir ~/Backup &&" part and replace "~/Backup" with full path to your preferred location, for example "/media/disk" or where ever you like.

Having said that, I've never actually NEEDED my backups after upgrading.  I HAVE needed them after doing very STUPID things to my guest OS. :)

---

### Post by dmizer on 2009-01-28
Moved this to the virtualization section. Thanks :)

---

### Post by Dedoimedo on 2009-01-29
Backing up is always a good idea.

That said, I did an upgrade about a week ago or so and things went smoothly. This with the puel version of VB on Ubuntu 8.10, 32-bit.

Dedoimedo

---

### Post by binbash on 2009-01-30
I never saw a problem while upgrading but you should do a backup

---

