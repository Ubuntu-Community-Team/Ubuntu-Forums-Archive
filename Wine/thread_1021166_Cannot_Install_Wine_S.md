---
title: "Cannot Install Wine :S"
date: 2008-12-25
forum: Wine
---

### Post by Dan_Sheen on 2008-12-25
Hello, I am about to show you the error I get when I attempt to install Wine.

Yes, I am new to Ubuntu, and I am just starting, with getting familiar with the controls and how it works, but can someone help me please?

---

### Post by dino99 on 2008-12-25
> **Dan_Sheen said:**
> Hello, I am about to show you the error I get when I attempt to install Wine.

Yes, I am new to Ubuntu, and I am just starting, with getting familiar with the controls and how it works, but can someone help me please?

hi,
and happy new year,

first, stay cool, read how to install it using synaptics, add what needed in sources.list (all is clearly explain on your sreenshot: repositery and scottie key, that's all !!!)

it's better if you do only one thing at a time: i've seen that you have several instances opened (cs, winehq, softpedia, ...)
... if you want broken things, that's the way !!!

So, close every thing and reboot first. then go on [www.//winehq.org](www.//winehq.org) and follow the instructions .

---

### Post by namdung on 2008-12-25
Pls use Add/Remove Applications to search & install WINE. Ensure *All Available applications* is selected in *Show* dropdown.

---

### Post by Meow27 on 2008-12-25
well if you are willing to sacrifice your bandwith and your hard disk space,

open up the terminal and type the following

```
sudo apt-get install -f
``` (to remove broken packages)
and then
```
sudo apt-get build-dep wine
```( to install every main dependency for wine, this is a messy way since this also installs the development files (which are needed if you want to compile wine from the source code))

mind i also reccomend using this site for downloading wine deb packages? 
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)


EDIT----------------
if you are going to be using that site, DONT download wine 1.1.10 (the menus are bugged in that version!) either 1.1.9 or 1.1.11 (assuming it came out)
have fun

---

### Post by Dan_Sheen on 2008-12-26
Thank you so much, I will choose your way :D

Update- Yes, installed perfectly, thank you:D

---

