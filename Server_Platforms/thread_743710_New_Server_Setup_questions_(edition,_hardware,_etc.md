---
title: "New Server Setup questions (edition, hardware, etc.)"
date: 2008-04-02
forum: Server Platforms
---

### Post by Erja on 2008-04-02
Hello all.  I have two computers currently (desktop dual boot Ubuntu 7.10 & Win XP; and laptop running Vista), and am preparing to put together an Ubuntu server.  Here is what I'd like to do:

* Host my own website(s)
* Connect a network printer to the server for my other computers to use (without having to switch usb cables constantly between my laptop and desktop)
* Host shared files (such as music, video, etc.)

My internet setup is dsl modem + linksys router (wireless to the laptop, and wired to the desktop).  I would like to run a wired connection to the Ubuntu server.

So, here are my questions:

1. Which Ubuntu edition would be best for me to use?  I've only been using 7.10 for about 4 months, and have fairly limited linux experience.  I am, however, interested in learning and wouldn't necessarily shy away from the server gui-less version if it is superior for my needs.  6.06 Server, 7.10 Desktop, wait for 8.04 Server/Desktop?  Pros/cons to using Desktop vs. Server?

2. For hardware: the computer I am building is mostly made up older computer parts from my previous build.  I have a Radeon 9600Pro video card which I could stick in it, but if I end up using Server edition would I be better served to just use my motherboard's onboard video?  I realize this might be a little off-topic.

3. Related to the issue of Desktop vs. Server edition: does using the server edition affect server performance in a noticeable way?  The computer will be running on an Athlon 2400+ processor, with 1GB of DDR 3200 memory.

4. How much traffic would a website need to generate before hosting it myself becomes unrealistic?  We have a 2 mbps dsl connection.

5. Lastly, any specific suggestions for my particular setup with regards to software I should use?   

Thanks for all your help in advance!

---

### Post by kool_kat_os on 2008-04-02
1. I think you should wait for 8.04 LTS to come out 

2.Any old computer will due.

3. I personally like to use desktop edition

4. Dont worry...i guarantee that your computer and band width will be able to handle it...how much traffic are we talking about?

5. Apache 2 HTTP server for the web server...USE IT!!!

---

### Post by Erja on 2008-04-02
> **kool_kat_os said:**
> 1. I think you should wait for 8.04 LTS to come out

Is there a specific release date, or is is just "sometime in April"?  Also, does the LTS release come out concurrently with 8.04 or does it release later? 

> **kool_kat_os said:**
> 
2.Any old computer will due.

3. I personally like to use desktop edition

4. Dont worry...i guarantee that your computer and band width will be able to handle it...how much traffic are we talking about?

Zero at the start, but I'm hoping to grow :)  Just trying to get an idea of what the self-hosting ceiling is.

> **kool_kat_os said:**
> 
5. Apache 2 HTTP server for the web server...USE IT!!!

Thanks!

---

### Post by Iowan on 2008-04-03
> **Erja said:**
> Is there a specific release date, or is is just "sometime in April"?  Also, does the LTS release come out concurrently with 8.04 or does it release later? I saw the number 20 somewhere (April 20th?) 8.04 IS the LTS - both for server and desktop (server has longer support). Server kernel is (reportedly) optimized for server use.  Besides the GUI, the server usually comes without apps like Gimp, OpenOffice, multimedia players, etc. However, LAMP is available out-of-the box (off-the CD?) Just my opinion, but if your server is just gonna serve, the onboard video should be adequate. BTW, if you decide you need a GUI, you can add it to the server later.

---

### Post by schneider707 on 2008-04-03
Ok...you want to host sites out of your server which is at your home im assuming. 

Run 7.10 server, when installing select lamp and dns. After installation is complete, run apt-get install update && upgrade. Then run apt-get install phpmyadmin. That should be your basic server needs right there. Although I really don't know how you will host sites from that box as you need 2 static ips for your dns server (unless someone knows a trick around this?? i was thinking of [http://www.opendns.com/](http://www.opendns.com/) if it actually works) 

You <i> can </i> install a gui but there really isn't a point to it. O that reminds me, apt-get install webmin. That way you can manage your server over the net, and manage your mysql db with phpmyadmin. 

...I don't think im forgetting anything. I just did all this stuff like 6 times for several different friends...i have it down to 30min or so (some wanted gui's anyways). 

I would say to *not* wait for the new ubuntu simply because this would be good practice for you to throw a server up then take it down and re-do the whole thing. Plus, first few weeks of bugs and waiting for programs to get their own updates kinda sucks =P

If you need any help walking through any of this I'm more than happy to help.

---

