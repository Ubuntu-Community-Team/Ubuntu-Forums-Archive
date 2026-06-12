---
title: "how to host using ubuntu first time user here"
date: 2010-07-26
forum: Server Platforms
---

### Post by amargarit on 2010-07-26
I just joined and this is my first use of ubuntu. My friend has started her new business from home and it is quite a big business, and I have been charged to buy and setup a hosting server that will be hosted in her home. I have ubuntu 10.4 on my laptop and that is what I will use on the new computer she just bought.

My question is if you can assist me....what do I need to accomplish this. She wants to host her own website (which she now has with GoDaddy) but wants to create a new one and host it. I will be taking care and maintaining the server. I have never used any type of Linux, but am not intimidated by this also. 

She is getting a static iP from her ISP (Business account) so all ports will not be filtered. What would I need to host, applications, do I need security apps? Any help will help.

Thanks so much,  Oh, the PC is a desktop with Duo processes, 8 gig ram, 1 terb hd.

Anthony

---

### Post by arrrghhh on 2010-07-26
Honestly it'd probably be easier/cheaper for her to pay someone to host her site - that way she doesn't have to worry about security, hardware failures, backups, break-ins... or the big one - bandwidth!  Obviously that can still be an issue, but with a hosted solution usually upping bandwidth is a breeze.  Not always the case on an individual line - business or otherwise.

---

### Post by ruffEdgz on 2010-07-26
> **arrrghhh said:**
> Honestly it'd probably be easier/cheaper for her to pay someone to host her site - that way she doesn't have to worry about security, hardware failures, backups, break-ins... or the big one - bandwidth!  Obviously that can still be an issue, but with a hosted solution usually upping bandwidth is a breeze.  Not always the case on an individual line - business or otherwise.

I have to agree with this statement.

There are so many aspects to administering a web server which include security (application, server, network, etc...), configuring, updates, backups, recovery, and much, much more.

There isn't just one place to start with this request so its hard to just say 'here you go' and have a web server up and running over the weekend.

I always encourage people to try something new and if you are interested in doing this on your own, by all means, do it to learn more. If you want to make this into a production server which talks to others on the web, I would advise on a hosted, non-headache solution.

---

### Post by amargarit on 2010-07-26
Thanks guys for a quick responce. I do want to host this on my own, it will be a learning process i know, but the only way to learn with all the speed bumps..;  ) I install ubuntu 10.4 I know there is a lot to do, so I am willing to start and learn as I start. I know this is getting your feet wet big time. So any tips will help if at all possible. Once I get it up and running, it will be because of all the help i will have received from this forum.  ;  )

---

### Post by arrrghhh on 2010-07-26
Well I'm not even sure where to start then.  Do you need a MySQL database?  PHP?  Is it just going to be a simple site?

If it's a fairly simple site, apache by itself should get you started.  As far as security goes, there's a lot of little things within the software that you need to setup, but the main one is going to be firewall.  I would strongly recommend having a hardware firewall between the internet connection & this server.  I also run a software firewall, UFW makes it very easy to open ports.

There is sooooo much more, I'm not even sure where I should direct you.

I think Google found me the perfect guide.  [Check it out!](http://www.devarticles.com/c/a/JavaScript/Building-a-Secure-Web-Server/)  Looks like it goes over a lot of topics, from the ground up.

That one does go over some topics that may not apply... So [here's](http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server) another guide.  I literally googled "building a web server, ubuntu" to turn up these searches BTW :D

---

### Post by wojox on 2010-07-26
Do you have a router? You'll need to Port Forward port 80.

Here's a good link to get you started [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

---

### Post by amargarit on 2010-07-27
Hey thanks for the links, I will look at it today.:D

---

### Post by i.r.id10t on 2010-07-27
I would look at using ISPConfig

---

### Post by drdos2006 on 2010-07-27
I found this HOWTO very informative.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards

---

