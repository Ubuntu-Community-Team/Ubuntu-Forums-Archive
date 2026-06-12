---
title: "HTPC Or File Server?"
date: 2010-05-23
forum: Server Platforms
---

### Post by AoDZelda on 2010-05-23
I have been toying with some ideas in my head about creating a Ubuntu Server based on the new i3 processors and H55 chipsets.

I was thinking of building two units. One being a file/backup server and the other a HTPC. The HTPC to playback files (video, pictures) wouldn't have them stored locally but on a network drive.

Is this efficient or pointless? (Worrying about bandwidth)The reason I was thinking this was using Mythbuntu on the HTPC, and on the file server Ubuntu 8.04 or 10.04. 

As for the file server I have some pretty good ideas as to what I would like it to do. I don't want to "overload" the server doing multiple things. 

HTPC
Proc: i3-540
H55 Chipset
2GB RAM

File Server
Proc: i3-540
H55 Chipset
4GB + RAM

In response I have specific questions about the file server functions and capabilities. However at this point I'm wondering if I should have two different devices or not.

Thanks in advance!

---

### Post by CharlesA on 2010-05-23
There is no way just streaming files would overload a server with those specs.

Mine is running a dual core CPU and does fine streaming dvds.

---

### Post by AoDZelda on 2010-05-23
Well I have an old P4 2.6, 2GB RAM board that's just sitting around. I was thinking I could use that for the HTPC even. I want to have that eventually do all the transcoding video in 480/720p video (DVD copies primarily) which would store the finalized file on the "netshared drive" or it could do that locally with say 500GB hdd. I'm reluctant using the P4 for anything since the power it draws and its old technology. I'm better off getting like a low-end dual core or amd64 proc.

---

### Post by AoDZelda on 2010-05-23
Am I thinking right when I say for things being done on the LAN you use SSH. For things outside of the LAN(WAN) you would use VPN?

---

### Post by CharlesA on 2010-05-23
You can just SSH in from outside the LAN as well, but you would need to have ports forwarded on the router.

---

### Post by AoDZelda on 2010-05-23
Oh ok. OpenSSH is the better application to do this?

I may hit up the irc:// #ubuntu-server for all the other questions I want help answering. 

Thanks for the assistance.

---

