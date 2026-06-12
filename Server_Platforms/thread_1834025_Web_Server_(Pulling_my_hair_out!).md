---
title: "Web Server (Pulling my hair out!)"
date: 2011-08-26
forum: Server Platforms
---

### Post by Watchlord on 2011-08-26
First off let me say: Yes, I am a total Ubuntu noob. I've been running 11.04 pretty well on my netbook though. I'm also worn out; the hum of this server is becoming horrible. Please excuse any weirdness.

Here's the situation. I recently bought a new machine \/

HP Proliant DL380 G3
4GB RAM
2x Zeon 3.06ghz
3x 73GB HDD @ 3x RAID 0 (Don't tell me that's stupid, I want 3 non-RAID drives and that was the only way.)
Ubuntu Server 11.04 w/ GNOME Desktop

Anyway, my goal is to migrate my website which includes a glype proxy from my old xp machine running xampp (I know it's insecure, but I'm not running a high profile server here.). I'm totally lost. I have everything (pages, glype, passwords, etc.) perfectly configured in my (I forgot the directory name for index.html) folder. What do I have to do to move this and make it work? What about DynDNS client? Will I have to spend weeks learning how to run all this by command line with Lamp? I have no problem wussing out and switching back to XP to save me alot of headaches. I love Ubuntu, but I'm just totally lost.

I also want to run a Minecraft server with Bukkit. After a few hours no longer think running an MC server in Linux is a good idea. Looks like I'm going to have to use VMWare because Wine is giving me errors too.

---

### Post by Iowan on 2011-08-27
Moved to Server Platforms

---

### Post by meastwood on 2011-08-28
I'm not sure ... the default Apache install should have your DocumentRoot in
/var/www

First - on your ubuntu open up your browser and point it to 
[http://localhost](http://localhost)

Should get a page with something like - It's working .... i.e. Apache server is working.

Then try copying everything on your old laptop - from where your index.html file is to /var/www.  Then take a look at in a browser

As for Bukkit - don't know, looks like java as it comes in  a .jar.  May need to install that anew.

DynDNS - no problems I use that.  Just use the software they suggest -
e.g. [http://dyn.com/support/clients/linux/](http://dyn.com/support/clients/linux/)

---

### Post by Watchlord on 2011-08-28
I already figured it out. Seems all I needed was some sleep. Anyway, I've run into a whole set of new problems that I recently made a post about. Thanks alot though.

---

### Post by Wim Sturkenboom on 2011-08-28
Please post the solution; can be useful for others.
Please mark the thread as solved using the thread tools just above the first post on this page.

---

### Post by Watchlord on 2011-08-28
I simply reinstalled LAMP. As for Minecraft, bukkitcraft works, but the server software provided my Mojang doesn't.

---

