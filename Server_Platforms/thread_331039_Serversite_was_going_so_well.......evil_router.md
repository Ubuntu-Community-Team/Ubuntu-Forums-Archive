---
title: "Server/site was going so well.......evil router"
date: 2007-01-04
forum: Server Platforms
---

### Post by aceron on 2007-01-04
Hey So I followed the steps [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") to make a server.
I set up an account with dyndns (made sure it was dynamic)
I installed wordpress in /var/www and all was going well....then i plugged in my router instead of going directly through the cable modem
its a linksys i went in and set up the ddns for dyndns 
and port forwarded 80
now whenever i try to go to my site it brings me to the routers admin page
note that all was working well and fine pre-router (meaning i could go right to my site via browser)
did i miss a step? does this mean that my isp is blocking 80?  or do I have a setting messed up somewhere?
I realize this may be a question asked often so I did search the ubuntu forums but found nothing that could fix my problem
oi, any help would be appreciated

---

### Post by ikonia on 2007-01-04
this is a router setup issue, nothing to do with ubuntu

---

### Post by aceron on 2007-01-04
not necessarily, i was more curious if i had to do something to apache in order to get dns to work or mysql for that matter, neither of which am I very familiar with

---

### Post by digitalshepard on 2007-01-04
ikonia is correct.  
*Taken from [http://www.boutell.com/newfaq/creating/forwardports.html](http://www.boutell.com/newfaq/creating/forwardports.html)*
[INDENT]Problem #2: Remote Router Access Is Enabled

You're testing from a computer outside your network and you still get the router's logon page! What's going on?

Your router has an optional feature that lets you log in and make configuration changes from the Internet. This is not setting up a web site. It is remote access to your router's built-in configuration pages. The Linksys WRT54G calls this "remote router access." It is turned off by default for very good reasons.

In your early attempts to figure out how to set up a web server at home, you probably enabled this feature on port 80 by mistake. Disable it now. It's not what you want and it's dangerous too. Turn it off and port 80 will become available for port forwarding purposes instead.

If you really want remote access to your router's configuration interface (and trust me, you don't, it's dangerous), configure it on an alternative port instead of port 80 so it won't conflict with your web server. Then you can log in remotely to your router at [http://yourdynamichostname:8080/](http://yourdynamichostname:8080/), (if you choose port 8080). But again, you don't want this. If you're an exception, you probably understand why already. [/INDENT]


I would guess that you were configuration port forwarding on your router and accidentally enabled remote access.  To disable this (assuming you have a linksys), go to **Administration -> Management.** 

Wordpress requires you to setup a mysql database, and requires that you have php installed.  I am pretty sure that wordpress explains pretty easily in one of the install.MYSQL.txt or something the setup for the database, and there are instructions for setting up php across the forum.

---

### Post by aceron on 2007-01-04
thanks for the help and yes i had mysql set up and everything was working and i could go to my site from my computer before router, after router no computer anywhere could see site, i've upgraded firmware on router and i'm going to see if it helps thanks again

---

### Post by Patrick-Ruff on 2007-01-05
> **ikonia said:**
> this is a router setup issue, nothing to do with ubuntu

all that was, was a pointless unhelpful post.  refrain from that in the future.

I heard that there was a way to load a linux-like firmware for some routers, I forgot the name of the project and the website but it was really awesome, it had many other settings and special stuff that you could use with the router, it was only compatible with certain routers, but it wouldn't hut to test I suppose.

---

### Post by dannyboy79 on 2007-01-05
> **Patrick-Ruff said:**
> all that was, was a pointless unhelpful post.  refrain from that in the future.

I heard that there was a way to load a linux-like firmware for some routers, I forgot the name of the project and the website but it was really awesome, it had many other settings and special stuff that you could use with the router, it was only compatible with certain routers, but it wouldn't hut to test I suppose.


who are you to say such a thing????? I think that your post was helpless also, why would he want to install alternate firmware on his router?? If you're going to post then post a solution to his problem not off the wall suggestions. You posting what you did and making the comment you did is like the pot calling the kettle black! You're tallking about the DD-WRT firmware project, here [http://www.dd-wrt.com/dd-wrtv2/index.php](http://www.dd-wrt.com/dd-wrtv2/index.php) if you want this guy to know about it you might as well have posted a link to it instead of saying, I think, ah, I think it's linux-like firmware.

Anyway, the soltuion has already been posted, it has to do with the router being setup so that it allows remote administration on port 80, just change this to port 8080, that's what I do anyway and you'll be fine.

---

### Post by Patrick-Ruff on 2007-01-05
my post had a lot more information then one line telling the guy off.  I'm on dialup, I can't simply search through thousands of web pages to find the particular project I'm talking about, I gave a good idea of what I was talking about.  anyways, this post as well, is pointless, I just felt the need to reply to that.

---

### Post by eric_stewart on 2007-01-05
> **aceron said:**
> Hey So I followed the steps [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") to make a server.
I set up an account with dyndns (made sure it was dynamic)
I installed wordpress in /var/www and all was going well....then i plugged in my router instead of going directly through the cable modem
its a linksys i went in and set up the ddns for dyndns 
and port forwarded 80
now whenever i try to go to my site it brings me to the routers admin page
note that all was working well and fine pre-router (meaning i could go right to my site via browser)
did i miss a step? does this mean that my isp is blocking 80?  or do I have a setting messed up somewhere?
I realize this may be a question asked often so I did search the ubuntu forums but found nothing that could fix my problem
oi, any help would be appreciated


Did you get the information you were looking for?  I read some interesting (and accurate) replies to your post here and I think we would all like to know if you got this going?

The standard Linksys firmware will allow you to forward port 80 to your webserver as was indicated.  Unless you have setup the router to allow remote (ie: from the Internet) administration it will not respond to http on port 80 anyway.  This is a good, basic security feature of these devices.  Turn off remote administration if it's on unless you really need it.

Sidebar:  
------------------
There are a number of 3rd party firmware projects out there that will allow you to unleash some very interesting, but largely (to you) unnecessary features on the box.  Yes they are Linux, but certainly DD-WRT isn't the only one.

Hyper-WRT, DD-WRT, Sveasoft are others.  Head over to [www.linksysinfo.org](www.linksysinfo.org) for some more information, links and how-tos if you're really interested.

/Eric
webmaster
[www.breezy.ca](www.breezy.ca)

---

