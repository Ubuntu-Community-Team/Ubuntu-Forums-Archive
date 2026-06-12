---
title: "home file sharing server with Ubuntu"
date: 2013-03-19
forum: Server Platforms
---

### Post by ReijiK on 2013-03-19
Hello everyone,

I am new here and this is my first post. I've been searching but can't find an answer to my problem.

I want to set a new wireless server at home with file sharing capabilities. I am going to get a cheap desktop so I can install ubuntu to achieve it.

Basically we have around 4 computers at home, laptops with Windows 7 and Windows 8, a Mac running the latest OSX, also we have an android and an iphone that we would like to be able to share files as well.

What programs and protocols do I need to have in all those systems to be able to share the files? I have an external 2TB hard drive that I would like to connect to that server and be able to share the movies and pictures on that drive with the rest of the house, but also be able to have personal folders for each system that no one but they and the admin can access.

Finally, it is possible to have the server on at all times but without the need to have a monitor, mouse and keyboard connected to it? You know, if I want to change something I could connect from my laptop to the server and have the gui on my laptop to do the changes.

I am practically a newbie in this, but I can follow steps and also just need you to point me in the right direction. Reading a 14 pages software manual book is no problem for me.

Thank you in advanced and sorry for the long read/requirements post.

---

### Post by grunge09 on 2013-03-19
You can start here:

[http://www.howtoforge.com/creating-a-home-media-and-file-server-with-ubuntu](http://www.howtoforge.com/creating-a-home-media-and-file-server-with-ubuntu)

or ...

[http://www.havetheknowhow.com/default.htm](http://www.havetheknowhow.com/default.htm)

NFS may be the simple method for file sharing, Samba is more in depth to setup but using wireless server might be the better way to go.  

Sinze its wireless make sure the wireless connection is WEP or WPA protected.  

See Here:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by darkod on 2013-03-19
Couple of things I would consider.
1. Do you plan to run data/media from the ext hdd temporarily or permanently? I'm not sure it will be fast enough pulling data over usb and then sharing it through wi-fi, especially HD content for example. I would strongly consider having all data on internal hdds in the server machine.

2. Yes, it can run without monitor, keyboard, mouse, that's how most home servers run. It's called headless. In most cases you would do administration using SSH session from a computer on the same home network (LAN), but by default the SSH session is command line only. Not sure if you would prefer GUI tools, there are some around but leaving the server with no GUI installed and administering over SSH is welcomed. Besides, once you have it set up there is not much need to administer it. :)

3. Do you plan a wireless adapter for the server too? I assume you already have a wi-fi internet router with wired ports, so you can simply plug the server with a network cable into it, and all devices in your home wi-fi network can access it since it will be in the same network. That's how I've got mine connected, into the router, no separate wi-fi adapter.

4. Are you thinking about any kind of raid protection against disk failure? With all data on single disk, if it fails everything is gone. In most cases you would start with 2 disk raid1 array (mirror). Other options are 3 disk raid5 or even 4 disk raid6/raid5.

---

### Post by thnewguy on 2013-03-19
For easy compatibility between the different operating systems you will probably want to go with Samba shares on the server.

---

### Post by SeijiSensei on 2013-03-19
Use NFS for *nix systems like Linux and OSX and Samba for Windows.  I run both on servers to share out the users' home directories to both types of clients.

---

### Post by Moose on 2013-03-19
I am not very good at in-home file sharing servers. But as far as editing the options via your laptop, your best bet would be to use teamviewer. Sorry I couldn't help further.

---

### Post by ranger12 on 2013-03-20
Same here on my file server. I use nfs for linux and samba for windows for dishing out a user's home directory. I have not had any issues with it so far. As far as a remote connection, I remotely connect to my server from my ubuntu client with ssh for doing administration on the server. I just use the plain ol' terminal to do it. You could set up the same kind of connection with Windows 7 or 8. I think when I had a win xp pro box on my network - I think I used Putty.

---

