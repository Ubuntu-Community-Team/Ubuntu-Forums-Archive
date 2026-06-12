---
title: "Telnet Client !!!!!! C++"
date: 2008-06-15
forum: Server Platforms
---

### Post by tornado89 on 2008-06-15
I'm Trying To Create My Own Server On Ubuntu Hardy Using C++
It's A TCP/IP (Stream Socket). When I Connect To My Server Through
The Normal Terminal Telnet Everything Work Just Fine..

But When I Connect Using Windows Telnet.....
Whenever I Try To Write A Command It Gets Sent Automatically After One Character Is Typed.. I Can't Complete
Any Single Phrase... 
BTW I Send And Receive Through A Normal char Buffer ( char* )..
I Also Tried The SSH/Putty Client On Windows... But No Luck !!!!

 :confused:

---

### Post by windependence on 2008-06-15
> **tornado89 said:**
> I'm Trying To Create My Own Server On Ubuntu Hardy Using C++
It's A TCP/IP (Stream Socket). When I Connect To My Server Through
The Normal Terminal Telnet Everything Work Just Fine..

But When I Connect Using Windows Telnet.....
Whenever I Try To Write A Command It Gets Sent Automatically After One Character Is Typed.. I Can't Complete
Any Single Phrase... 
BTW I Send And Receive Through A Normal char Buffer ( char* )..
I Also Tried The SSH/Putty Client On Windows... But No Luck !!!!

 :confused:

You need to install the OpenSSH package. You should be using ssh anyway.

-Tim

---

### Post by tornado89 on 2008-06-15
Hey Thx For Ur Reply...
I Do Already Have OpenSSH Installed... But
What Does IT Have To Do With My Server or C++ :confused::confused:

My Problem Is That Windows User Can't Communicate With My Server 
Throughout Any Client .... ONLY LINUX

As I Mentioned Before They Can Only Connect But Can't Send Anything In One Piece ,,,,, 
It's Like A Problem In Line Buffering or Something Like This !!!!!

---

### Post by windependence on 2008-06-15
> **tornado89 said:**
> Hey Thx For Ur Reply...
I Do Already Have OpenSSH Installed... But
What Does IT Have To Do With My Server or C++ :confused::confused:

My Problem Is That Windows User Can't Communicate With My Server 
Throughout Any Client .... ONLY LINUX

As I Mentioned Before They Can Only Connect But Can't Send Anything In One Piece ,,,,, 
It's Like A Problem In Line Buffering or Something Like This !!!!!

You should be able to reach the Linux box from Windoze boxes using PuTTY. Use the IP of the Linux box unless you know what you are doing with DNS.

What happens when you try to reach them via PuTTY?

-Tim

---

### Post by PacketCollision on 2008-06-15
Tim: a telnet client is often used for basic testing, tornado knows to use SSH for shell access.

What terminal emulation settings are in use for Windows telnet/PuTTY?  I've never heard of the problem you are experiencing, but it could be something about the client.  Try talking to an SMTP or HTTP server with the Windows telnet client and PuTTY and see if you experience the same problem.  If you do, then you know it is a setting on the Windows computer.  If you don't, then it is your programming.

---

### Post by tornado89 on 2008-06-16
I Use VT100/ANSI Emulation..
I Tried To Connect To An HTTP Server From The Windows Basic Telnet And
All Goes OK... Perhaps You're Right ( PacketCollision ).. And It's My Programming I'll Check Up My Networking Class...
But... mm.. What Could Cause Such A Problem ???
I Mean It Works Flawlessly On Linux !!!????
I Tried From More Than 9 Linux Boxes At Same Time... & All Is Great

Anyway I Should've Excpected This From WindoZe :lolflag:
I'll Post Back After Checking All My Code.
Thx So Much Guys......

---

