---
title: "Server, how much time do you spend on server maintenance?"
date: 2009-11-17
forum: Server Platforms
---

### Post by Torning on 2009-11-17
How much time do YOU spend on keeping your Ubuntu webserver running?

I need a web server (to host multiple sites). I have been using several shared hosts, but I am not impressed. I would also like to install some video streaming software and a php cache system and basically have some more options, and in particular SPEED. 

So I took at look at [http://www.serverpronto.com/compare.php](http://www.serverpronto.com/compare.php) their minimum package looks good to me. However.... and this is a big one for me. I can't spend too much time upgrading and updating various programmes. This is not my core expertise. I like to fiddle with HTML and some PHP and making small videos that I put online. 

Question 1: Is maintaining a Ubuntu server as easy as maintaining a basic Ubuntu desktop? Will the server just tell you to update and you just say "OK Ill update" then reboot and thats it - OR do you need to do more when running a Ubuntu/apache web server?

Question 2: When Ubuntu 9.X comes out, can I just update my whole server easy? Or would I need to tweak all sorts of config files and have (considerable) downtime on my sites? 

Question 3: Do I need to worry too much about security? I have been looking at the "Uncomplicated Firewall", it looks uncomplicated ;-) Do I really just need to set up the box and allow for FTP and HTTP? Is that it, or do I need to read a bunch of security tutorials...?

Sorry for the long post, but I need to know :popcorn:

---

### Post by cdenley on 2009-11-17
If speed for remote users is your concern, especially with streaming video, then your internet connection is almost always going to be your bottleneck. If you're going to host your own server, what kind of internet connection will it have?

---

### Post by Torning on 2009-11-17
> **cdenley said:**
> ...what kind of internet connection will it have?

"All ServerPronto customers are connected via their own 100Mbps cross connection to Infolink's switches which have redundant Tier-One backbone connections." - It will be fast. I have a friend that uses them with success.

My current bottle neck is that I am on a shared host. I cant really install i.e. APC (Alternative PHP Cache).

Anyway, I need to know how much time you typically have to allocate to maintaining the actual server. 

Questions 1-3... :-)

---

### Post by cdenley on 2009-11-17
1. If you stick to the repo's, then you just need to make sure the security branch is enbaled, the do a "sudo apt-get update && sudo apt-get upgrade" whenever a security notice is made that you need to fix. Some people also monitor logs and use intrusion detection utilities, though. You shouldn't need to do much between upgrades.

2. The upgrade between one release and the next, or one LTS release and the next, should be easy, but might take while.

3. You don't need to worry about a firewall, though it couldn't hurt. Most importantly, configure any server you run correctly.

---

### Post by HermanAB on 2009-11-17
Zero time...

Most Linux trouble is finger trouble. If you leave a Linux system alone, then it will run until the hardware fails after 3 to 5 years.

---

### Post by prsjm3qf on 2009-11-18
Very little.

Just keep an occasional eye on the logs but if it's working don't fix it.

---

