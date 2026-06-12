---
title: "Radio"
date: 2008-09-11
forum: Ubuntu Brainstorm
---

### Post by wolterh on 2008-09-11
Besides knowing that most of the music players that are available for linux have the capability of playing internet music streams, I think that it would be very nice to have an application coded specially for listening to "radio stations".

Why?
-To keep a list of the "stations" you hear
-Small, compact, yet comfortable GUI
-Save RAM by not having features that you do not need while listening radio streams (Features that most multimedia players have and invest ram in)
-Its quite simple to do

Why not?
-No reason

I already have a GTK GUI design. Check it out:
[http://img84.imageshack.us/img84/1203/radiojm9.png](http://img84.imageshack.us/img84/1203/radiojm9.png)
The buttons are related to the stations
The chooser is to select the station
The empty space is for a buffer progress meter

I do not know if this is the correct place, but the project is open for anyone who wants to join. If necessary, we could make a google project to host it...

---

### Post by Whiffle on 2008-09-11
Like Streamtuner?

[http://www.nongnu.org/streamtuner/](http://www.nongnu.org/streamtuner/)


No longer being activly developed, but it worked well last time I used it.

---

### Post by wolterh on 2008-09-11
Wow... that was quick...
I searched and searched for an application that was dedicated to listen internet music streams, and found nothing. I even posted a query for this application type in this forums, but people just started hiting me with music players.

Thanks. 

Anyway, if someone wants to do the project, we could even make a cooler radio application and apply for it to be included in the ubuntu built-in applications.

---

### Post by wolterh on 2008-09-11
Well... I've downloaded it and it requires xmms, and I guess that it also requires realplayer and other applications... 
I think that the radio application is actually needed. This player is very outdated...

---

### Post by xebian on 2008-09-11
> **woli said:**
> Wow... that was quick...
I searched and searched for an application that was dedicated to listen internet music streams, and found nothing. I even posted a query for this application type in this forums, but people just started hiting me with music players.

Thanks. 

Anyway, if someone wants to do the project, we could even make a cooler radio application and apply for it to be included in the ubuntu built-in applications.


sudo apt-get install streamtuner

---

### Post by wolterh on 2008-09-11
I did it that way, but many dependencies were not installed.
For example: xmms, which required glib, another dependency not installed, and not available at the repository. I think that there is a chain of dependencies that every user willing to have a simple radio application will have to search and download. There should be an application that will use non-outdated libs.

---

### Post by Whiffle on 2008-09-11
Yeah streamtuner uses XMMS for tuning in the actual streams, its more of an organizer.  You might email the guy, maybe he'd be open to someone taking over.

---

### Post by xebian on 2008-09-11
> **woli said:**
> I did it that way, but many dependencies were not installed.
For example: xmms, which required glib, another dependency not installed, and not available at the repository. I think that there is a chain of dependencies that every user willing to have a simple radio application will have to search and download. There should be an application that will use non-outdated libs.

What's wrong with outdated?  As long as it works, it should be fine.  You may have to enable universe/multiverse.

---

### Post by smartboyathome on 2008-09-11
> **woli said:**
> Besides knowing that most of the music players that are available for linux have the capability of playing internet music streams, I think that it would be very nice to have an application coded specially for listening to "radio stations".

Why?
-To keep a list of the "stations" you hear
-Small, compact, yet comfortable GUI
-Save RAM by not having features that you do not need while listening radio streams (Features that most multimedia players have and invest ram in)
-Its quite simple to do

Why not?
-No reason

I already have a GTK GUI design. Check it out:
[http://img84.imageshack.us/img84/1203/radiojm9.png](http://img84.imageshack.us/img84/1203/radiojm9.png)
The buttons are related to the stations
The chooser is to select the station
The empty space is for a buffer progress meter

I do not know if this is the correct place, but the project is open for anyone who wants to join. If necessary, we could make a google project to host it...

Why not:
-Repetitive
-Waste of disk space
-It is more code, which means more bugs

---

### Post by irrdev on 2008-09-12
Rythmbox already does all this, and includes a small (but editable) list of popular internet radio stations. Sure, the interface maybe a bit overblown for just listening to radio, but Rythmbox by default adds an icon to the notification area where you can minimize it to. There is absolutely no need for duplicating this functionability on the LiveCD.

---

### Post by wolterh on 2008-09-12
Well... maybe it is not worth to put it as a built-in application. You are right. Anyway, I just wanted to see if I could recruit some team for the project.

---

