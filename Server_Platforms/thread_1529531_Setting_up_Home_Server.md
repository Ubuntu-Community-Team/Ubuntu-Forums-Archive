---
title: "Setting up Home Server"
date: 2010-07-12
forum: Server Platforms
---

### Post by David52 on 2010-07-12
I am brand new to this forum so I will admit that. I run 3 of my own websites and host and manage 2 others for outsiders. I use a hosting company out west as a server. But due o them being hit by antiDos attacks my sites go down sometime for 12 to 15 hrs when it happens. Lets say at least once every 3 months. My account will expire with them in 60 days so I am considering setting up my own home server. I did a dig on google last night and found this link to set up a home server. Can someone that has been into this experienced take a look at it and tell me if it is just this easy and can u set up your own home server this way with another tower. 
 
[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
 
Now I did download the Ubuntu Server addition, I did burn it onto a disk as a ISO file. This is as far as i have went because I do extensive research before I do anything. Now I have 2 computers. Both are Desktop Pc Towers. ! use one full time and have the other idle as a spare. I am considering using the spare as a home server, but I am going to put in a fresh hard into it. 
 
[LEFT][COLOR=#000000]Western Digital 640GB 7200RPM SATA2 3.0GB/s Hard Drive - WD6400AADS [/COLOR][/LEFT]
 
[LEFT][COLOR=#000000]The desktop I am going to consider has a 1 gig memory stick. I have a router but have nevr had to use it for I use the ethernet cable to hook to my 2 wire modem. I do use att dsl as my internet. Now can I set up a home server to run my own sites and these 2 as the link states. If not correct can anyone direct me to link to answer my questions. Go to go and i will await a response.[/COLOR]
[COLOR=#000000]David[/COLOR][/LEFT]

---

### Post by tyleruk on 2010-07-12
If you follow that tutorial you will have a working web server. The only problem with it is that he says don't use LAMP server, then goes and explains how to install Apache, MySQL & PHP. Well a LAMP server is Apache, MySQL & PHP so you might as well choose LAMP in the first place.

You will need to setup your router so you can route outside traffic to your server, a good guide for this can be found [here]("http://lifehacker.com/127276/geek-to-live--how-to-access-a-home-server-behind-a-routerfirewall")

The problem with having a server at home is that you’re likely to have a slow upload speed on your internet connect; this will mean your website will probably be very slow. You will also be more vulnerable to DOS attacks on a slow connection, if you suffer from this it may be worth telling your hosting company to see if they can do anything.

---

### Post by David52 on 2010-07-12
I am brand new to this forum so I will admit that. I run 3 of my own websites and host and manage 2 others for outsiders. I use a hosting company out west as a server. But due o them being hit by antiDos attacks my sites go down sometime for 12 to 15 hrs when it happens. Lets say at least once every 3 months. My account will expire with them in 60 days so I am considering setting up my own home server. I did a dig on google last night and found this link to set up a home server. Can someone that has been into this experienced take a look at it and tell me if it is just this easy and can u set up your own home server this way with another tower. 

[[COLOR=#444444]http://net.tutsplus.com/tutorials/ph...rver-for-free/[/COLOR]]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/")

Now I did download the Ubuntu Server addition, I did burn it onto a disk as a ISO file. This is as far as i have went because I do extensive research before I do anything. Now I have 2 computers. Both are Desktop Pc Towers. ! use one full time and have the other idle as a spare. I am considering using the spare as a home server, but I am going to put in a fresh hard into it. 

[LEFT][COLOR=#000000]Western Digital 640GB 7200RPM SATA2 3.0GB/s Hard Drive - WD6400AADS [/COLOR]

[COLOR=#000000]The desktop I am going to consider has a 1 gig memory stick. I have a router but have nevr had to use it for I use the ethernet cable to hook to my 2 wire modem. I do use att dsl as my internet. Now can I set up a home server to run my own sites and these 2 as the link states. If not correct can anyone direct me to link to answer my questions. Go to go and i will await a response.[/COLOR]
[COLOR=#000000]David[/COLOR][/LEFT]

---

### Post by bodhi.zazen on 2010-07-12
You can easily set up a home server, I would check with your IP provider first. Many IP providers will either block port 80 (and similar) or my IP provider limits the upload speed, so my web servers are slow.

An alternate is to consider an alternate host, VPS are very cost effective and almost always perform better then a standard internet connection.

---

### Post by lisati on 2010-07-12
Threads merged

---

