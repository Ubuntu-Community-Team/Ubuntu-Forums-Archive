---
title: "Two problems with USP and Edgy"
date: 2006-11-13
forum: Ubuntu System Panel
---

### Post by shiversc on 2006-11-13
afte installing usp on my brothers ubuntu edgy he have two problems.

first: between the usp and the gnome-panel are a little free border. i think 5 px. how can i get the usp nearly the panel?

second: whenn i open the usp and choose a application, the usp don't close itself automaticly. 

on a dapper maschine are no border and usp close direcly after choosing a application.

sorry for my bad englisch and thx for the help.

greetings from germany.

---

### Post by stalker145 on 2006-11-13
As I'm not in front of my computer at the moment (durn Win2K at work) I may be a little off on my response, but here it goes...


> **shiversc said:**
> first: between the usp and the gnome-panel are a little free border. i think 5 px. how can i get the usp nearly the panel?

There is a setting that states border width within the USPconfig file that is downloadable from [here]("http://ubuntuforums.org/showthread.php?t=272372") that should be able to help you out.

> **shiversc said:**
> second: whenn i open the usp and choose a application, the usp don't close itself automaticly.

If you toggle the button on the upper-left corner of the USP window, that should take care of this problem. 

I hope this helps... hell, I hope it's accurate ;)

---

### Post by Malac on 2006-11-13
Open gconf-editor and go to /apps/usp change the value panel_size to 1 and see if that helps.

---

