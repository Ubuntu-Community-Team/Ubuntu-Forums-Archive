---
title: "System Hang/Network Crash when transferring large files (2GB+) PC to PC"
date: 2017-05-14
forum: Server Platforms
---

### Post by ddubief on 2017-05-14
Hey folks, 

Recently built up an HP DL180SE for a pretty overkill home NAS running Emby. This currently runs on a 60GB SSD, on the host ICH10R chip, and a 6drive ZRAID2 pool on the 6 3TB drives. I have the pools up running successfully, server runs without a hitch, except for when I transfer into that pool via SAMBA share. Transferring video files from an existing Server2008 box over my network it gets at most about 20% through and hangs for about 3~4 minutes. Just disconnects any SSH session, becomes unresponsive and regardless of what I do will not allow me to copy/cut/the files over. 

Pretty at wits end with this, as I have roughly 6TB to transfer, and no way to simply install the drive with files into the server (existing Raid card is required) I have tried a few things thinking network related, and feel free to move this post if in the wrong section. 

I have tried:

Network switch
AP Bridge
New NIC
Changes to VM.Dirty_Ratio (5,50,10,80)
Changes to VM.Dirty_Background (5,50,10,80)

Memory = 60GB (16x4GB)
CPU = 2x 4C Xeons

system typically runs at 1.5% load, so I cannot assume there is a bottleneck there. For the 20% of transfer though it is full gigabit saturation, then stops.

Any thoughts? I am primarily windows, this was my venture into Linux to get more reliability (Which it is, but this problem is difficult to troubleshoot)

Thanks in advance!

---

### Post by wildmanne39 on 2017-05-14
*Thread moved to **Server Platforms**.*

---

### Post by steven60 on 2017-05-14
> **ddubief said:**
> Hey folks, 

Recently built up an HP DL180SE for a pretty overkill home NAS running Emby. This currently runs on a 60GB SSD, on the host ICH10R chip, and a 6drive ZRAID2 pool on the 6 3TB drives. I have the pools up running successfully, server runs without a hitch, except for when I transfer into that pool via SAMBA share. Transferring video files from an existing Server2008 box over my network it gets at most about 20% through and hangs for about 3~4 minutes. Just disconnects any SSH session, becomes unresponsive and regardless of what I do will not allow me to copy/cut/the files over. 

Pretty at wits end with this, as I have roughly 6TB to transfer, and no way to simply install the drive with files into the server (existing Raid card is required) I have tried a few things thinking network related, and feel free to move this post if in the wrong section. 

I have tried:

Network switch
AP Bridge
New NIC
Changes to VM.Dirty_Ratio (5,50,10,80)
Changes to VM.Dirty_Background (5,50,10,80)

Memory = 60GB (16x4GB)
CPU = 2x 4C Xeons

system typically runs at 1.5% load, so I cannot assume there is a bottleneck there. For the 20% of transfer though it is full gigabit saturation, then stops.

Any thoughts? I am primarily windows, this was my venture into Linux to get more reliability (Which it is, but this problem is difficult to troubleshoot)

Thanks in advance!

ok been a while since i ran a server.
but i did remember having a similar problem.
this helped me...
hope it helps you too.

[https://askubuntu.com/questions/279812/file-copy-freezing-with-large-network-copies](https://askubuntu.com/questions/279812/file-copy-freezing-with-large-network-copies)

---

### Post by ddubief on 2017-05-14
I'll give that a shot. Thanks!

---

### Post by darkod on 2017-05-15
Is this problem relevant to samba only? Have you tried something like scp (from windows you can use WinSCP) or it has to be strictily samba shares?

How do you open the share, with \\server-IP?

---

### Post by ddubief on 2017-05-15
The above attempt with using the ionice or rsync still result in the disconnect happening. Don't believe its a Samba specific issue. I can initiate the transfer from either side, either on the Windows Server I can open the SMB Share from the Ubuntu pool, and try cut/copy using the explorer windows. Or vise versa on the Ubuntu box, using cp as I have mounted the Windows share using fstab to /poolmnt. transferring in any case doesn't seem to complete but will kick me out of any Remote session, and become unresponsive on the network.

I can try scp next. Just looking for a simple means of migrating data, and sadly the simple drag and drop method isn't working.

Outside of this, I can read no problem from the Ubuntu instance, across multiple devices simultaneously.

---

### Post by ddubief on 2017-05-15
Let me try an FTP share, one of my counterparts here mentioned an issue he also ran into, and referred me to setup an FTP server on the windows box and perform the transfers that way. I'll give that a shot, otherwise the SCP method will be next.

---

### Post by ddubief on 2017-05-15
Update** FTP server/client (both methods) WINS>UBUN and UBUN>WINS failed in the same way.

---

### Post by ddubief on 2017-05-15
One thing I have noticed, that when using glances, prior to this issue, my zpool was using roughly 50% of my memory at any time, in use or not. Now I am only showing 1.7% usage and this issue. Should I be looking at the raid?

---

### Post by darkod on 2017-05-15
Well, the ZFS is something you should definitely check out. I haven't worked much with it but I was under the impression it needs significant amount of ram. So if it's using only 2% now, that might be a sign of something. But I don't know what unfortunately...

PS. It's little bit deprecated these days but you can also try iscsi from the NAS to the windows client (the NAS is the iscsi target and the windows is your initiator).

---

### Post by ddubief on 2017-05-15
Appreciate it! I built this specifically for ZFS, has 60+ GB of ECC RAM. So prior I was not concerned that 30GB was occupied by ZFS system. Now, I'm showing very minimal use, and didn't think about that before. I'll if I can dig up something in regards to that.

---

### Post by ddubief on 2017-05-15
sadly even transferring files via external usb causes a hang, so i think i can rule out network side of things.

---

