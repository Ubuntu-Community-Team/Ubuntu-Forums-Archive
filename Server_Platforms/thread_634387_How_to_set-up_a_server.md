---
title: "How to set-up a server?"
date: 2007-12-07
forum: Server Platforms
---

### Post by jseiser on 2007-12-07
I work on computers at a computer repair place :) and a customer didnt want their old set-up because the HD went bad so we built them a new one.  So i have this small set-up, and an old harddrive and wanted to try and make it a media server of sorts for my 2 computers.

Mine is linux, and my girlfriends is windows :( so i need to set-up access from both machines.  
I want to use rtorrent and have it download all my torrents to this box.
I would then want to be able to tell ncmpc to look there for my music, and have my girlfriends foobar look their for the music.  Also having vlc play a movie off of it would be ideal.  I want all administration to be through the command line from my computer.

To install can i control it from my machine or would i need to hook a monitor up to it for the installation at least?  I imagine i need SAMBA/NFS ( though i dont know how to use them) also ssh.  I would also have to give the machine a static IP as well as my machine a static IP so i can ssh from one to the other.  I dont use ubuntu, or gnome or anything, so i would need a command line way of doi

I have searched around and havent found anything real helpful.  Any tips or walk through available?
Thank you :)

---

### Post by p_quarles on 2007-12-07
This link has the instructions for setting up the basic Samba file server and users:
[http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend)

Samba will allow just about any modern computer OS to access files via the server's shared folders. If you simply want to be able to have media files available from this server, that's really all you need to do.

The installation process will require you to hook up a monitor to the box. Once you're done setting up, though, you can administer it entirely via SSH. That part is super easy:
```
sudo apt-get install opensssh-server
```
You can use the built-in SSH client in Ubuntu to access it. From Windows, you'll need to use PuTTY, which is available for free. 

For static IP, I'm gonna be lazy and point to another post where I gave instructions for that:
[http://ubuntuforums.org/showpost.php?p=3893680&postcount=33](http://ubuntuforums.org/showpost.php?p=3893680&postcount=33)
Look at the rest of that thread for context. 

Good luck.

---

### Post by HermanAB on 2007-12-07
Actually, looking at all the threads with people having difficulty setting up Samba, I would suggest that you rather install NFS client on the Windows machine and run NFS server on Linux.  NFS is much easier to set up - only about 3 lines, vs hundreds of things that can go wrong with Samba.

Google for "Windows NFS" and a Microsoft guide will be right at the top of the list.

Cheers,

Herman

---

### Post by jseiser on 2007-12-07
thank you, i can handle the static IP and ssh, just wasn't sure about getting both computers to be able to access the files.  Thanks for the replies :)

---

### Post by kencoe on 2007-12-11
> **p_quarles said:**
> ```
sudo apt-get install opensssh-server
```
Small correction for new users' benefit... the correct command to install ssh server should be
```
sudo apt-get install openssh-server
```
No offense intended...

---

