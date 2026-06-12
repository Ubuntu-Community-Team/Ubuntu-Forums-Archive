---
title: "[SOLVED] 8.04 Reboot"
date: 2008-10-24
forum: Server Platforms
---

### Post by Guigues67 on 2008-10-24
Hello,

I'm new on this forum and on Ubuntu Server too. 
Many thanks for those who will help me.

I've a problem on a Ubuntu Server 8.04.
I did a reboot yesterday evening (sudo reboot -now).
The server did its reboot.
But all data/files created since September 10th were lost

The server went back to the state of this date (configuration files, data, files, ...) 

Can anybody help me on this subject ?

Guy

---

### Post by StickyStyle on 2008-10-24
Where all the 'lost' files perhaps on another drive, or network share?  e.g. you mounted a drive, started using it but forgot to add it to /etc/fstab

I've see this done before where server that had files migrated to an NFS (or SMB,AFP,whatever) share, and the new share was just mounted on top of the old directory with the data still in it.  When the mount did not come back everyone just saw files from years back.

---

### Post by Krupski on 2008-10-24
> **Guigues67 said:**
> Hello,

I'm new on this forum and on Ubuntu Server too. 
Many thanks for those who will help me.

I've a problem on a Ubuntu Server 8.04.
I did a reboot yesterday evening (sudo reboot -now).
The server did its reboot.
But all data/files created since September 10th were lost

The server went back to the state of this date (configuration files, data, files, ...) 

Can anybody help me on this subject ?

Guy

The "-n" parameter for "reboot" means "don't sync before reboot or halt".

Maybe the "reboot -now" got interpreted as "reboot -n" (I don't want to check it here obviously!)

If you rebooted without doing a "sync", maybe that's where your data went.

-- Roger

---

### Post by Guigues67 on 2008-10-25
Thank you both for your answers.

StickyStyle : lost files are not store on a network drive. All data are stored on local hard drives.

Krupski : I'll test your solution. I've never heard about "sync" before. 

Guy

---

