---
title: "the best p2p client"
date: 2006-06-17
forum: The Cafe
---

### Post by tompouce on 2006-06-17
Hi!

I want your opinions on which is the best p2p client?

And don't say Limewire, it's a java piece of crap, everything java is too slow, I want something nice, the only one that I've found is gtk-gnutella.

Thanks

---

### Post by jc87 on 2006-06-17
I used Azureus in the past for .torrents , but it is buggy , resources hog , the GUI is bad designed in some areas (i installed recently the latest version in the Dapper repositories , the GUI "redesigners" must be smoking some really bad crack) , and "stupid" (a Gnu/Linux app that tries to self update itself :confused: )

I´m now using the Bitorrent utility that comes with Dapper for some time now , a little too simple for my taste , but it works , and that is what matters.

Amule is also good for ed2k stuff.

---

### Post by Kernel Sanders on 2006-06-17
[QUOTE=jc87]I used Azureus in the past for .torrents , but it is buggy , resources hog , the GUI is bad designed in some areas (i installed recently the latest version in the Dapper repositories , the GUI "redesigners" must be smoking some really bad crack) , and "stupid" (a Gnu/Linux app that tries to self update itself :confused: )

I´m now using the Bitorrent utility that comes with Dapper for some time now , a little too simple for my taste , but it works , and that is what matters.

Amule is also good for ed2k stuff.[/QUOTE]

I heard uTorrent runs well under wine?

---

### Post by Somenoob on 2006-06-17
I use uTorrent, i run it under Wine.

---

### Post by lapsey on 2006-06-17
i have no problem with azureus on a 400Mhz debian sarge box

---

### Post by Cynical on 2006-06-17
Use frostwire, its not slow like you've been describing and its more convienant for downloading the one or two songs you heard on the radio.

[www.frostwire.com](www.frostwire.com)

Cant believe ubuntu has its own package :)

---

### Post by Johnsie on 2006-06-18
I'm using apollon with Ares, Gift, Kazzaa(Fasttrack) and Gnutella all at the same time. It takes a bit of configuration but I think it's worth it. Here's how I do it:
[B]
1. Make sure you have the restricted respositories enabled in your /etc/apt/sources.list[/B]
If you don't know how to do that then ask someone here or on xchat. One easy way to know if it's enabled is by going into the terminal and typing
apt-cache search ares plugin
If that finds the ares plugin for gift then you know you have them enabled.

**2. In the terminal type:**
sudo apt-get update
sudo apt-get install gift libares-gift libfasttrack-gift apollon

**3. The  following instructions must be carried out by each individual user. In the termnial type:**
gift-setup


**You'll get asked a bunch of questions. You can ignore most of them but you might want to change the folder downloaded files go into and you definitely need to answer the following:**

***THE MOST IMPORTANT PART IN THIS BIT IS TO MAKE SURE YOU TYPE IN THE FOUR NETWORKS WHEN IT ASKS YOU WHICH PLUGINS TO USE****

**Ares:Gnutella:FastTrack:OpenFT**

Remember that it's case sensitive you you have to have your capital letters in the right places.

After that you can just keep hitting return and then run apollon from the terminal by typing:
apollon

(if apollon fails to connect the first time close it, type *giftd* in the terminal and try opening it again. You will only ever have to do that once)

Yes, it may take a few minutes to set up but in the long run it's definitely worth it because you have access to all the major filesharing networks and a pretty decent gui.

---

### Post by nalmeth on 2006-06-18
Combo Ktorrent and Apollon.

I didn't have to add extra repos to install the fasttrack and ares plugins, i think they are in the restricted repos. Always best to make a habit of stickin to the ubuntu repos when possible.

---

### Post by Iandefor on 2006-06-18
Bittornado works like a charm for me.

---

### Post by Johnsie on 2006-06-18
ah you're right... I must've had a bad sources list the first time I did it or it wasn't on there then.... I'll update my post :-)

---

### Post by Johnsie on 2006-06-18
It would be nice if someone wrote some sort of script to do that automatically.

---

### Post by benplaut on 2006-06-19
[QUOTE=Johnsie]It would be nice if someone wrote some sort of script to do that automatically.[/QUOTE]

did what, change your sources.list?

try either Automatix or Easy Ubuntu... they both are in 3rd party projects.

And for goodness sake, don't ask which is better! #-o

---

### Post by Johnsie on 2006-06-19
lol, that's pretty much what automatix does anyway.... I've already asked them to add gift. 

However it would also be nice if it configured gift as well as intalled it. That would save time. There's no point doing things manually when you can have a script do it. Not everyone in the world has time to fiddle about :-)

---

### Post by nalmeth on 2006-06-19
I agree, it's odd, because anyone installing apollon for the first time (even without installing extra gIFT plugins) is required to tell apollon where the gIFT plugins reside. 

8/10 people picking this up will have to look it up.

It must have to do with accounting for differences in filesystems + distros.

I think debian is the same, but I couldn't say for sure about any non-debian-based others...

---

### Post by yaztromo on 2006-06-19
Amule 2.1 for KAD and Edonkey network.

Ktorrent for torrenting. It's installed by default in Kubuntu and really is amazing.

---

### Post by ricoris on 2008-06-04
Hi! 
I'm a beginner with ubuntu and I'm trying to find a good p2p program and install it. I installed Frostwire but it doesn't seem to work very well...it doesn't find much and it's quite slow (I don't if this is related to the fact that I have an old version of ubuntu because of a graphic problem or has other reasons). Somehow (I didn't really know what I was doing) I installed something called giftui. When I start it says: connection to localhost:1213 failed. Then there is a place with the label 'host' and there it says 'localhost' but you can write other things if you want and below there are different option with numbers like 1213, 1212, etc. I am really confused somebody can help me out?

---

### Post by gameryoshi600 on 2008-06-04
Transmission. and why does everyone hate Java? Java can get you a good job.

---

### Post by BuffaloX on 2008-06-04
Amule is very good.
Native Linux version of emule.
it even handles large files up to 8 GB.

---

### Post by ghindo on 2008-06-04
KTorrent is pretty rad.  I just wish it was a GTK application. :(

---

### Post by gameryoshi600 on 2008-06-04
No one has answered my question. but thats ok I just want to know why lots of people hate java apps. java can get you a good job

---

### Post by ghindo on 2008-06-04
> **gameryoshi600 said:**
> No one has answered my question. but thats ok I just want to know why lots of people hate java apps. java can get you a good jobJava applications are larger and more resource-intensive than applications written in lower-level languages like C.

---

