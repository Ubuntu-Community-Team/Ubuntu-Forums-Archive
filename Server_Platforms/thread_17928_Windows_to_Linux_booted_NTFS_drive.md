---
title: "Windows to Linux booted NTFS drive"
date: 2005-03-03
forum: Server Platforms
---

### Post by bob k on 2005-03-03
I have a production computer running WIN 2K Pro on a LAN (netbios)  that contains all of my company data. I do nightly image backups to a HD on the 2K box.

I loaded Ubuntu on another box that I used for weekly Image backups, thinking that Linux wasn't quite ready. Boy was I wrong, I have ended up using Ubuntu for every thing, except for Email (outlook is just a better product) and windows only apps.

My problem is that I forget to reboot back to windows on weekly backup night, and would like to automate this step.

Has anybody done this? Any Ideas on how to do this?
I have looked at Samba but I don't want to run it 24/7,
just start it up at a specified time and then shut it down.

I don't need a detailed map on how to do this, just point me in the right direction and some of the problems that you have had.

Any Input will be Valued

Bob

---

### Post by alastair on 2005-03-03
You'll want to use Samba to a greater or lesser degree probably - it's the easiest link to NT shares. Take you time to test (small directories etc.) and experiment. It's no problem to run it 24x7.

Look to mount your NT share(s) via smbfs (or even the "cifs" filesystem). Smbfs is older and more well known.

Check you have "smbfs" installed then :

man smbmount

You can mount your NT share(s) and do a backup to the share - perhaps look at using "rsync" for the backup.

---

### Post by bob k on 2005-03-03
I'm wanting to backup from my windows machine to a samba NTFS share. The Idea with this trek is that both boxes are running the same hardware so all I have to do is restore and be up and running in 1hr. I would lose my grub but I could live with that for a few days to keep my company running, but I would like to have both worlds.

I'm using drive image on the windows side, it can read the Linux drive if booted to windows, but the compression sucks if there is any.

I have half of a computer lying around all it needs is some memory, a processor and a box. ($200usd) move all of my disks and make into a backup server, tack it on my router, no monitor, and email me every night as to the status. I would have to get a bigger KVM switch. This way I can backup both computers.

I guess I've been thinking out loud, anybody done this.

TIA

Bob

---

