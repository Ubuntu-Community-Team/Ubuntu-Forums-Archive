---
title: "What media server app?"
date: 2008-04-14
forum: Server Platforms
---

### Post by blade22 on 2008-04-14
I have a spare PC lying around the house (P4 3ghz, 1gb ram, 80gb HDD, Decent PSU) and was planning on upgrading the hard drive and turning it into a 24/7 server to host all of my media files. I did a bit of googling and came up with names such as "Media Tomb", "Fuppes" and "DAAP".

It would have to stream files to any PC connected to my home network and, if possible, have accessible over the internet?

Does anyone have any suggestions? I would like ideally like to set it up and leave it in the corner of the room only connecting the monitor to add files every now and a gain (or even from a network computer would be better - requires VMWare??). 

I have a little (very little) linux knowledge as I have dabbled into the OS in the past (few months ago). So I know my way around, but i'm still scared of the terminal (although i'd learn to use it if it were necessary)

Am I looking at creating an FTP server?? Or using one of the above apps.

Your help would be MUCH APPRECIATED!! :)

---

### Post by Deathrend on 2008-04-14
I like Jinzora, I found it fairly fast, not sure if there's better or not, however.

I have something like, 4.5 TB of movies/Music (I hate CDs/DVD's, it's to easy to convert them for easy storage these days) which I serve with Jinzora.  It's a very nice web interface that is accessable via the web, however movies aren't the greatest steam.  You can imbead a player (Like VLC) however I haven't spent the time to do this yet.  I just connect my laptop via HDMI, works like a charm.

---

### Post by blade22 on 2008-04-15
Thanks for the input. Woud I be able to download the tracks from my server to the computer I listening to them on? Does it support remote writing of data to the server?

---

### Post by Deathrend on 2008-04-15
Yep, you can download them, stream, you can upload, it also supports adding directorys on to server (While remote, not using the install).  The server it runs on only has around 100Gb of hard drive space (4x36Gb SCSI RAID5).  So for the media portion, I use network mounts to my actual file/media server (Which is a Windows 2003 Server).

That's how I started atleast, I've since moved to iSCSI, which for media didn't make much of a diff, however file transfers are much much faster (Internally).  Before I leave in the morning I can grab two ore three movies, pack up my laptop, and leave.  Works very very well for what I wanted.

---

