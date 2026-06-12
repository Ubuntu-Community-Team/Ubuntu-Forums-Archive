---
title: "questions about bandwidth managment, hardware and apps w/ Ubuntu media server build."
date: 2010-01-23
forum: Server Platforms
---

### Post by nelsonm on 2010-01-23
Hi all,

I want to build a Ubuntu media server to serve up multiple streams of Standard and High Def Videos throughout my home. I will be using some windows laptops for viewing the streaming content as well as some dedicated windows (maybe ubuntu) pc's used as streaming clients with DVI/HDMI graphics cards connected to HDTV's via DVI or HDMI connections.

After reviewing posts on this forum, it appears that Ubuntu Server...
1. does not include all the apps required for streaming
2. there is no mention of whether Ubuntu Server provides bandwidth management. It would appear that bandwidth management is required for handling multiple streams at once.
3. what else, hardware/software, is required to insure consistent multiple simultaneous streams throughout a home?
4. is more than one nic card required required on the server?

Also...
1. many posts say that an old P3/P4 will do since streaming or file serving does not require much processor power. Is this true? I would think this notion would get blown out of the water if format conversion is needed for streaming.
2. How many videos can you simultaneously stream from one server that has a gigabit nic card router and switch.

The most i know is that you need...
0. a gui for ubuntu server.
1. samba for file sharing between windows clients and the ubuntu server.
2. a media player like vlc on the clients.
3. a gigabit nic on the server and clients, and a gigabit router and/or switch.
4. anything else?

---

### Post by nelsonm on 2010-01-23
No responses, Did i answer my own questions?

---

### Post by The Real Dave on 2010-01-24
Seems you have answered your own questions. You won't need more than one NIC for a standard media sever, though, if you were making a network gateway or similar, you would. As for power, that depends, if the server has to convert the file, no, a PIII won't be enough. If not, a PIII, preferably PIV will be plenty. As for whether it will need to or not, I can't say. I presume that if the client can open the filetype locally it will open it remotely.

That being said, my [servers]("http://linuxexpresso.wordpress.com/hardware") only stream music files, unless you count sharing video files through NFS to other computers ;)

---

### Post by nelsonm on 2010-01-24
thanks for responding.

What do you think of using some of these new digital media receivers, like the Acoustic Research DMP3000 or D-Link MediaLounge DSM-520 or netgear EVA2000 or EVA8000, in stead of having a desktop attached to the HDTV and network?

I think the advantage of purchasing one of these devices is that it comes with a built in interface and remote control so you don't have to use a mouse and keyboard as you would with a desktop attached to the network and HDTV.

What you do all think?

---

