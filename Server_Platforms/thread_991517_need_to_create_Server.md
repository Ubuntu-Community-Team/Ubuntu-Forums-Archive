---
title: "need to create Server"
date: 2008-11-23
forum: Server Platforms
---

### Post by myharshdesigner on 2008-11-23
i need to make ubuntu desktop as my server and want to connect my windows pc with it and also share hdd on networking. pleas guide me hot to do that it will be easy in windows with the hep of DHCP server. 

now how can i do it in  ubuntu 8.10.
please guide me.


i also need to install xampp [PHP] server on ubuntu machine.

---

### Post by rslrdx on 2008-11-23
what kind of server? need more details on what you are trying to achieve. To me at least, i cant be sure if you are trying to share your network connection, host pages with php, or create samba shares to share files with other computers on the network

---

### Post by cariboo on 2008-11-23
Go to System-->Administration-->Synaptic Package Mnanager -->Edit-->Mark Packages by Task and select the servers you want.

Jim

---

### Post by myharshdesigner on 2008-11-23
i want to make a server - client network where server have ubuntu 8.10 and clients will have windows xp pro and ubuntu 8.10 both. so how can i create it please guide me.

---

### Post by mitchroberts on 2008-11-24
Are you looking for thin client's or just a file serve?

---

### Post by myharshdesigner on 2008-11-24
> **mitchroberts said:**
> Are you looking for thin client's or just a file serve?


*thin client's or just a file serve* ?

measn ?

what simply i can explane is i nee to do networking between linux and windows pc. with also folder/drive sharing.

---

### Post by mitchroberts on 2008-11-24
for file folder and drive sharing look at setting up samba also
remember linux can read a windows disk windows can not read a 
linux disk windows can't even see it so samba will let you see a linux drive.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by squeakyneb on 2008-11-24
You need to specify exactly what sort of server.
A web server, to put web pages up-look into apache, with PHP and mysql, see LAMP servers

A file server to give files over internet-theres a few ways to do this, such as FTP and NFS, also possible with webservers

File sharing, to give files over LAN-see Samba, it's like the Linux version of windows network drives

I can help you out with Apache and web pages, but thats it. I need some help with samba.

---

### Post by myharshdesigner on 2008-11-24
> **squeakyneb said:**
> You need to specify exactly what sort of server.
A web server, to put web pages up-look into apache, with PHP and mysql, see LAMP servers

A file server to give files over internet-theres a few ways to do this, such as FTP and NFS, also possible with webservers

File sharing, to give files over LAN-see Samba, it's like the Linux version of windows network drives

I can help you out with Apache and web pages, but thats it. I need some help with samba.

ya i need web server and file server both.

---

### Post by mitchroberts on 2008-11-24
samba is in the repository also i would run the server not the desktop you can always install x-window system if you need it
i am not the best person to ask about a web server there are people out there that could tell you a lot more i mostly deal with terminal server and file servers but read the link i sent in my last post that should get you on your way to setting up
a file server between linux and windows...:guitar:

---

