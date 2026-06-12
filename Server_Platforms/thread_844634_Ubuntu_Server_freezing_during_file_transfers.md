---
title: "Ubuntu Server freezing during file transfers"
date: 2008-06-29
forum: Server Platforms
---

### Post by cknapp12 on 2008-06-29
I use Ubuntu server on a machine I put together a while ago. I don't really remember the exact specs in there. I think it's an AMD running around 1400Mhz, with probably around 512 MB of RAM. It's got 4 EIDE hard drives totalling about 750 GB. It's running the LAMP server, and I've got Samba and some kind of ntfs handler installed so I can use it on a Windows network. I use it to store my MP3s and my recorded TV shows after they've been compressed. 

I used to just use a networked folder on the server as the output directory for the video compressor, and it worked just fine, but a little while ago I got a new router, and then the compression jobs started failing every time, so I had to set the output folder to a local one and just move the compressed files over to the server when I got around to it, but even that barely works. The files are about 700 MB apiece, and if I only move one at a time, it's usually okay, but if I try to move two or more in a row, the Windows file transfer will slow down and the estimated time remaining will start going up again, and then it will fail, and I won't be able to access the networked drive again and I'll have to restart the server (sometimes I can ssh in to restart it, but sometimes that doesn't respond and I have to hit the restart button). I also can't sync my iPod anymore because my iTunes music directory is on the server, and it also freezes up the server.

At first I thought the problem might be that the new router can support gigabit speeds, and my desktop system has a gigabit card but the server does not. I thought maybe it was sending in data too fast for the server to handle, so I tried setting the network card settings on the desktop to 10 mbps half duplex and stuff like that, and I think that made it a little better, but it still failed most of the time. Now I'm wondering whether it might be some kind of DHCP problem, if it's got to be something to do with the router...

Does anyone have any idea of how I might fix this, or what other relevant information might be needed to make such a diagnosis (and what I need to type to get that information)?

Thanks.

---

