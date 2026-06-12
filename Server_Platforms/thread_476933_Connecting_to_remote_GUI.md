---
title: "Connecting to remote GUI"
date: 2007-06-17
forum: Server Platforms
---

### Post by Quickjelly on 2007-06-17
Hi. I need help.

It's like this. I have a ubuntu 6.06 server sitting in france. On this server I need to set up LAMP and Torrentflux.

Now since torrentflux is GUI based and I feel more comfortable using a GUI I wanted to set up a desktop environtment on the server before installing everything else.

Some people told me that I could install packages like xubuntu-desktop and ubuntu-desktop on the server, which I have done. I did this via ssh on windows vista, which I use at home (vista/feisty dual boot).

OK, so I got it all set up and started the x server from my ssh command prompt (using putty, a ssh tool for windows). The I realised, I couldn't run a GUI over a ssh command prompt. I was/am a little tired so I haden't thought of this before.

So what I need to know is how to connect from windows to my remote xubuntu-desktop GUI thingy. Do I have to do this with the remote desktop function in ubuntu?

I've been hearing about samba and I can't say I know much about it, is samba capable of connectting me to my remote desktop?

Huge thanks in advance.

---

### Post by Reugen on 2007-06-17
You need to run a vnc server on the remote computer and a vnc client your windows box.  Samba is used for fileshareing and such and as far i I know doesn't have anything to do wth remote desktop software.  You can get vncserer through the apt repository sudo atitude install vncserver if your using ssh.  Then you need a vnc client on windows.  Ubuntu may have a vnc  server set up by default, but you'd need a vnc client to use it i believe(but not the other way around) [http://www.realvnc.com/](http://www.realvnc.com/) has a free vnc server you should be able to use.
Hope that helps.

---

### Post by Quickjelly on 2007-06-17
Yeah man, it helped. Now I can finally go to sleep. :)

Big Thanks to you.

---

