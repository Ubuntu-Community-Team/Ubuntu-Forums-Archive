---
title: "Setting up an Ubuntu Server"
date: 2011-10-12
forum: Server Platforms
---

### Post by jsbailey on 2011-10-12
Hi all,

Let me preface this thread by stating something: I'm not here looking for hand-holding or someone to walk me through what I'm asking step-by-step, so please don't mistake my questions for laziness on my part. I'm merely someone new not only to Linux/Ubuntu, but to setting up a server. I am not a novice computer user, however.

I think the easiest way to lay this is out is to explain the current situation, and what it is I want to do. So here goes:

My company sells old PC's that it doesn't need for a quite generous price. I picked up one of these a few months ago and decided to set myself up a web server. I got one set up and it works well enough, but I want to go bigger. I'm a PC gamer and play with a core group of friends, and we always set up a guild/clan/what have you, and I'd like to host a website for us with all the trimmings (forums, database for dkp/whatever). I'll also likely host a small blog for my general ramblings, but that's an afterthought. So then I got to thinking, I wouldn't mind an e-mail server, too. And maybe even a small Ventrilo server. This leads me to my question(s). I've got the web server set up easy enough, but it's taking it to the next step that I have trouble with.

--Is it possible to host a web server, e-mail server, and Ventrilo server all on the same machine? Are there any guides for setting up a web server and e-mail server on the same machine?
--What kind of specs (storage/bandwidth/etc.) do I need for each?
--How easy is it to manage accounts for other users, and their permissions (for instance, can I give someone access to the guild web server files to update/create/delete but not to be able to touch say my blog directory)?

Thanks for any help/tips/advice. It is greatly appreciated.

---

### Post by The Sorrow on 2011-10-12
1. Yes. I do the same thing except the email. I run it on a Pentium 4 with 4 GB ram and it runs fine. I have Cox 12 Mbps service. Storage is up to you and depends on your userbase. 

2. Managing accounts on an email server is the same thing as managing users on a linux machine (Depending on the program).

---

### Post by Lisiano on 2011-10-12
1) Just follow the guides that assume you are using this server as just for that, Linux has no problems running 3 or even 30 services, as long as the CPU, RAM and space can sustain that.
2) Web server, around 10Mbps for smooth loads but can be used even on 1Mbps. E-Mail, anything above 256Kbps. Ventrilo depends on what codec you wish to use for voice compression, the higher the quality the more bandwidth, usually you can host loads of people on the lowest one and keep it under 512Kbps (On TS at least). The more people and the higher the quality, the more bandwidth, also note that if more than 1 person speaks at the same time in the same room, more bandwidth is used.
3) "Set up and forget" <-- usually that hard. But you do have to use a CMS for both.

---

### Post by The Sorrow on 2011-10-12
Google is amazing for tutorials. Just stick "<service> setup <operating system>" and a number of how-tos pop up. theyre usually step by step. just add your own customizations to the steps in the tutorials.

---

### Post by jsbailey on 2011-10-12
Thanks for the replies so far. Few questions/comments:

1. What is a CMS?

2. I did precisely the Google method mentioned before to setup my web server, but I find that most of them are outdated and small alterations are necessary to complete the process for current versions of Ubuntu.

---

### Post by collisionystm on 2011-10-12
Use Zentyal.

[www.zentyal.com](www.zentyal.com)

based on ubuntu 10.04. It is a god.

---

### Post by Lisiano on 2011-10-12
CMS - Content Management System, that is stuff like Wordpress, Drupal, Joomla, etc.

---

### Post by SavageWolf on 2011-10-12
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

This is the official server guide from the documentation.

Note that much of the stuff on networking expect you to have a machine in a room connected directly to the ISP or some such. If you are using your home network, you can just connect it to the internet in the "usual" way (However, probably from a command line). You don't really need a knowledge of TCP/IP or such.

---

### Post by collisionystm on 2011-10-12
[http://www.zentyal.com/en/server/infrastructure/](http://www.zentyal.com/en/server/infrastructure/)

Look at screen shots.

I would use this.

You can install wordpress on it with sudo apt-get install wordpress. Email and web server all managed in the web interface.

---

### Post by SavageWolf on 2011-10-12
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

This is the official server guide from the documentation.

Note that much of the stuff on networking expect you to have a machine in a room connected directly to the ISP or some such. If you are using your home network, you can just connect it to the internet in the "usual" way (However, probably from a command line). You don't really need a knowledge of TCP/IP or such.

Edit: Yay! Slow internet... And bugs!

---

### Post by oldos2er on 2011-10-13
Thread moved to Server Platforms.

---

