---
title: "streaming from an HP Proliant dl360g4p"
date: 2010-03-04
forum: Server Platforms
---

### Post by gl0wst1ckn1nja on 2010-03-04
i currently have my ftp server running off of my hp dl360 
 ubuntu 9.10 server

i cannot seem to stream anything.

i can use WINS and mount the share and then watch videos over my LAN like that but i want to stream my media over the internet, i already have a domain and NAT 100% set up with port forwarding.

The snag im hitting is i cannot seem to get streaming to work over the net.

the stats on the DL360g4p (1u rackmount) are as follows
1x Xeon 3.08GHz - 512MB cache
2 GB RAM
2x 300GB SCSI @ 10k RPM in raid0.
gigabit NIC
ubuntu 9.10 server


all web(http/ssh) traffic is forwarded to seperate ubuntu server VM running ontop of ESXi on a different 2u HP proliant dl380g3

all ftp/smb traffic is forwarded to the 1u dl360



I have tried vlc -I http (port 8080 redirected to ftpserver) under a detatched screen window and it failed to initialize video driver.

I have an entire Directory that i would like to make available to stream.

Thanks in advance for your help

---

### Post by tgalati4 on 2010-03-04
Are you running icecast?

---

### Post by gl0wst1ckn1nja on 2010-03-04
> **tgalati4 said:**
> Are you running icecast?

icecast is only for music isnt it?

i have video i want to stream too

---

### Post by gl0wst1ckn1nja on 2010-03-05
does anyone know why i am getting a video driver error.

or if there is a way to stream files in raw format rather than having the server render the stream

---

### Post by ephmanjmm on 2010-03-05
What software are you using for streaming?  I have used wowza in the past with good results.  ftp is not designed to stream media nor is smb to the best of my knowledge.

---

### Post by gl0wst1ckn1nja on 2010-03-05
> **ephmanjmm said:**
> What software are you using for streaming?  I have used wowza in the past with good results.  ftp is not designed to stream media nor is smb to the best of my knowledge.

at the moment im only streaming to my LAN and right now i use ftp and smb to mount the servers share and then open the shared file with VLC (i also have ushare for my xbox). once i experiment with some streaming software that yields results im happy with i will let the server touch the internet

---

### Post by gl0wst1ckn1nja on 2010-03-05
also i have .avi as my current format.

---

### Post by ephmanjmm on 2010-03-07
At the moment, it sounds like you are not streaming the media.  Check out this:
[http://en.wikipedia.org/wiki/Streaming_media](http://en.wikipedia.org/wiki/Streaming_media)

---

