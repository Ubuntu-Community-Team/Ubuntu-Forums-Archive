---
title: "Interesting Article"
date: 2007-04-18
forum: The Cafe
---

### Post by Blather_X on 2007-04-18
Here's a bit on encouraging news. (Everyones "favorite" flavor of Linux)   I got this in an email  this morning.  

From an experienced users point of view this information might be ''old hat''  (as opposed to ''red hat''... HA... sometimes I crack myself up)  But as a new user I found this to be an interesting read.  

Take a look and let me know what you think.  Is the information good, bad, usable?


Here's the blurb:

*If you've been thinking of moving to Linux, consider Ubuntu. It's simple to install, comes with lots of powerful features and drivers, and it just works well. But if you've been using it for a while, or if you're a newbie, you know there are always ways to tweak and improve any system. So we've put together our favorite lists of tweaks on how to optimize Ubuntu. Check it out; it's a great way to get more from what's becoming everyone's favorite flavor of Linux.*

```

```[http://www.extremetech.com/article2/0,1697,2114115,00.asp](http://www.extremetech.com/article2/0,1697,2114115,00.asp)

---

### Post by karellen on 2007-04-18
pretty useful...:)

out of topic: I like your avatar, silver surfer is one of my favourite comic superheroes :D

---

### Post by ArtificialSynapse on 2007-04-18
Good to hear, that book looks really cool! Hope it's online somewhere.

---

### Post by jamesrl on 2007-04-19
Be a little careful with this article, and be sure to check the comments as there are mistakes in the article.  One comment from an Ubuntu developer corrects at least several blatant errors.  I discussed two here in the [thread (http://ubuntuforums.org/showthread.php?t=410927)]("http://ubuntuforums.org/showthread.php?t=410927") on this from yesterday.  

First, by default both edgy & feisty (and probably dapper & breezy as well, though I never had more than 1 Gb of ram with either) are able to have systems with more than 1 Gb of RAM and use them well (I am running 7.04 with 2 Gb [see previous thread]) and it utilizes all the memory properly (without swapping) [Whereas his article incorrectly states its worthless to use ubuntu with more than 1Gb of physical memory).  Second, there are important cron jobs enabled by default on the installation (for example look in the /etc/cron.daily /etc/cron.weekly /etc/cron.monthly /etc/cron.hourly directories) and you will see scripts do various things periodically (such as updates the locate database (so you can quickly search for files), or resync the package descriptions for apt).  He also sort of mischaracterizes anacron (which just makes sure cron jobs have been run periodically for systems that aren't up all the time), saying you should just move the anacron jobs to cron (and he said you could disable cron if you want as it doesn't do anything by default).  If you look in the cron directory and /etc/anacrontab you'll see that anacron runs the scripts daily if you machine isn't continuously on.

---

