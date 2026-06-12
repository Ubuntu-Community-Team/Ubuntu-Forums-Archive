---
title: "[Hardy Server] NTFS Supported?"
date: 2008-05-05
forum: Server Platforms
---

### Post by psyion on 2008-05-05
Hello All,

I have started the task of moving from using a windows home server box as my home file server and plan to use Hardy Heron Server edition as a replacment. I have backed all my data up onto a 500gb drive(internal NTFS) and have installed Ubuntu Hardy Heron Server(latest) on another hard drive(internal EXT3)

I have also installed the Gnome desktop manager so i have a GUI, when i click Places> and select my 500gb backup NTFS drive i get the message unable to mount NTFS partition and advises me to try forcing it at the command promt. I tried the suggested command and it didnt seem to do anything.....

I did do alot of reading before deciding to move over to linux, somthing i did read about hard heron is that its NTFS compatable out of the box..

My question is this..

Is there anything im doing wrong when trying to access this NTFS drive? Or is there another way to go about getting this partition mounted so i can copy the data to an EXT3 drive?

Thanks very much

---

### Post by hyper_ch on 2008-05-05
hardy can read ntfs drives without installing something... however for writing to ntfs you need to install ntfs-3g.

If you can't mount the ntfs driven, then there might have been an improper shutdown of it. Best you hook it up to a windows machine and shut it down there safely.

Btw, if you have two computers that are networked, attach the drive to the windows computer...

on your linux box install ssh server
```

sudo apt-get install openssh-server

```

Then download WinSCP ([http://www.winscp.com](http://www.winscp.com)) on Windows, install it and run it.

Enter your IP of the ubuntu server and also the username and password for your system user on the ubuntu server.

Then you are connected to it.


You could also setup samba (which you probably will do anyway) to put the data onto to the server.

---

### Post by psyion on 2008-05-05
Ahh that would make sence, it is telling me also that the drive is in use.

I just tried to load windows home server from teh grub menu and its coming up with a message NTLDR missing..... then asks me to restart.

any ideas? It was workign before i installed ubuntu

---

