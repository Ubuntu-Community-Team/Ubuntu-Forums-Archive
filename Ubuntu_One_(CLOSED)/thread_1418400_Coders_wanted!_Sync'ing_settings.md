---
title: "Coders wanted! Sync'ing settings?"
date: 2010-02-28
forum: Ubuntu One (CLOSED)
---

### Post by kaffemonster on 2010-02-28
I think I have a great idea but I am sure I don't have the skills/insight to implement it, so here's to hoping I'm not the only one who thinks this would be cool :)

Pretty much all settings in Ubuntu and programs running under Ubuntu are stored in flat files. Personal settings are stored in hidden folders under /home/username, ie my thunderbird config is stored in /home/ssn/.mozilla-thunderbird

Ubuntu comes with Ubuntu One... so here's what I thought: Wouldn't it be possible to sync all those settings over Ubuntu One? So that your settings are the same on all the Ubuntu machines you use? I'm currently on 3 different machines, but imagine if after a fresh install of ubuntu you only had to sync with The Ubuntu One Settings Thingymajig and your box would be set up just the way you like it? In addition to up/downloading settings files, you could add a runonce script like runonce.sh. The first thing I do after a fresh install is this:

```
sudo apt-get remove empathy && sudo apt-get install thunderbird pidgin ubuntu-restricted-extras filezilla gparted exaile ufraw scite vlc audacious
```

To wrap up my ramblings, here's what I'd love: A script (possibly w. a gui) that either up or downloads a predefined list of files and folders to Ubuntu one and runs the runonce.sh script.

Result: My usual tools are installed and my settings are applied. Automagically.

---

### Post by DedMoroz on 2010-02-28
Its a great idea. Im sure thats what cloud computing of the future is all about. All your data is stored online and you just dump whatever OS, Ubuntu, Google OS, Mint, Mac, XP, whatever you want and no big deal.

Someone will come along with your idea, or Ubuntu is already working on it. Alternatively, you COULD make your own ISO with your programs you want already and just use that disc whenever you want to do a fresh install.

I used to be against cloud computing, but this whole weekend Ive been cleaning up my data, removing duplicate stuff, and seeing where I stand and how much GB of online storage I would need. If you have sensitive data you dont want in the cloud, you just store them on your system or on a USB drive like I am doing now.

---

### Post by joshuahoover on 2010-03-01
> **kaffemonster said:**
> I think I have a great idea but I am sure I don't have the skills/insight to implement it, so here's to hoping I'm not the only one who thinks this would be cool :)

Pretty much all settings in Ubuntu and programs running under Ubuntu are stored in flat files. Personal settings are stored in hidden folders under /home/username, ie my thunderbird config is stored in /home/ssn/.mozilla-thunderbird

Ubuntu comes with Ubuntu One... so here's what I thought: Wouldn't it be possible to sync all those settings over Ubuntu One? So that your settings are the same on all the Ubuntu machines you use? I'm currently on 3 different machines, but imagine if after a fresh install of ubuntu you only had to sync with The Ubuntu One Settings Thingymajig and your box would be set up just the way you like it? In addition to up/downloading settings files, you could add a runonce script like runonce.sh. The first thing I do after a fresh install is this:

```
sudo apt-get remove empathy && sudo apt-get install thunderbird pidgin ubuntu-restricted-extras filezilla gparted exaile ufraw scite vlc audacious
```To wrap up my ramblings, here's what I'd love: A script (possibly w. a gui) that either up or downloads a predefined list of files and folders to Ubuntu one and runs the runonce.sh script.

Result: My usual tools are installed and my settings are applied. Automagically.

We love this idea! We're a ways off from being able to provide this functionality but it's something we're excited about potentially doing in the future. 

Thank you,

Joshua

---

### Post by kaffemonster on 2010-03-02
Yay! I had a good idea!

/runs to note it on the calendar.

Come to think of it, if there is a descrtiption of the Ubuntu One API somewhere, I guess I could take a swing at it myself, at least a simple script at first.

---

