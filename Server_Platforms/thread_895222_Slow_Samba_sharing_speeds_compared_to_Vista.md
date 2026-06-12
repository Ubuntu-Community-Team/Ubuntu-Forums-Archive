---
title: "Slow Samba sharing speeds compared to Vista"
date: 2008-08-20
forum: Server Platforms
---

### Post by vorgusa on 2008-08-20
I have a 8.04 Server running Samba and a dual boot Desktop running Vista and Ubuntu 8.04 64bit.  Both the desktop and the server are up to date.  I am a bit unhappy with Samba's sharing speed... it is only going at about 9MB/s when sharing with the Ubuntu OS, but if I switch to Vista I get speeds of up to 70MB/s... to me that is quite a difference.  Does anyone know why I am getting such slower speeds on Ubuntu?

---

### Post by mbeach on 2008-08-20
out of curiosity, is the slow speed only observed when transferring in one direction, but fast coming back the other way?

if you copy a big file from computer A to computer B, then from B back A, is the same rate of speed seen?  If so you may have a nic speed/duplex issue.

---

### Post by vorgusa on 2008-08-20
hmmm not sure... but I did more testing last night, let me know if it sounds that way.  

From Server to Ubuntu Desktop I get 45 MB/s
From Ubuntu Desktop to Server I get 9.5 MB/s
From Server to Vista I get          110 MB/s
From Vista to Server I get          100 MB/s then half way drift to 75 MB/s

This was all tested on the same machines using a 3.2GB file

---

### Post by MJN on 2008-08-20
Have you searced the forums? I don't have any specific references to hand but this issue comes up a lot and so it would be worthwhile (for everyone) if you at least attempt some of the proposed fixes/configurations previously discussed.
 
Mathew

---

### Post by freelinuxhelp on 2008-08-20
MS developed a new version of the SMB protocol for Vista and Server 2008 in order to speed it up. I believe that Samba 4 is supposed to support the changes in the protocol. You might find more information here: [http://us1.samba.org/samba/](http://us1.samba.org/samba/)

---

### Post by vorgusa on 2008-08-20
Having to do with Samba 4.0, the server is still running the 3.2 version of Samba, so I don't see how it can be any faster.  

I looked around the forum some more and there are tons of threads about samba in just the last couple weeks.  I will try doing a full out mount instead of going through the Network Places area and seeing if that speeds it up. Someone mentioned that it would, kind of odd that there would be a speed difference there, but worth trying out.

---

### Post by vorgusa on 2008-08-20
I tried permanently mounting it and got very little benefit out of it.  Uploading to the server increased but I am still less the half the speed of Vista... anyone have any other ideas?

---

### Post by MJN on 2008-08-20
A couple of things worth trying:

- Check your interface card configuration at both ends of the link as mbeach hinted at. I suggest ethtool for this (e.g. sudo ethtool eth0) to check you are running in full-duplex (or whatever your cards/network can support).

- Try mounting the Samba share with CIFS, if you're not already, on the Ubuntu client as this reportedly can improve performance.

Mathew

---

### Post by HermanAB on 2008-08-20
Increase the buffer sizes for Samba.  That can make a big difference.

---

### Post by vorgusa on 2008-08-20
I am using the CIFS method of mounting.. and I did get an increase in Upload performance.  I will try out that ethtool mentioned and see if I can find out about increasing the buffer size for Samba

---

### Post by vorgusa on 2008-08-20
Ok, I have been searching way too long.. how do you change the buffer size in Samba?  I keep finding articles that say it is a good way to increase speed, but they do not say HOW!

---

### Post by Mrwasab1 on 2008-08-20
> **vorgusa said:**
> Ok, I have been searching way too long.. how do you change the buffer size in Samba?  I keep finding articles that say it is a good way to increase speed, but they do not say HOW!

from the man page of smbclient

```
 -b buffersize
          This  option  changes  the transmit/send buffer size when getting or
          putting a file from/to the server. The default is 65520 bytes.  Set&#8208;
          ting  this  value smaller (to 1200 bytes) has been observed to speed
          up file transfers to and from a Win9x server.

```

Need to specify the hostname, and you need to escape all the \'s so you end up with

```

smbclient \\\\hostname\\public -b 1200

```

then you are asked for a password and it should be set.

---

### Post by vorgusa on 2008-08-21
that requires using the Command line which is not fun.. it does increase the speed to 60MB/s but still far less the Vista.. guess I will just have to stick with what I have.

---

### Post by mbeach on 2008-08-21
it will probably show up auto negotiated 100/full and not yield much usefull in this disussion (it might though) but what does:
sudo mii-tool
output from the server, then from ubuntu client?

---

### Post by vorgusa on 2008-08-25
I will give it a try.. ifconfig said 1000mb/s  and I was able to change both MTUs to 7000... one odd thing was that the Desktop would not go to 9000 (or 8000), which is the packet size for the switch I use.  The Server let me go all the way to 9000.  Do you think that is just the difference in NICs?

---

### Post by mbeach on 2008-08-25
anytime I've seen problems with fast speeds one way, slow the other all hanging off the same network it seemed to be a nic setting.  Either the switch is unable to auto negotiate with the particular nic, and lowest common speed is chosen, or one is attempting full duplex, the other half etc.  I never seem to be able to fully retain (in my head) the 'best' policy, and end up doing some reading when I run into those troubles.  Sorry - I'm not really of much help on this one.  If you had a spare card and some spare time it would be something I'd try though (swapping in a new card) to rule it out.

---

### Post by vorgusa on 2008-08-26
For the desktop I got :

eth0: negotiated 1000baseT-FD flow-control, link ok

which looks pretty good to me for the Server I got:

SIOCGMIIPHY on 'eth0' failed: Operation not supported

Does this Mii tool have to do with Network manager?  or something Server does not have that desktop does?  Either way I think the server is setup correctly since it can go to 115 MB/s and either way I got speeds of 40 MB/s currently which is way over 100Mb/s

---

