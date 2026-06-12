---
title: "WoW problem... with my sincere apologies"
date: 2010-04-05
forum: Wine
---

### Post by ginsong on 2010-04-05
Okay guys,
I know you receive this question every other day, but I'm going out of my mind here and this is my last resort.

I've been trying to install World of Warcraft Battle Chest on Ubuntu 9.10, and have been unsuccessful.  I've tried every single fix in every WoW problem thread I've run across, but keep hitting the same brick wall.

The installer is read-only.  I've tried 
sudo mount -t iso9660 /dev/x /media/yand that doesn't work worth a hoot... i'm not even sure what it does, other than that it somehow allows you to see something other than just the Installer.

I'm completely lost, and the documentation available doesn't seem to be of much help (the WoW section of WineHQ is labelled obsolete).

HALP!  :S

---

### Post by ginsong on 2010-04-05
deleted by me because of stupid

---

### Post by ginsong on 2010-04-05
But first post still applies.   I have no idea how to run the installer.  :(

---

### Post by ahuddleston on 2010-04-06
> **ginsong said:**
> But first post still applies.   I have no idea how to run the installer.  :(


i just installed wow and ubuntu. did you download and install wine? it's like a virtual windows client. actually pretty cool. i got the information on the best way to install with that.

If you did install it i apologize.. you didn't say which packages you have installed. if that's the case, just rightclick your installer and run with wine. :} hope that helps.. but everything i did came from these forums.. helped alot. hope you can find your help too

---

### Post by ginsong on 2010-04-06
Aye, yeah--I have Wine.  :)  I also downloaded PlayOnLinux and tried numerous guides to install the WoW BattleChest, to no avail.

The problem centers around an inability to modify Installer.exe, because it is read-only, and I haven't found any way (except one, mentioned below) to change that.  Not only this, but all the files on the disc are hidden *except* for Installer.exe.

I found something online (I am away from my home computer right now so I don't have the exact terminal commands in front of me) that allowed me to unhide the files on the WoW discs and allow me to transfer the install files to a folder on the desktop, but when I install it through PlayOnLinux, it won't change to the second DVD (or at least, I don't how to switch its focus, if that makes sense)

Without those commands to unhide and unlock the files, it says it can't find any files to install with.

When it is unlocked and the other install files are unhidden, and I try to install direct from the DVD, it says that it is unable to create a temporary folder.

When I try to install it from the desktop (after copying) it eventually asks for disc two, and I can't seem to get it to recognize my second folder that represents the second disc.

I'd like to try making an ISO from it, but since it is read-only, I dunno how to do this.  Re-installing Windows would be so much easier than this.  >:(

---

### Post by ahuddleston on 2010-04-06
i don't know what all you've done.. but the thing i did was just move the file from the download folder to a new file i made on the desktop. my installer properties says read and write and i can change it if i wish. make sure you're the admin.. should be prompting you with those keys you made when you installed ubuntu? 

don't try installing it straight from the download,, try moving it from that folder to the new one and then rightclicking the .exe file from there and open with wine windows program loader. you can't change it from the .exe because that's the way it's supposed to be. it's just ubuntu isn't recognizing it. wine is kind of a ghost drive :} does any of this help?

---

### Post by kyreks4 on 2010-04-07
I am having the same problems!!! I have Ubuntu 9.10... I have tried these guides... 

[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine) (i am not sure how to 
use the right file directory)

and i have also tried using PlayOnLinux....

I have tried from the CDs, both download clients from WoW.. and all the Youtube and forum guides I have found!!! What can I do? 

After I install, I have a variety of errors, such as... crashing when you run WoW, installer not working properly, when you load the game to play (after installed) the installer popping up, asking you to install, like you never did, and the "I agree" button not working after using this link to client: [http://www.worldofwarcraft.com/downloads/files/pc/wowclient-downloader.exe](http://www.worldofwarcraft.com/downloads/files/pc/wowclient-downloader.exe)

S.O.S.:confused:

---

### Post by ginsong on 2010-04-10
Back to Windows for me.  Nothing online has helped, so I guess I'll have to wait until Ubuntu or WINE figures out a way to get the Battlechest to work.  Thanks anyway, guys.  :\

---

### Post by lahook on 2010-04-11
I installed WOW by copying the folder from my windows install to a folder in Linux. I play WOW on Linux now because my Vista kept crashing.

---

### Post by itendo on 2010-04-13
go to your Blizzard account management screen and download the install client. the 'battlechest' as you refer to it is just a bundled version, right? basically the client download (or any wrath of the lich king dvd) will do the full install for you without the fuss of dealing with multiple versions.

remember, all of your information is basically on their servers. you simply have a library housed locally; ie. even if you only have BC youre still on patch 3.3.3 . anyway, run the installer client from Blizzard and it will download about 7.5 gigs and install them, then it will run updater and patch you to current (if you have problems during patching you might look into downloading the patches individually). but for installation ditch the battle chest cd as long as you still have your subscription.

---

### Post by kyreks4 on 2010-04-17
Window$ has screwed me over... again... even though im using Linux and OSS...

I have tried for several hours over a course of a few weeks which amounts to literal DAYS to get this to work...

I have two options... try to run it on ReactOS.... or Window$.... really kinda sucks, but it's what happens when MS sits on a couple million, nay billion to buy out the market whenever they want...

[http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)

:(

---

### Post by Demonlord1111 on 2010-04-17
Hey I've been able to install wow but I ran into another problem :(. As soon as i log in the contrast gets really bright. After i pick my toon an go into the game the ground is all black and i only see white figures running around instead of people. I was talking with a buddy and he said i need help making somthing called a source. if you have information please contact me via Skype or on this. my skype name is Demonlord1111

---

### Post by itendo on 2010-04-18
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

Assuming you installed through wine,  goto the wowwiki instructions on how to add the opengl line to your config.wtf file. You probably don't have it enabled and this should help. Keep up the work.

---

### Post by asdfoo on 2010-04-19
installing from cd appears to be a known issue, the other workaround is making an iso of the cd, mounting it and installing from there i think, there are some other good suggestions on this thread though

---

### Post by Kurtosis on 2010-04-20
ginsong, I had a similar experience with Ubuntu 9.10, couldn't install or play wow due to what appeared to be permissions issues I couldn't hack a solution to.

Then I reformatted my hard disk, installed Mythbuntu 9.10, Wine 1.2, and WoW (from the installer downloaded from Battle.net), and it just works.  Try Mythbuntu b/f going back to Windows.

---

### Post by itendo on 2010-04-21
a) although i dont know if mythbuntu is the best idea (since i havent used it), kurtosis is definitely on to something. youre better off in mythbuntu or another distro with a more limited desktop than ubuntu for the sake of graphics and freeing up system resources/conflicts. (if youre sticking with ubu at least make sure you disable the special effects.)

b) i am assuming you already have an account with wow, and that you previously installed the battlechest. that is why i recommended you **download the wow installer from the account management page and use it to install**. wine does pretty well with it. it will pop up some weird dialog bubbles, but you'll get through install easily enough as long as you have the up to date release of wine and your opengl is enabled. it WILL take longer since it will download the entire game during installation, and you will need to sit there and babysit it, but it will work.

c) once you get the install up and running, you are bound to need to tweak your config.wtf file (otherwise it may render the world upside down with a solarized filter as it did for me). open it (its in your /wow_directory/wtf/) up with your favorite text editor, go to the bottom, and add the following line to enable opengl:
```
SET gxapi "OpenGL"
```
that resolved many of my problems with the graphics and made it reasonably playable. some people have reported that it the config.wtf file will sometimes be edited after playing and the line will disappear, so be wary of that. 

d) however, i have a logitech lx8 mouse and am accustomed to the 9-button mouse play and couldnt rewire my brain to play at the wine-imposed(*) 7-button limit and had to re-install vista. also the sound wouldnt work and my fps was peaking at 40 fps but i couldve coped with those two probs.

(* not sure if this is really a wine issue, but ive heard it mentioned as such.)

---

