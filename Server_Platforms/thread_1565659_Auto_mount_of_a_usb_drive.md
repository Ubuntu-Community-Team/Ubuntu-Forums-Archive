---
title: "Auto mount of a usb drive"
date: 2010-09-01
forum: Server Platforms
---

### Post by MarkyMarc35 on 2010-09-01
Hello All,
 
I just changed the os on my media server from Windows Home Server to Unbuntu 10.4 server. I got most of it working (samba, twonkymedia) with allot of help from mr. Google :D
 
The only thing i have left to get working is the backup of that server. I installed bacula as i beleive it will do the job (unless someone has a better and simpler to configure idea) and i would like it to backup to my external usb 1Tb hard drive.
I am able to mount the drive manually but this server gets turn on and off often to save power (and cut the electric bill) when not in use. 
I tried adding a line to fstab but when a do that, the server gets stuck on the startup even with the drive turned on. I read somewhere that i should use the UUID of the drive as it could change from sbd1 to sbh1 on restart so i did, same result.
 
Any advise would be apreciated.

---

### Post by arrrghhh on 2010-09-01
So even with the UUID in the fstab entry it didn't work...?

Maybe you should just plug the drive in when you need it if the server gets turned off, I don't see why that would be an issue.  Not a pretty solution, but the UUID fstab entry *should* work assuming the drive is powered & plugged in.

---

### Post by MarkyMarc35 on 2010-09-01
Exactly.
The line in fstab is
UUID=1a542b49542b274b /backup ntfs-3g defaults,locale=en_US.utf8 0 0
 
On the statup of the server, it gets stuck after the 3rd time the line
init: ureadahead-other main process (750) terminated with status 4
is shown.
 
I have the ctrl-D to cancel whatever it's doing and get my server back.
 
If i comment out the line in fstab, everything works perfect.

---

### Post by MarkyMarc35 on 2010-09-01
I've finally found the problem ..... me :o
I entered the UUID with lower case letters instead of the UPPER CASE as the external drive is NTFS.
 
I'm such a noob ...

---

### Post by arrrghhh on 2010-09-01
Ah... yes, everything is case-sensitive in Linux.  Took some getting used to for me as well!

---

