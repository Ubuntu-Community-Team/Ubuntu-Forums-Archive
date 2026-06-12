---
title: "Basic server questions"
date: 2007-03-13
forum: Server Platforms
---

### Post by Talako on 2007-03-13
Yo guys,
My dad and I are planning to set up a media and file server for our home network, we want it to be stable, and I am getting used to using Ubuntu, so we are going to give it a go, but I have never set up a server before and I'm not sure wtf I'm doing.
1. How difficult is it to get the server to talk to Windows machines (I would also like to know how to get Ubuntu machines to talk to other Windows boxes).
2. Is there a TV tuner card natively supported by Ubuntu? Also, is there a DVR program that I can use, we want to try to set up a Tivo-type service on the server.
3. We have a few server utilities which only run in Windows, so I would like to virtualize a windows box, but I have not really played with VMWare-server yet, though I have a very basic idea of how it works. Any suggestions?
Any other suggestions/tips/advice would be greatly appreciated, I am a noob when it comes to servers, but I have an intermediate skill level with Ubuntu.
Thanks,
Talako

---

### Post by bandie on 2007-03-13
start here  [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
get that running then tackle/ post one issue at a time

---

### Post by rjfioravanti on 2007-03-13
1. it is easy to talk to windows machines over a network using 'samba', theres lots of information about samba on this forum and just google search i guess

2. i dont know anything about that

3. what do you need windows server utilities for? there may be good open source alternatives

---

### Post by jp33 on 2007-03-13
I have been doing application development for quite some time.  Regardless of what you are trying to accomplish, try sticking with open standards.  If you can stream media over http then it really won't matter if it is Windows, Linux, MAC, etc.  There is also a lot of good open source stuff out there now (hence why you are using Linux), much more than when I started more than 10 years ago.

---

### Post by djgrandmarquis on 2007-03-13
The Ubuntu Guide helped me set up Samba, it was really easy:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

I've heard good things about MythTV (Linux DVR), but I've never used it myself:
[http://www.mythtv.org/](http://www.mythtv.org/)

---

### Post by Talako on 2007-03-13
Thanks guys, I'll try setting the server up soon. I'm sure I'll be back.

---

### Post by nucklebone on 2007-03-13
Talaco,

If nothing else, I can offer this bit of encouragement:

On my box I have:

Apache web server
Proftp FTP server
SSHD SSH server
Unreal Tournament game server
GNUMP3 mp3/ogg server
GALLERY photo album
and as of about 5 minutes ago... Postfix email server

I suppose if I cared about television I could also get something going with the S-video out to my HD receiver.

And that same machine is pumping .flac files out to my home stereo so I can listen to high quality sound at home and streaming music on the road.

All of that took about 2 weeks to install, setup and tweak.

Good luck and don't be afraid to read a LOT of documentation.

---

