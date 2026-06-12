---
title: "Creating a Home Server/Media Center"
date: 2008-11-11
forum: Server Platforms
---

### Post by dontocsata on 2008-11-11
I'm trying to create a home server with Media Center abilities.  I'm a student, so via Microsoft's Dreamspark & my school I have (free) access to Windows Server 2008 and Windows Home Server.  So if someone thinks these are a better option, I can use those.

However, I use Ubuntu Desktop for one of my PCs, and I like it a lot (plus, WHS probably doesn't support Linux too well...)  So I'm thinking of using Ubuntu Server.

My LAN will be this: 1 Server, 3-4 other PCs (running Ubuntu, XP, Vista, & OSX)

The server specs easily handle any server OS.
P4 @ 3ghz HT
1024 mb RAM
60 gb (IDE) - For server installation, so ext3 (I guess?)
160 gig (SATA) - NTFS
750 gig (SATA) - NTFS
1024 gig (SATA) - NTFS

The Filesystems aren't set in stone, but I'd rather not install software on my Windows computers to read ext3.  I need expandability with HDD space.


I need to be able to setup permissions.  Like, block certain users from accessing specific folders, etc.


I need it to work as a media hub.  It will store all of music & videos, and stream them over the LAN.  It must also be able to connect to a TV (via S-video) and play videos on this TV.  I also would like the option of playing DVDs & using a TV Tuner card to watch/record TV.


It must also run a public & private website (using Apache, PHP, I guess).  And therefore, an FTP would be nice.


I also need remote access.  To both manage the server and access files/media.  


Not Necessary, but nice: Run VMWare Server, auto-backup my PCs (WHS can do this) (either specific folders or the entire PC)


Is it possible to setup Ubuntu Server to do all of this (I know it must be!).  What packages & software would be required?  Names/websites for research would be very helpful.


I'm not totally adverse using command-line for the server.  But since I need it to be a media center, I'll need some sort of GUI.


Please post any suggestions or information!  If you need something clarified, let me know.

---

### Post by loell on 2008-11-11
the answer is almost always **mythbuntu** :)

---

