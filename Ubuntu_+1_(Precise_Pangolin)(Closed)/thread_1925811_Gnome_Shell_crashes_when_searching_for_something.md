---
title: "Gnome Shell crashes when searching for something"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sauferkel on 2012-02-15
Hey everybody
i installed the Gnome shell on 12.04 and it often crashes if I type something into the search field. Anybody the same problem? How can i find out whats going on there? 

cheers
henning

---

### Post by dino99 on 2012-02-15
did you got a crash ? look at /var/crash/, if there is one, then right click on it and select "send this problem" or so. If you receive an error saying "you are not the owner of this file" or so, then into a terminal:


sudo chown user:user /var/crash/*
(replace user:user by your login)

and try reporting again, you'll be asked to create an launchpad account if you dont have one yet.

---

### Post by sonicb00m on 2012-02-15
Nautilus crashes for me whenever I try to do a search. Been like it for ages.

---

### Post by sauferkel on 2012-02-15
okay, thank you , that's what i was looking for.

i'll report it :)

---

### Post by PaulW2U on 2012-02-15
> **sauferkel said:**
> Hey everybody
i installed the Gnome shell on 12.04 and it often crashes if I type something into the search field. Anybody the same problem? How can i find out whats going on there? 



I had a crash yesterday when Gnome Shell couldn't find an application because I spelt its name incorrectly. Is that what you are seeing or is it on searches where you've only partially typed the application's name?

---

### Post by dino99 on 2012-02-15
Send report & let us know about its number please.

---

### Post by OGpmpdog on 2012-02-15
> **sauferkel said:**
> Hey everybody
i installed the Gnome shell on 12.04 and it often crashes if I type something into the search field. Anybody the same problem? How can i find out whats going on there? 

cheers
henning

Hi,

I'm having the same issues on my T61 laptop.

I press the super button, and start typing to search, and system just hangs, and eventually crashes.

---

### Post by k@e on 2012-02-17
Which version of the NVIDIA driver does Ubuntu + 1 ship with?

If it's 295.17 or newer, you may be affected by the same bug as some Fedora and Arch users. The problem is described [[COLOR="DarkRed"]here[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2529340").

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-17
I have the same problem. Acer Aspire TimelineX 5830TG, Intel graphic card.

---

