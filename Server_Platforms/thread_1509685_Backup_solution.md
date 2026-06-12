---
title: "Backup solution"
date: 2010-06-14
forum: Server Platforms
---

### Post by micrometric on 2010-06-14
Hello,

I'm trying to find a backup solution for a new server. It's running 10.04 Server edition. I need to be able to have an automated solution that can be run while the system is in use as it can not be shut down. The only command I've found that can do this is dd.  Unfortunately, I'm only using about 2GB of the drive and am wasting storage space from all the empty blocks. Is there another program I can use that actually allows a backup of the system while it's running that compresses the image?

---

### Post by CharlesA on 2010-06-14
Could tar it, but that's kinda iffy. Normally you would image the machine after you get it up and running and then restore that image if anything happens to it.

---

### Post by micrometric on 2010-06-14
I need something I can run on a schedule, say weekly, that can be restored if the system crashes.

---

### Post by dapperdanny77 on 2010-06-14
if you just want to have your files backed up somewhere without keeping different versions of files the rsync is the perfect choice - works great over the network

a more sophisticated backup can be achieved with backup software like bacula is

either way this means if your server dies you have to reinstall and restore from the backup

if you need a bootable backup I heard of mondo, but have no experience with this

---

### Post by argail1980 on 2010-06-14
Hi,

I have BackupPC running on a Lucid server. It gets full and incr. backups from several cliets via rsync, ssh or smb. It can also back up the server itself (e.g. on an external hard drive). I did not try a full restore yet, but i find it optimal to restore single files, e.g. when somebody deletes files by mistake. Drawback: web based interface

---

### Post by arrrghhh on 2010-06-14
If you want a complete, bit-for-bit copy of the hard drive you're going to have to take it down... Unless it's a VM and you can take a snapshot.

Other than that, all the backup solutions will just backup files - there's plenty of those out there, but it seems like you wanted a bit-for-bit copy of the server to do a complete restore from the MBR up...

---

### Post by arrrghhh on 2010-06-14
Sorry I double-posted...

---

### Post by HermanAB on 2010-06-15
Hmm, dd for backups is not recommended. It is sloooow and tied to specific hardware.  One day when your server fails, you then need to find an identical replacement on Ebay or something.

The better way to manage servers is to virtualize them.  You can backup the whole VM using tar and save it to a DVD.  You only need to do this once. Then store all the data outside the VM on a network share.  The data, you can then backup daily or weekly or whatever to an external HDD or tape.

One day when the server fails, or when you need to upgrade to more powerful hardware, you install a new machine with VMware, copy the VM from the DVD and restore your data from backup.

---

