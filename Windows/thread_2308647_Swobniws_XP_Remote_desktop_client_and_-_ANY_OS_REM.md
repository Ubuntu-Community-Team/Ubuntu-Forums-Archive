---
title: "Swobniws XP Remote desktop client and - ANY OS REMOTEDESKTOP"
date: 2016-01-04
forum: Windows
---

### Post by drazenprado on 2016-01-04
Greetings.
Time ago i posted about what to do with some pentium pro PCs with very limited hardware. 
Some suggestions were install puppy4x or tinycore, but i really would rather that they would not do any kinda of tasks.
Then i installed windows XP suricata (a very "light" mod). 
Today i tried to use mi AMD e1 laptop with w7 as server, and the results were very good. 

The NICS of the "clients" are 10mbits, then i guess that i had better use RPD instead VNC. 

Then now i am a bit "decided" about what to do. Now i guess that i will need a RDP server, and i do not really matter what would be linux windows... ubuntu puppy opensuse... Anyone. And if the RDP server would be "lighter" in the clients, it is another good point.

Finally, i am here asking for suggestions of any RDP server multiuser (at same time) for use with those windows xp clients. 

Event if a linux client would be lighter than those xp, it would be greater then. 
Finally, thanks a lot. I will ask this in ubuntu puppy and opensuse and TC forums. Thanks a lot

---

### Post by drazenprado on 2016-01-05
bump

---

### Post by MAFoElffen on 2016-01-05
You know what RDP stands for right?

RDP is an acronym for Remote Desktop Protocol. That means you will be trying to control one pc (running a Remote desktop server) from another (running a remote desktop client) as is you are seeing their GUI desktop from a GUI window in your desktop. This transmits the GUI representation of the remote server computer to the local client... 

A variation of that is a RDP Gateway, which controls RDP access to computers on your network.

RDP sends all it's GUI screen to another PC over it's network connection...That is a lot to ask fo from any PC, let alone an old PC of limited specs. For either of those roles above, you could do it, but it would be so painfully slow that it would seem unusable. 

Why? 
(1) All comms limited to your 10mBs NIC Card. Out of 1000/100/10 speed NICs, yours is the slowest rating of those. Even browsing the internet would be slow, let alone trying to transmit or receive a remote desktop.
(2) A Pentium Pro could not handle what you are asking it to do. Fastest Pentium Pro was 200mhz, 32bit data path ... and they did not do MMX, which was for multimedia processing. Which means it never did very well trying to do GUI intensive applications.

Think that a Pentium Pro was designed for Windows 95, was okay with Windows 98 ... and painfully slow with Windows XP. It deadened there, t o be able to run anything in the Windows line. You are already pushing it past what it was originally designed for.

---

### Post by howefield on 2016-01-05
Thread moved to the "*Windows*" forum.

---

### Post by drazenprado on 2016-01-06
The initial idea was LTSP but it got several issues. With tons of trys no one of them was sucessfully. Then tried puppy linux, it booted, but in the SCSI hdd it got kernel panic and when opening seamonkey it got frozen.

I know all of that, i know the limited hardware and i have being reading tons of documentations and ways for make them usable.
Then, now i finally make the test with windows xp installed and the everything was good enough. Only slow "streaming video" but with low resolution it get better.
If a previus versions of windows (or linux with rdp client built in) could make the job better, it would be greater then.

If linux could be a good RDP server, i would like to know any suggestion, but if windows does it better (what a disapoint for a linux fan), then i will enable that hack for multiuser RDP in a amd a8 "server".

---

