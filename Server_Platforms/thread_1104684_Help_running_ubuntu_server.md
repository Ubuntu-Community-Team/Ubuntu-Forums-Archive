---
title: "Help running ubuntu server"
date: 2009-03-23
forum: Server Platforms
---

### Post by gafadi on 2009-03-23
Hey guys hi 

i am a new user to Ubuntu family , i recently purchased a server 

Ubuntu 64bit , Intel DUAL CORE E2140 ,	2 GB ram , 500 GB SATA

I will be running a site in this server but the thing is i don't know anything about running Linux server's and running sites on them. 

I was provided with Ip , User and pass from the host , the host was kind of cheap so they don't provide much help so i am here for help. 

Ok how can i login to my server , install necessary thing ( which i don't know, i don't know what i am suppose to install and how ) 

It would be great if you guys can help me out. 

thanks

---

### Post by BkkBonanza on 2009-03-23
To start out you login with SSH. That service is usually running there from the start.

If you are working from Windows. Then use putty or Tunnelier to do ssh. If from Linux then open a console and do like this, replace with your values,

ssh user@ip

enter password when prompted. That will give you a console window into the remote machine where you can get going. As for what to do after that - well thats a logn story. You'll have to read a lot about remote managing a server and it depends on what you want to do. Also you'll need to read a bit about securing the server.

As an aside - I would mention that you don't need a "real" server to learn and test all the things you can do with a server. It's cheaper (free) and easier to install virtualbox on your machine (Win or Linux) and then install Ubuntu server into that. You would have a virtual server runnig on your own machine that behaves (almost) identically with the one you would run in a remote data center. Of course, when you want to have real site visitors then you will need the real server - whether dedicated or vps. 

Even with a real server you usually need a place to test code and work on the site without upsetting real sites or clients. Using a virtual machine for that is ideal as you can make it mimic the real server and then rsync any updates to the real server directly from the test/dev virtual server.

---

### Post by Iowan on 2009-03-24
There are others available, but [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page is a good place to start.

---

