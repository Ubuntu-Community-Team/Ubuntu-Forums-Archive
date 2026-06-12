---
title: "Make Ubuntu Server visible for WAN?"
date: 2011-01-16
forum: Server Platforms
---

### Post by ReinVO on 2011-01-16
Hi there,


I downloaded Ubuntu Server. I absolutely love it. It is easy to set up and I've already learned alot while doing so.

Now, I want to get a bit further. I want my Ubuntu Server to be accessible from the internet, so I can access my files and webpages from everywhere.

Everything works locally, but I don't have any clue to maken it visible for WAN. Is everything from here set in the router settings? Or will I also have to make adjustments in the Server's settings?


Thanks in advice.
Rein, linux novice

---

### Post by spynappels on 2011-01-16
Without a little information on what you want to expose to the WAN, and without you knowing what you are doing, that is a very bad idea. Server security is easy to compromise if you don't know what you are doing.

Reading the stickies by Bodhi.Zazen in the Security Forum is a great start, and if you can tell us exactly what you want to do, we'll do our best to help you achieve what you want or tell you why it would not be a good idea.

---

### Post by ReinVO on 2011-01-16
Thanks for your reply Spynappels. I fully understand your reply. I know security is something very important to keep in mind. So the first thing I'll do is read through the stickies you pointed me to. 

Furthermore; my ultimate goal is to have access to ftp, ssh and the webpages (apache, php, mysql).

I'm a very patient person and want to do this step by step. Just to learn about it. I thought this forum would be a great start. So if anyone has some interesting links or tips; feel free to share!

Greetings,
Rein

---

### Post by RobbanC on 2011-01-16
All your servers are currently running on your machine (i.e. you can connect to your server from another box on your local network)? 
In that case, all you will have to do is open (or forward) a few ports in your router.

FTP uses port 21
SSH uses port 22
webpages uses port 80

Depending on your router, you might find som help how to open ports here:
[http://portforward.com/]("http://portforward.com/")

This tool might be useful to see if your server responds on a certain port that you have opened:
[http://www.canyouseeme.org/]("http://www.canyouseeme.org/")

Also, note that the whole internet will be able to access your server, so use strong passwords, disable guest- and anonomous-FTP and disable that root is able to log on through ssh. At least that is a good security start according to me. :)

---

### Post by ReinVO on 2011-01-16
Thanks for the useful reply RobbanC.

canyouseeme.org says my ports are open and my isp is not blocking them. Trying to login to my ip usng ftp or ssh does not work tho, is it because I try it while being in the network?

---

### Post by cariboo on 2011-01-16
> **ReinVO said:**
> Thanks for the useful reply RobbanC.

canyouseeme.org says my ports are open and my isp is not blocking them. Trying to login to my ip usng ftp or ssh does not work tho, is it because I try it while being in the network?

Some routers won't allow you to connect to your external ip address from inside you internal network. Either go the somewhere that has wifi if you have a laptop and try accessing your server, or get one of your friends to access it from their computer.

---

