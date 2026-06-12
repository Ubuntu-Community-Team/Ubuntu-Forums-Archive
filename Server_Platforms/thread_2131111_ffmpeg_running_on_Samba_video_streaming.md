---
title: "ffmpeg running on Samba video streaming"
date: 2013-03-31
forum: Server Platforms
---

### Post by jpaytoncfd on 2013-03-31
Every time I stream a video to my XBMC install over a samba share from Ubuntu Server 12.10 ffmpeg is running indicating the file I am watching several times looking at htop. does this mean ffmpeg is streaming the video? Could I transcode video over samba depending on the host using the video? It would be cool to use my VPN on my phone or laptop to stream outside my network. However doing that over a 1000kb/s uplink is taxing at 1080P with 7.1AAC

At the same time I want to make a PHP site to serve up my media using ffmpeg. I have the XBMC database in mySQL. I havent done much research yet but I figured if someone knows some good readings on the subject I'd like to know. Primarly I want to know about the Samba Streaming though.

Thanks,
Joe

---

### Post by rubylaser on 2013-03-31
I use XBMC on all of my front ends, but for remote steaming, the plexmediaserver works very well.

---

### Post by jpaytoncfd on 2013-04-14
I did start using that but thats not the issue. I have ffmpeg showing on htop working on the video I am streaming over a local samba share

---

