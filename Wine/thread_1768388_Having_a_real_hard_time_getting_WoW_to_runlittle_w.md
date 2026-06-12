---
title: "Having a real hard time getting WoW to run/little wine problem."
date: 2011-05-26
forum: Wine
---

### Post by Super10.10 on 2011-05-26
Hello there folks, I am veryyyyy new to Ubuntu and linux in general,  I've been a Windows guy for a long time. 

  I am running Ubuntu 10.10 legit and I just  recently finished  installing WoW also legit off the blizzard/battle.net  site. I finished  patching it is all up to date. When I went to install  it, it said it  was going to my c:/program files like it always does and  should by  default, I did not change it..now I need to get to the wow  directory  and it is no where to be found. I looked in my wine c: drive  program  files, all thats in there is a three folders, common files which  is  empty, users, and IE. All three are useless in my situation. I  checked  my home folder/username/ but nothing is in there..downloads  folder is  empty, nothing in the documents or anything either. I then  checked my  computer -- system file and didn't find anything..
I really   would just like to play some wow so if you can help me through this   ridiculous nightmare, please do. thank you for your time.

Also  if it means anything to  anyone I have a folder in my Applications  section that says 'Windows  Games' and has WoW in it and only wow..course  clicking it doesn't do  anything lol..Sorry for the wall of text but I have been at this since  saturday..I've pulled two all nighters trying to get this down already,  heh. Thanks guys. :sad:

Also I posted this in the wrong section the first time but you should check out to see what things have been tried so far -- [http://ubuntuforums.org/showthread.php?p=10862873#post10862873](http://ubuntuforums.org/showthread.php?p=10862873#post10862873)

---

### Post by Super10.10 on 2011-05-27
Anyone?..In a nutshell I can't find my WoW directory so I can't do the Opengl thing I need to do to be able to play it..

---

### Post by cwwilson721 on 2011-05-27
IF it really installed, it IS IN THE '.wine' FOLDER.

I would, if I was in your shoes, do the following (if I couldn't find it):
[LIST]
[*]Delete the '.wine' folder (Since you can't find anything anyway, it's no big loss)
[*]Run 'winecfg' (This creates the '.wine' folder and dependencies, including Gecko. Yes, install Gecko if it asks). Make sure that you have an audio driver selected (Alsa), and the default version for running apps is XP (Or you may end up with sound issues)
[*]Install WoW (I prefer from the latest DVD, but it is up to you. Search forum on how to install)
[*]Make sure proprietary drivers are installed.
[*]Run WoW
[/LIST]
Or do as you wish.

If done like the above, IT WILL WORK. And it will install to ~/.wine/drive_c/Program Files/World of Warcraft. And it will create it's own World of Warcraft entry in the Applications > Wine > Programs menu

---

### Post by Super10.10 on 2011-05-27
Alright so uninstall wow/delete .wine folder and re-do both pretty much? I don't have any of my dvd's/cd's, is it okay to install it from the official site?

---

### Post by cwwilson721 on 2011-05-27
You are NOT 'uninstalling' anything. You're deleting the folder. wine is still available.


Try doing the steps I outlined above. The only mention of a disk is to install WoW, not wine.

---

### Post by Super10.10 on 2011-05-28
> **cwwilson721 said:**
> You are NOT 'uninstalling' anything. You're deleting the folder. wine is still available.


Try doing the steps I outlined above. The only mention of a disk is to install WoW, not wine.

Well technically WoW is installed..somewhere. Because I have the option to uninstall it, that's all I meant. And yeah I was just referring to the WoW cd's not wine, I do not have them which is why I dl'd it off the site. Got wine from the software thing provided by ubuntu. I will try this and report back, thank you.

---

