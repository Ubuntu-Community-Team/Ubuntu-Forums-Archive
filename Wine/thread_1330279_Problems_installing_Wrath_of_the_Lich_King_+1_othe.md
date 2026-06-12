---
title: "Problems installing Wrath of the Lich King +1 other WoW related problem"
date: 2009-11-18
forum: Wine
---

### Post by Kjardina on 2009-11-18
I am a Linux n00b, so bear with me please. I am running Ubuntu 9.10, Wine 1.1.31 and I have installed PlayonLinux. I followed the directions from the Ubuntu documentation post ([https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)) and successfully installed World of Warcraft and The Burning Crusade using the Blizzard downloader.

But when I try to install Wrath of the Lich King the same way, I get an error after agreeing to the EULA:

Sorry, the installation has failed.
 The disk doesn't have enough free space to install Wrath of the Lich King. (More than 10.1 GB is required, but only 0.0 MB is available.) Please free up space.

When I go through Wine to browse the C:\, it says I have 38.8 GB free. I've already activated my 10 day trial of WotLK so I really want to get it working. :(

The other problem I'm having is when I try to launch the game through Wine, I get this error:

Could not launch 'World of Warcraft'
Failed to change to directory '/home/kenzie/.wine/dosdevices/c:/Program Files/World of Warcraft/' (Permission denied)

This seems like it's probably something obvious, but I'm at a loss.

I've googled and searched the forums for both of these problems but I haven't found anything. I love my Ubuntu and really don't want to ever use Windows again, but I also love WoW.

Help?

---

### Post by akoskm on 2009-11-18
> **Kjardina said:**
> 
...
Sorry, the installation has failed.
 The disk doesn't have enough free space to install Wrath of the Lich King. (More than 10.1 GB is required, but only 0.0 MB is available.) Please free up space.
...

Open the File Browser from Places > Home Folder.
Take a look to the status bar, if the Free space is < 10.1 then free up some space on */home/<user>/*.
> **Kjardina said:**
> 
...
Could not launch 'World of Warcraft'
Failed to change to directory '/home/kenzie/.wine/dosdevices/c:/Program Files/World of Warcraft/' (Permission denied)
...

Are you sure that this is the correct patch to your Wow.exe?
My patch:
```

/home/<user>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe

```
*replace the <user> with your user name.

---

### Post by beastrace91 on 2009-11-18
Wanna try running the following command in terminal and see if it fixes the issue: ```
chown -R kenzie /home/kenzie/.wine/dosdevices/c:/Program\ Files/World\ of\ Warcraft
```

That *should* fix the permissions error it is giving you.

Regards,
~Jeff

---

### Post by Kjardina on 2009-11-18
> **beastrace91 said:**
> Wanna try running the following command in terminal and see if it fixes the issue: ```
chown -R kenzie /home/kenzie/.wine/dosdevices/c:/Program\ Files/World\ of\ Warcraft
```That *should* fix the permissions error it is giving you.

Regards,
~Jeff

I get the same permission denied error. Also, when I go directly to the World of Warcraft folder, it has a lock and an X on it. I went to properties, and changed the permissions, which allows me to see the files inside, but if I navigate away or try to launch WoW the lock returns.

---

### Post by Kjardina on 2009-11-18
> **akoskm said:**
> Open the File Browser from Places > Home Folder.
Take a look to the status bar, if the Free space is < 10.1 then free up some space on */home/<user>/*.

Are you sure that this is the correct patch to your Wow.exe?
My patch:
```

/home/<user>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe

```*replace the <user> with your user name.

Free space is 38.9 GB.

This is the path it's giving me in the error. I er, can't actually find the .wine folder to navigate through it that way and see if it's correct. *blush*

---

### Post by beastrace91 on 2009-11-18
If your seeing the little lock icon it is definitely an ownership issue and not a lack of space issue (I recall this issue popping up in a couple other WoW in the last week or so not sure what is causing it) Try this: ```
sudo chown -R kenzie /home/kenzie/.wine
```

Also to view the contents of your **~/.wine** directory you open your file viewer to your home folder and press **ctrl+h** to view hidden files and folders.

~Jeff

---

### Post by Kjardina on 2009-11-18
> **beastrace91 said:**
> If your seeing the little lock icon it is definitely an ownership issue and not a lack of space issue (I recall this issue popping up in a couple other WoW in the last week or so not sure what is causing it) Try this: ```
sudo chown -R kenzie /home/kenzie/.wine
```Also to view the contents of your **~/.wine** directory you open your file viewer to your home folder and press **ctrl+h** to view hidden files and folders.

~Jeff


Okay, so I have WoW folders in both the dosdevices and drive_c folders (?) but both of them have locks.

When I put that command into the terminal, it asks me for a password. I entered the only password I use and it returned me to the base line. But the folders still have locks and I get the same permissions error when I try to launch the game.

When I unlock the folders using permissions, I can launch the game's initial window, but when I click the Play button nothing happens.

---

### Post by Alatar1 on 2009-11-18
heres what you do, Unlock the folder permissions in the folder properties (all of the ones that are locked) , browse yourself to your world of warcraft directory, run the game via using Wow.exe , once at the log in screen, Unclick the "show launcher" box and that should fix up the permissions problem....for some odd reason the launcher will cause it to lock up every time...so just don't use it.

The very same thing kept happening to me, so I just disabled the launcher and it quit locking up

Also you do have to make sure its UNlocked to install WOTLK , just run it VIA WoW.exe to get into the login screen and disabled that launcher.
The "permission denied" Error is a well known and recent occuring error with WoW as of blizzards latest patch...DONT use the launcher, it WILL lock you out EVERYTIME
*edit*
There really should be a thread in here that says something along the lines of "World Of Warcraft Players check here first"
there seems to be someone with a WoW problem everyday here,and obviously people aren't reading the readme first threads for wine, I'm assuming because they dont pertain specifically to World Of Warcraft

---

### Post by Kjardina on 2009-11-18
Alatar1, I'm in!!! :D It's downloading  something now, so it might be getting WotLK.

It did cause one small other problem... I have a widescreen laptop, and after opening WoW, it's made my desktop go all wonky. WoW itself looks great, but my desktop is stretched and the fonts are huge like it's gone to a lower resolution. I've fixed it, but if it happens every time it'll be annoying. If anyone knows of a solution for that, it'd be great.

I hate sounding like such a user. LOL

---

### Post by Alatar1 on 2009-11-18
Same thing also happened to me lol, just make sure WoW and your desktop are set to the same resolution, should prevent that. :)

---

### Post by beastrace91 on 2009-11-18
If you have desktop effect enabled I'd also recommend trying to toggle them off while playing Wine games - it can cause issues like the one you describe above.

~Jeff

---

### Post by Alatar1 on 2009-11-18
Desktop effects and WoW havent given me too much of a bother, I've even ran COMPIZ and the desktop cube while using wow, it can drop framerates a bit, but all around the desktop effect and WOW have gotten along pretty well for me. BUT i do have them disabled for raids, due to the demanding nature of 25 man activities. but if your just messing around and doing regular old stuff the effects shouldnt be a big deal.

---

### Post by Kjardina on 2009-11-18
Okay, I tried changing the screen res in WoW and it locks up. I've got Compiz running with cube enabled, so I'll try disabling it.

---

### Post by Kjardina on 2009-11-18
Nope. Still locks everything up when I try to change the screen resolution.

---

### Post by Alatar1 on 2009-11-18
Do you have WoW set to run in OpenGL, And i'd also like to know what video card and driver your rockin...

---

### Post by Kjardina on 2009-11-18
> **Alatar1 said:**
> Do you have WoW set to run in OpenGL, And i'd also like to know what video card and driver your rockin...

I have an Nvidia card using the Nvidia accelerated graphics driver (v. 96). I don't know if I'm running in OpenGL? The screen res problem is secondary to not being able to get WotLK to install though. I can now get the installer to launch, but it hangs at 0% saying it's waiting for files to close. ?

---

### Post by GCoffee on 2009-11-18
Meaning to post this for a while, but anyway,

I had problems installing WOTLk on ubuntu, and eventually followed a guide to install it (something like files weren't showing on disk) anyway,

ever since updating to the latest patch I have to Chown my ~/.wine folder to root and launch nautilus as sudo.. I get the same permission denied error even if  I don't chown the ~/.wine folder.

Any help?

Cheers.

---

### Post by Alatar1 on 2009-11-18
Try running ```
winecfg
``` in terminal and setting it to a different windows version to install WOTLK i hear setting it to NT works.

   you can also configure wine by clicking applications > wine > configure wine

---

### Post by Alatar1 on 2009-11-18
Sure would be nice if people researched more...

Gcoffee ,
   Browse on over to home/yourusername/.wine/c_drive/program file/world of warcraft 

if theres an X on the folder right click, it go to properties, change the permissons(or you can do the sudo chown in terminal if you like, as long as you unlock the folders first,BUT you do NEED to browse to the world of warcaft directory under /c_drive/program files!!!), Now in that world of warcraft directory, launch WoW via using "WoW.exe" once in the login screen, un-click the box that says "show launcher" to not use the launcher when you run WoW , should fix that permission denied error right up, DO NOT USE THE WOW LAUNCHER IT WILL LOCK YOU OUT EVERYTIME

---

### Post by akoskm on 2009-11-18
> **Kjardina said:**
> ...
I don't know if I'm running in OpenGL?
...

Add the parameter
```

-opengl

```
after Wow.exe or, add the following line to the *.../World of Warcraft/WTF/Config.wtf*
```

SET gxAPI "OpenGL"

```.

---

### Post by Kjardina on 2009-11-18
> **Alatar1 said:**
> Try running ```
winecfg
``` in terminal and setting it to a different windows version to install WOTLK i hear setting it to NT works.

   you can also configure wine by clicking applications > wine > configure wine


Okay, I tried all the other versions. On NT, WoW says it can't install on anything earlier than XP. On the rest (XP, Vista, 2008) it hangs at waiting for files to close. Should I just let it sit and see if it ever starts up? I have no idea what files could need to close.

I'm sorry, I know I'm frustrating because I'm frustrated. But I really want this to work. :(

---

### Post by Alatar1 on 2009-11-18
Ok new strategy, I did some research and this is actually a problem thats come up on windows quit often as well...you need to make sure none of the following are running int he background.

/home/yourname/.wine/drive_c/program files/world of warcraft Launcher.exe

/home/yourname/.wine/drive_c/program files/world of warcraft Wow.exe

/home/yourname/.wine/drive_c/program files/world of warcraft Wowerror.exe

/home/yourname/.wine/drive_c/program files/world of warcraft Backgrouddownloader.exe

/home/yourname/.wine/drive_c/program files/world of warcraft Repair.exe 
OR ANY other WoW related processes, more than like running thru the same directory as the others....
and to check what processes are running I use a little prog called Htop
```
sudo apt-get install htop
```
then after it installs just type htop in terminal to run it and show what processes are running...

---

### Post by Kjardina on 2009-11-18
> **Alatar1 said:**
> Ok new strategy, I did some research and this is actually a problem thats come up on windows quit often as well...you need to make sure none of the following are running int he background. ...
then after it installs just type htop in terminal to run it and show what processes are running...

OMG IT'S INSTALLING! WOOT!

Thank you SO much. I found a thing about the screen res and changing the config.wtf file temporarily to d3d so I'll try that after it installs.

Thank you, thank you, thank you!

---

### Post by theonlyalterego on 2010-04-25
> **beastrace91 said:**
> Wanna try running the following command in terminal and see if it fixes the issue: ```
chown -R kenzie /home/kenzie/.wine/dosdevices/c:/Program\ Files/World\ of\ Warcraft
```

That *should* fix the permissions error it is giving you.

Regards,
~Jeff

I ran into this same error message.
> 
 The disk doesn't have enough free space to install Wrath of the Lich King. (More than 14.7 GB is required, but only 0.0 MB is available.) Please free up space.


The suggested solution worked for me, with one caveat. It was a permissions issue, I didn't own the wow directory under .wine, I couldn't get chown to assign the correct permissions, so instead of went through the file browser, used CTL+h to view hidden files, right clicked on the "World of Warcraft" subfolder, and granted myself, and my usergroup the ability to "create and delete files". This fixed my issue.

Thank you all for your suggestions! :)

---

