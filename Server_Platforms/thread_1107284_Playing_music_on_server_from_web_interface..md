---
title: "Playing music on server from web interface."
date: 2009-03-26
forum: Server Platforms
---

### Post by neonpolaris on 2009-03-26
Hey guys.  I'm trying to make a very simple web-controlled jukebox of sorts.  I've got Ubuntu 8.10 Desktop running Apache2, PHP5, MySQL, and phpmyadmin all successfully.  I've found a command-line mp3 player, mpg123, which seems right for the job.  It's installed, and it works.  But I've been unsuccessful in getting the web interface to start the program locally.

I've given www-data permission to directly access to the sound device.  I've made a simple php page trying to run 'mpg123 go.mp3'.  I've specified the directories of the program, even copied it to the www folder with the page.  The page does load with no errors, but nothing seems to happen.  I've tried with exec, passthru, and system, but I'm a bit lost.

I've seen some php jukebox software around, but most of them are about streaming to the remote computer, which is not what I want.  The others are too convoluted and feature-rich for me to find what routine actually plays the file.

Also, if I run the PHP from the command line:
php -r "exec('mpg123 go.mp3');"
It works.

Has anyone else done something like this?

---

### Post by volkswagner on 2009-03-26
Check out [Jinzora]("http://en.jinzora.com/").  They have a jukebox mode for local playback.  I uses the MPD.  Even if you don't use jinzora, check out how they setup MPD.

---

### Post by netztier on 2009-03-26
> **neonpolaris said:**
> Has anyone else done something like this?

Can't tell from my own experience, but my brother's been using [ampache]("http://ampache.org/") for quite some time now. It's available from the universe repositories.

regards

Marc

---

### Post by HermanAB on 2009-03-26
The easiest method is with Edna:
[http://edna.sourceforge.net/](http://edna.sourceforge.net/)
[http://aeronetworks.ca/ogg2mp3-howto.html](http://aeronetworks.ca/ogg2mp3-howto.html)

Cheers,

Herman

---

### Post by R.Bucky on 2009-03-27
I have been using Jinzora2 for some time. In my opinion, it offers more configuration options and reliability than other alternatives that I have used. My primary purpose is streaming music from my server at home. It runs beside my hosted web site and proxy server on Ubuntu Server 8.04.

---

### Post by MrWES on 2009-03-27
Might want to look into mt-daapd, it's in the repos and supports sharing in Rhythmbox and iTunes.

Bill

---

### Post by neonpolaris on 2009-04-07
Wow, thanks guys.  I'll have to try these soon, though no time here in the next few days.  I'll report back when I do!

---

