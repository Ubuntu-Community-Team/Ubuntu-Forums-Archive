---
title: "How to Setup Ubuntu File Server"
date: 2008-01-27
forum: South Carolina Team - US
---

### Post by xarquid on 2008-01-27
It can be accessed by Windows (of any version), Macs, Linux etc. etc. all across your home network!

Posted by How To Forge:

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

Excellent Guide.

After you're done setting it up...it won't even need a monitor!! So, you can just dig out or build a "cheap bare bones" PC and use it as a file server for around your house for files, mp3s and old file storage. Great idea.

XQ

---

### Post by Flare183 on 2008-02-02
Awesome HOWTO!

---

### Post by brodiepearce on 2008-03-27
I don't understand why it was necessary in that guide to format the storage drive/array in NTFS.  

Windows machines won't be interfacing directly with that drive... wouldn't any of the decent Linux file-systems have been fine?

*edit*

Forgot the opening paragraph... NTFS formatting so it can be physically swapped between Windows PCs and the server.

---

### Post by tryorke on 2008-09-13
i just setup a server following the directions (hardy server), and yet my hardy desktop cannot access the server. is there something additional i need to do on the client machines?

---

### Post by WillT87 on 2008-12-10
Awesome thanks for posting

---

### Post by aago1254 on 2009-06-27
i  just setup a server following the directions (hardy server), and yet my hardy desktop cannot access the server. is there something additional i need to do on the client machines?
 
 
please note you still have to be in the same work group. also in ubuntu desktop  you have to slecet a netowrk to connect to and put in your server info quite easy.   
ubuntu desktop is easier to network share than windows

---

### Post by DivineTemplar on 2009-09-27
This guide might come in handy for me in the future. Bookmarked for future reference.

The last attempts I made at creating a home media server were based upon using an old Xbox, and it worked out pretty well in fact. I haven't had a need for one or a spare computer to use to create a new one since I left that old one in the move, but it is always good to keep options open for when the time comes again that I have both the equipment and the desire to make one.

Thanks for sharing this with us.

---

### Post by amalafrida on 2011-11-28
I've succeeded in getting the LAMP ensemble set up on my local machine. Everything works fine. I can serve web pages to any box on the LAN.

The part that is driving me crazy is remote connection.

In order to keep this as simple as possible, I've pulled the router out of the loop.

Numbers look like this:
HOST: 192.168.1.64 -->
browser serves correct web page;
google translate: fails, of course (invalid url)

MODEM: 192.168.1.254 -->
browser serves modem config/info page;
google translate: fails (invalid url)

INTERNET IP ADDRESS, static address assigned by ATT: 74.181.252.241 -->
from my computer (192.168.1.64) browser serves modem config/info page;
from remote computer browser: timeout
google translate: fail

INTERNET GATEWAY ADDRESS: 72.157.8.14 -->
browser yields 'time out';
google translate: fail

all four addresses ping out nicely.

How in the world do I get remote access to this machine? I've floated around chat rooms and spent well over an hour with BellSouth ... any suggestions?

Thanks in advance.

Robert

---

