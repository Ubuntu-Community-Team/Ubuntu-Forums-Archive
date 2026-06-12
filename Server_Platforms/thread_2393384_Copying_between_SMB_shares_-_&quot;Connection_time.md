---
title: "Copying between SMB shares - &quot;Connection timed out&quot;"
date: 2018-06-02
forum: Server Platforms
---

### Post by nraygun on 2018-06-02
I have a server running Ubuntu Server 18.04 and a Windows 10 with SMB1/2/3 enabled. I tried using only SMB1 and get the same results when using SMB2/3.

When I copy a group of large multi-gigabyte files, I get an error that says, "Connection timed out", "Do you want to skip it?" and the options are Retry, Yes to all, Yes, and Cancel.

I'm doing the copy inside of Thunar. I have the min smb set to 2 and max smb set to 3 in the smb.conf file in /etc/samba/smb.conf.

Any ideas?

---

### Post by wildmanne39 on 2018-06-02
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by nraygun on 2018-06-08
Any ideas now that it's in the right forum area?

---

### Post by wildmanne39 on 2018-06-08
If you do not receive a reply you can bump your thread once every twelve hours to keep it in view.

---

### Post by darkod on 2018-06-08
You really didn't give much data.

1. Is this over a wired connection or wifi?

2. Thunar seems to be XFCE GUI file manager. Ubuntu Server has no GUI. Did you add GUI environments?

3. Have you tried anything else except SMB? That is really among the worst protocols. How about NFS or iSCSI? Do hey have higher and more stable speed?

---

### Post by nraygun on 2018-06-08
1. The machines involved are wired.
2. I'm using Thunar to connect to both servers. The Ubuntu server is headless and Windows is, well, Windows.
3. I have not tried anything else since the target is Windows which I think is only SMB.

---

### Post by darkod on 2018-06-09
So you have a third machine with Thunar and use that to issue the copy command? In that case that machine will be the bottleneck. I'm not sure if you are aware, but if you issue the copy command like that all data has to pass through that third machine. Which means it will be receiving much data from source server and sending much data to destination server.

If the target is windows, why not log into the windows and copy directly from the ubuntu server?

By the way Windows 10 does have iSCSI Initiator integrated.
And you can add NFS shares to it too, look it up on google.
Plus you can even use something like WinSCP in windows to directly copy files from linux to windows.

---

### Post by nraygun on 2018-06-10
Thanks darkod.
Yep, I knew the bottleneck thing.
I supposed I could remote into the Windows box and initiate the copy directly.
Not sure I want to use other protocols on the Windows box since it serves up stuff to the rest of the house like video to the PS3 via Serviio. Not sure those systems know about iSCSI or NFS. I suppose I could try it if it means better performances/stability.

---

