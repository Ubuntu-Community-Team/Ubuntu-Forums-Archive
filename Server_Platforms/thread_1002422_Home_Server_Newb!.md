---
title: "Home Server Newb!"
date: 2008-12-05
forum: Server Platforms
---

### Post by norman_069 on 2008-12-05
Hello

I have been wanting to set up a home server but I am very confused on a few things.  First of all I have ubuntu 8.10 installed on my laptop and desktop and I have been reading that I should un-install the normal 8.10 and use the server version.  is this necessary? Also I was looking for a nice easy set up on-line somewhere but couldn't find anything so any help or web pages or books would be great. Also I was wondering what is the deal with the static ip address.  Do i need on to access the server from outside my home. Any help or links on how to get this started would be great.

thanks

---

### Post by hictio on 2008-12-05
The version of Ubuntu, whether Desktop or Server, depends on what are you going to do with the box, mostly.
What will be the primary usage of this server? What will you use it for?

---

### Post by norman_069 on 2008-12-05
I want a desktop that i can use as a Server when i am not home.  It will probably be used as a server 50 percent of the time.  i want to set up a raid 5 on it as well

thanks

---

### Post by hictio on 2008-12-05
Cool, a server of what? A web server, a backup or file server?

---

### Post by norman_069 on 2008-12-05
I want to be able to store files and access them from where ever I am so I guess a file server.  I would also like to print from it and maybe stream video if possible.

---

### Post by nault31 on 2008-12-05
If you are using it as a desktop then I suggest keep the desktop version installed.  The server edition is more or less the same OS without a GUI and other software as professional servers don't need those features.  You can do anything the server edition does with the desktop edition as all the packages are the same.

My server runs the server edition, but it's only plugged in with 2 only cables: the power cord, and the ethernet cord to connect to the router. All I use it for is to store my files that are shared over Samba and I can access them from any of the 4 computers in my house (such as stream music or videos).  This one has a statip IP in case the power goes out and it reboots that it'll keep the same local IP. (It needs to stay constant in case I need to change settings I can log in wirelessly from my laptop)

However my brother in law runs the desktop edition on his server, he uses it as a regular computer most of the time but there are extra hard drives that hold his movies and music that are also shared over Samba in the exact same manner as my server.  He doesn't use a static IP for his and it works just as well.


It's pretty simple:
-set up a folder or extra HD to store those files
-make sure it "automounts" on startup  (I had this problem for a while)
-configure the folder with Samba so that it easily shares with windows computers (and shares well with Ubuntu computers)
-I use CUPS on my Ubuntu desktop to share my printer over the network, that's basically makes my desktop a "print server"


However I do not access my server from outside of my home network (ie over the internet), but doing that is not impossible.

---

### Post by hyper_ch on 2008-12-05
just use your normal desktop isntall and have it install openssh-server.

Then, if you're behind a router you will need to forward port 22 from the router to your computer. It's best to assign a static ip...

then you'd also need some dyndns service that will give you a dynamic domain name and points it to your home, so the IP is always current. If you have a router then it probably supports one or multiple dyndns services, just sign up for one that is supported (no-ip.com and dyndns.org are free to use).

Once that's done, you can use a ssh program to enter your computer/server. On windows you can use putty to get a terminal connection or winscp ([www.winscp.com](www.winscp.com) --> free and open source) to get a graphical interface for file transfer.

on linux you can use sshfs to mount a remote server folder into your local file system.

---

