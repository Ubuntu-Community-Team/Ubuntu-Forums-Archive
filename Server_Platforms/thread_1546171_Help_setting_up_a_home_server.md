---
title: "Help setting up a home server"
date: 2010-08-04
forum: Server Platforms
---

### Post by dragao-azul on 2010-08-04
Hey,

I'm thinking of creating a small home media/file server.

The idea is to have the pc connected to the TV (so i'll use the "regular" ubuntu).

I was able so set up both ssh, vnc (trough ssh) and ftp so I can send and receive files remotely.

But now I'm looking for some help to set up the home sharing.

So:
I'd like to have some folders (or entire drives) shared so that all PC's could access them in a reliable way (I have both Mac's and PC's running windows). I've read about NFS, samba and NAS (this one is a different concept from what I understood).

Which of these is the best option?
Samba works native on windows but from what I gathered is slower, I don't know if it is possible to set up a NAS server in ubuntu and NFS needs clients at least for windows (don't know about mac's).

How can I set this up?

Thz in advance.
;)

---

### Post by tyleruk on 2010-08-05
Personally I have always used samba for sharing movies just because it’s so compatible. It’s always been fast enough for me, even when several people are watching different films at once.

An extensive tutorial can be found at: [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by YesWeCan on 2010-08-05
[QUOTE=dragao-azul]
I'd like to have some folders (or entire drives) shared so that all PC's could access them in a reliable way (I have both Mac's and PC's running windows). I've read about NFS, samba and NAS (this one is a different concept from what I understood).
[/QUOTE]
networking protocols:
NFS = Network File System (derived from unix)
SMB = Server Message Block, aka CIFS = Common Internet File System (MS networking)
FTP = File Transfer Protocol and SFTP = Secure FTP
AFP = Apple Filing Protocol

network appliance:
NAS = Network Attached Storage (a network appliance for storing data)

OSX is another unix derivative like linux and I believe Mac's can connect using SMB, NFS, FTP, Webdav and AFP. Windows will be more restricted in what it is able to connect to but it does SMB, obviously. Putty lets you do command line SFTP from Windows and Filezilla provides a GUI, but neither are as simple to use as SMB.

---

### Post by LightningCrash on 2010-08-05
There are also NFS clients for Windows but they're not really straightforward IIRC.

XBOXes can speak SMB though.

---

### Post by dragao-azul on 2010-08-05
I guess I'll use SMB with Samba then. If it works fine, it's easier to configure, and is compatible with all OS's I use then it's a good option.

Thz

;)

---

### Post by Iowan on 2010-08-05
The [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") might have some more ideas for you...

---

### Post by pipemartinm on 2010-08-05
I have SMB and FTP on my media pc. Haven't found anything that can't use one of those.

---

### Post by LightningCrash on 2010-08-07
uShare does uPNP/DLNA on Ubuntu but I have found that some combination of the XBOX1's XBMC + uShare doesn't update the library properly when changes were made.

So I stick to Samba.

---

### Post by wigg on 2010-08-07
If your going to do something like DLNA....  Just use Media Tomb.  It works amazingly.  My home server runs on a 1.2 ghz amd and it can easily transcode media to any device that can see it uPNP on the network without any hit to other server functions it is performing.  You can even edit where Media Tomb looks for media from a web portal on your Windows or Mac boxes.  One thing I wouldn't recommend is trying to transcode anything over a samba share.  Media Tomb exploded when I did that and I had to reinstall it, as well manually remove the mysql database it creates.

---

