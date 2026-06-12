---
title: "Ubuntu Cluster"
date: 2016-12-30
forum: Server Platforms
---

### Post by lars17 on 2016-12-30
Hi.. 

Question: 

**1:** Clusters. I have a low end CPU on my server. and i resently aquired a Laptop With a pretty hefty CPU and a broken LCD. so i've been Reading around about clustering. Can i setup my 2 pcs in a cluster so they can share CPU and RAM. Reason is that i have Plex Media Server and some of my media is now in HEVC/H265, and for now a lot of hardware doesn't support HEVC codec so the Server have to Transcode the media into H264 so the player can play it. 

**2:** if I can, can somone help me into setting up or show me how. I just need it to share CPU & RAM. nothing else. All Storage is on my main server.

---

### Post by cariboo on 2016-12-30
Try [serviio]("http://serviio.org/"), running it right now, and there is virtually no load on my older server:

```
inxi
CPU~Dual core Pentium E5400 (-MCP-) speed/max~2003/2700 MHz Kernel~4.4.0-57-generic x86_64 Up~9 days Mem~711.9/1990.7MB HDD~3960.8GB(65.4% used) Procs~224 Client~Shell inxi~2.2.35

```

I'm also running:

[LIST]
[*]Calibre Server
[*]Mediawiki
[*]Nextcloud
[*]phpmyadmin
[/LIST]

---

### Post by #&amp;thj^% on 2016-12-30
> **cariboo said:**
> Try [serviio]("http://serviio.org/"), running it right now, and there is virtually no load on my older server:

```
inxi
CPU~Dual core Pentium E5400 (-MCP-) speed/max~2003/2700 MHz Kernel~4.4.0-57-generic x86_64 Up~9 days Mem~711.9/1990.7MB HDD~3960.8GB(65.4% used) Procs~224 Client~Shell inxi~2.2.35

```

I'm also running:

[LIST]
[*]Calibre Server 
[*]Mediawiki 
[*]Nextcloud 
[*]phpmyadmin 
[/LIST]


Sorry for the intrusion here But Thanks for this...What a Great Idea!:D

---

### Post by lars17 on 2016-12-31
Checked out ```
http://serviio.org/features
``` and this is a meida center server. and this is not what i'm looking for. I run Plex media server on 10 diffrent systems. and i would like to free up my Gaming PC so that i can run PMS on my Ubuntu server. but the server is to weak for transcoding HEVC/h265.

---

