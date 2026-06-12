---
title: "Music player error messsage &quot; no plugin installed&quot;"
date: 2004-12-04
forum: Repositories &amp; Backports
---

### Post by ryan on 2004-12-04
In music player I browse to a location where I have MP3 s a try to load them and tthe message that I get is "There is no plugin installed to handle a MP3 file. Am I doing something wrong obviously. I used the same program with FC2 and 3 and NP at all. I am a ubuntu mewbie and need some help, so far I like very much what I have seen. tks

---

### Post by ryan on 2004-12-04
Ok found the solution in one of the other forums..

HOWTO: Tweaking Ubuntu after your first installation.

Enable MP3 support in Rhythmbox.
Quote:
1. sudo apt-get install gstreamer0.8-mad

or what I did was:

Enable Universe in Synaptic.
Quote:
From your desktop select Computer > System Configuration > Synaptic Package Manager you will be asked to enter your password. Goto Settings > Repositories you will see (2) grayed out boxes click both of them, then click the Reload button.

then select gstreamer0.8-mad to install and it makes sure that all the dependencies are there as well very cool great job..

---

### Post by poofyhairguy on 2004-12-04
[QUOTE=ryan]Ok found the solution in one of the other forums..

HOWTO: Tweaking Ubuntu after your first installation.

Enable MP3 support in Rhythmbox.
Quote:
1. sudo apt-get install gstreamer0.8-mad

or what I did was:

Enable Universe in Synaptic.
Quote:
From your desktop select Computer > System Configuration > Synaptic Package Manager you will be asked to enter your password. Goto Settings > Repositories you will see (2) grayed out boxes click both of them, then click the Reload button.

then select gstreamer0.8-mad to install and it makes sure that all the dependencies are there as well very cool great job..[/QUOTE]


Welcome ryan, I'm glad you got what you want. If you want a good video file player, I suggest gxine.

---

### Post by bob k on 2004-12-05
better yet mplayer man that thing rocks. I'm still going thru the setup thing to figure the best screen resilutiion. I haven't figured  out how some of the options work, but that will come with time.

When you down load it and compile and install it, there is a wiki and a how to, it's prettty straight foward. Play with it for a couple of days and then copy the *cofig to your home  (~) I found the location /usr/local/etc/mplayer/example.conf and copy it to your ~ then edit (I guess edit ain't the right word play with it is the right word) then have fun

---

### Post by Marauder1 on 2004-12-05
The best duo is : 

- Mplayer and Plugins for movies
- Xine for DVD

With this you can see anything 
 :-D

---

### Post by brammoreinis on 2005-01-01
[QUOTE=ryan]Ok found the solution in one of the other forums..

HOWTO: Tweaking Ubuntu after your first installation.

Enable MP3 support in Rhythmbox.
Quote:
1. sudo apt-get install gstreamer0.8-mad

or what I did was:

Enable Universe in Synaptic.
Quote:
From your desktop select Computer > System Configuration > Synaptic Package Manager you will be asked to enter your password. Goto Settings > Repositories you will see (2) grayed out boxes click both of them, then click the Reload button.

then select gstreamer0.8-mad to install and it makes sure that all the dependencies are there as well very cool great job..[/QUOTE]
 Hi, Ryan.

I'm a newbie, so...  I didn't see gstreamer0.8 -mad in the SPM - it went from -jpeg to -mikmod. 

I clicked all the grayed out "repository" buttons, except the two that said, "These are universe repositories and won't work with your system".  

Should I have checked them? Or is this a moving target? 

I haven't used these forums yet, so don't know if I'd get an email when you replied.  If I would, fantastic - if not, please email to [email]bram@cousinit.org[/email].

thank you!

---

### Post by podmf on 2005-02-26
[QUOTE=ryan]Ok found the solution in one of the other forums..

HOWTO: Tweaking Ubuntu after your first installation.

Enable MP3 support in Rhythmbox.
Quote:
1. sudo apt-get install gstreamer0.8-mad

or what I did was:

Enable Universe in Synaptic.
Quote:
From your desktop select Computer > System Configuration > Synaptic Package Manager you will be asked to enter your password. Goto Settings > Repositories you will see (2) grayed out boxes click both of them, then click the Reload button.

then select gstreamer0.8-mad to install and it makes sure that all the dependencies are there as well very cool great job..[/QUOTE]
 I installed gstreamer-mad and, eventually, all gstreamer-plugins ... but had no joy at all :-(

Any ideas?

---

### Post by ups on 2005-02-26
[QUOTE=podmf]I installed gstreamer-mad and, eventually, all gstreamer-plugins ... but had no joy at all :-(

Any ideas?[/QUOTE]
 What error did you get after installing those? Remember you should install gstreamer0.8-mad (and not gstreamer-mad).

---

### Post by dsa3 on 2009-09-11
i need music player plugins

---

### Post by dsa3 on 2009-09-11
> **dsa3 said:**
> i need music player plugins
i need gstreamer0.8-mad

---

