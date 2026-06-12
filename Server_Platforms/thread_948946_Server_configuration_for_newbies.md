---
title: "Server configuration for newbies"
date: 2008-10-15
forum: Server Platforms
---

### Post by davidgrudek on 2008-10-15
Do you guys have a web frontend to configure all the different settings that make it easy for a newbie but keeps the security in a good point since there is no x server running?

If not is there any plans for this?  This would be great.  I love the idea of linux but it is so much to handle at first for a new user.

---

### Post by Throwback on 2008-10-15
Welcome to freedom (linux) my friend! Freedom isn't free though, it takes hard work...

That said you sound like a man in need of Webmin. Webmin allows extensive configuration of your server from a web interface, and if you set your router up correctly, you can admin the thing from anywhere with an internet connection. Even a mobile phone with a browser!

Be warned though, you cannot avoid the shell all the time but it will give you a leg up. Also bear in mind- the first thing you must learn to configure is the firewall- it is turned off by default!

I will prolly incur some ire for posting debian instructions instead of ubuntu but these have worked for me, as long as you take CARE to READ the whole page and UNDERSTAND the differences between Ubuntu and Debian. [http://www.webmin.com/deb.html]("http://www.webmin.com/deb.html")

To get Webmin on there you will still need to spend some time at the prompt:
In short:

Either become root or run all commands as root (using sudo)
Backup /etc/apt/sources.list
Edit /etc/apt/sources.list to enable the universe repositories and add the webmin debian repository.
Run apt-get update to get the system to acknowledge the new software sources
Run apt-get upgrade to make sure everything is up to date
Install the dependencies for webmin
Install webmin 

Webmin is not in the the main universe or multiverse repositories but I am using the version from the webmin debian repository without issue. Bear in mind Webmin has its own issues but it still saves a lot of time at the prompt. Mind you, I consider myself a n00b and I have been using linux on and off for about 8 years.

Learning the shell is still a definite must if you intend to spend any time with linux though.

Its late here so thats all for now, you will need to read around to elaborate on these instructions. Message me if you wish. I have only recently moved from being a n00b to knowing just enough to cause some mayhem so I feel you are in roughly the position I was in a year ago.

---

### Post by brian77095 on 2008-10-15
Not exactly sure what you are wanting?  Are you looking for a web site to show you how to set up a web server??

If so there are plenty...  Start here.

[http://www.aboutdebian.com/index.htm](http://www.aboutdebian.com/index.htm)

It will be a lot of reading but, worth it.

---

### Post by lykwydchykyn on 2008-10-16
I don't recommend installing webmin through any repository.  I used to do that back on Debian sarge, but because webmin has its own updater built in, I had problems with the repositories overwriting newer versions with old versions.

ebox is another option for a web based interface.  It's different from webmin, both have their uses.  ebox seems more integrated and abstracted than webmin, which is good in some ways but doesn't seem to sit well with an existing config.  Webmin is more a-la-carte, so to speak, and just sort of lays out the config options without much explanation or abstraction.

I've used webmin a lot longer, still getting a handle on ebox.

---

### Post by Kellemora on 2008-10-16
Hi DG

I'm brand new too and just downloaded Edubuntu since it sets itself up and I figured from there I can figure out what it changed so I can learn WHY.

Figured if I was going to give it a try, try it with something that will run out of the box, hi hi.........

Lot's of documention to read over at Edubuntu too!  In simple language even I can understand.

TTUL
Gary

---

