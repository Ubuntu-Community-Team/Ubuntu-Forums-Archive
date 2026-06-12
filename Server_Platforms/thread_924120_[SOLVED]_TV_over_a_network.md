---
title: "[SOLVED] TV over a network"
date: 2008-09-19
forum: Server Platforms
---

### Post by Pro-reason on 2008-09-19
I have access to two Ubuntu machines.  One has an Asus MyCinema U3000 Mini USB TV tuner attached.  It is possible to view the signal from the device (which shows up at /dev/dvb) by using the me-tv application (available in the repos).

I would like to be able to use me-tv to watch television on my main computer too.

Is there any way I can get access to /dev/dvb from the other machine?

I've tried logging on to the remote machine by using “ssh -X”, but that has the effect of giving me the X app, but playing the sound on the remote machine.

---

### Post by Pro-reason on 2008-09-19
I've tried mounting /dev/dvb from one machine to the other, by using NFS.  However, it didn't work.  I get “*exportfs: Warning: /dev/dvb requires fsid= for NFS export*”.

---

### Post by cariboo on 2008-09-20
You should be able to use vlc or vls to stream video over a network, They are both available in the repositories.

Jim

---

### Post by eldragon on 2008-09-20
or just be a bit more patient and install mythtv. which does that and more.....

---

### Post by Pro-reason on 2008-09-20
OK, so you're saying that I can open a media player on the remote machine and make it send a stream over the network.

I'd prefer not to have to start any graphical app.  Perhaps there is a way to send a stream via the command line.

There is also the problem that I'd have to be at least able to view the TV via that media player in the first place.  I have so far only managed to get a TV signal via me-tv.  VLC doesn't work out of the box, and there is no hint as to what options might be necessary to make it work.  Totem has no ability to find channels.  MythTV is a monstrosity that takes over the screen with a garish, unnecessary, fullscreen set-up process which fails, and doesn't even start up a standard application with a help menu, etc.

---

### Post by puppywhacker on 2008-09-20
vlc is both a graphical and a commandline tool. It works very well for streaming both sending and receiving streams. but I think it's worth reading it's documentation although I don't consider the advanced features of vlc "out-of-the-box"

[vlc streaming dvb]("http://www.videolan.org/doc/videolan-howto/en/ch06.html")

---

### Post by kustomjs on 2008-09-20
well I would like get some information on how to setup IPTV using my cable so my fiance and watch my cable over the internet because she lives outside in the county and they cant get cable and only thing she have is regular tv so I just wanted to share my cable with my fiance

---

### Post by Dr Small on 2008-09-20
You can either use VLC from the command line and start a stream from the TV device, or get SSHFS and mount the device on the remote machine and then open VLC and mount the directory.

---

### Post by Pro-reason on 2008-09-28
In the end, the simplest solution was to stream all audio from one computer to the other by using PulseAudio.  See [guide]("http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio").

In the future, I may try again at the other methods.

---

### Post by braice on 2008-10-18
Hello

You can also use [mumudvb]("http://mumudvb.braice.net")

---

