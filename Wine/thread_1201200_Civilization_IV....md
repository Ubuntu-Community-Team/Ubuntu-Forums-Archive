---
title: "Civilization IV..."
date: 2009-06-30
forum: Wine
---

### Post by TheStabe on 2009-06-30
Hi. When I crashed my computer a few months ago (nice one by me), I lost my Windows XP Pro for good. This led to Windows 7, which I now dual boot with Ubuntu :cool:. I just tried reinstalling my Civ4 on 7, but the compatibility issues made it run like crap (and no, my computer is perfectly capable of running it nicely; ATI 4670, P4 HT 3.2Ghz, 2Gb RAM). I've yet to install WINE, can anyone tell me if Civ4 works smoothly under WINE in Jaunty 9.04?

---

### Post by X_Splinter on 2009-07-01
Thats is not the rigth place to ask.

However check the Wine App Database

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3632]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3632")

---

### Post by simon013 on 2009-11-11
Hi, I am a new Ubuntu user. I have 9.10, and wine 1.1.32. I installed civilization 4 pretty much flawlessly, and the game runs fine---until I actually load a game.

The map is kind of white/grayish and I cannot see anything clearly. I already adjusted the graphics of civ to "low" like the article here says:
 [http://tombuntu.com/index.php/2009/03/10/civilization-iv-on-linux-with-wine-1116/](http://tombuntu.com/index.php/2009/03/10/civilization-iv-on-linux-with-wine-1116/)

I followed all the steps, added the dll's, put a native override for msmxl3, but the game's graphics still are terrible. 

What do I do? I've heard Civ 4 worked well with Jaunty and older versions of ubuntu. 

Note: My computer used to be A Windows machine, its dell. I changed it a few weeks ago. I do not have a great graphics device, but it worked fine on Windows.

Any help would be GREATLY appreciated.

---

### Post by lavinog on 2009-11-11
It might seem like overkill but if you have a valid XP disk you can use xp in a virtual machine for some games.

you can try to enable logging to find what errors are occuring:
[http://www.2kgames.com/civ4/support_logging.htm](http://www.2kgames.com/civ4/support_logging.htm)

I think it is terrible that such a great game only supports winxp.
I got it to work in vista, but it required making a copy of the disk first because the installer isn't compatible with vista...go figure.

---

### Post by simon013 on 2009-11-11
yeah, but for that i would need to download a no-cd executable civ 4 file. i'm not totally sure how that works. you download the file and then do you replace it with the old executable file?

---

### Post by lavinog on 2009-11-11
> **simon013 said:**
> yeah, but for that i would need to download a no-cd executable civ 4 file. i'm not totally sure how that works. you download the file and then do you replace it with the old executable file?

I don't think you need the no-cd for a vm...you make an image of the cd and mount it to the vm.

---

### Post by simon013 on 2009-11-11
thanks. but I am just wondering--is there any record online of users of the latest ubuntu and wine using civ 4?

---

### Post by lavinog on 2009-11-12
> **simon013 said:**
> thanks. but I am just wondering--is there any record online of users of the latest ubuntu and wine using civ 4?

not with karmic yet, but there should be soon.
[http://appdb.winehq.org/appview.php?iAppId=2514](http://appdb.winehq.org/appview.php?iAppId=2514)

---

### Post by simon013 on 2009-11-12
Another question:
Is an Intell controller good enough to be used with games like civilization in wine?

---

### Post by lavinog on 2009-11-13
> **simon013 said:**
> Another question:
Is an Intell controller good enough to be used with games like civilization in wine?

is it good enough for windows?...then it should be.
It really depends on a number of factors...how does the card perform in linux.

I don't have alot of experience with intel cards, but with ATI and nVidia, I know you wont get the same fps as you would with windows.
for example ut2004 may run at 80 fps on windows, but 30fps in ubuntu. (although I haven't checked how the new drivers perform yet.)

the best way to answer your question is to try.

---

### Post by ceedub7 on 2009-11-13
> **lavinog said:**
> not with karmic yet, but there should be soon.
[http://appdb.winehq.org/appview.php?iAppId=2514](http://appdb.winehq.org/appview.php?iAppId=2514)

I was just playing Civ 4 + Warlords + Beyond the Sword on Karmic. I have all the graphics turned up and everything works fine.

When I installed, i used the instructions here: [http://www.rikertothebridge.com/2009/05/installing-civilization-iv-warlords-and-beyond-the-sword-on-ubuntu-linux/](http://www.rikertothebridge.com/2009/05/installing-civilization-iv-warlords-and-beyond-the-sword-on-ubuntu-linux/)

I did have to make a couple of adjustments:

  Where he recommends "sh winetricks vcrun2003", I actually had to go with vcrun2005.

  Also, it makes it easier to do multi-disc installs (like the gold edition) if instead using these 2 lines:

```
cd /media/cdrom
wine setup.exe
```

use this one line while working in another directory (like ~):

```
wine /media/cdrom/setup.exe
```

Otherwise it won't let you unmount the first disc during installation.

---

### Post by JBAlaska on 2009-11-13
Also there is a native Linux civ clone although I have not had time to check it out as I barely have time to play my favorite clone, Warzone 2100

---

### Post by simon013 on 2009-11-13
> **ceedub7 said:**
> I was just playing Civ 4 + Warlords + Beyond the Sword on Karmic. I have all the graphics turned up and everything works fine.

When I installed, i used the instructions here: [http://www.rikertothebridge.com/2009/05/installing-civilization-iv-warlords-and-beyond-the-sword-on-ubuntu-linux/](http://www.rikertothebridge.com/2009/05/installing-civilization-iv-warlords-and-beyond-the-sword-on-ubuntu-linux/)

I did have to make a couple of adjustments:

  Where he recommends "sh winetricks vcrun2003", I actually had to go with vcrun2005.

  Also, it makes it easier to do multi-disc installs (like the gold edition) if instead using these 2 lines:

```
cd /media/cdrom
wine setup.exe
```use this one line while working in another directory (like ~):

```
wine /media/cdrom/setup.exe
```Otherwise it won't let you unmount the first disc during installation.


I had no problem installing the game. I dud have trouble unloading disk 3, but that wasn't an issue because i just unloaded it by pressing eject in "my computer" in ubuntu rather than pressing the cd's button.

What is a problem is the graphics. I have an intel graphics controller. It ran the game perfectly fine on windows, but on karmic with wine, the graphics are so bad that i cannot play the game at all.

You are the first user that I have encountered who has Civ 4 working on karmic. What do you think I should do?

---

### Post by Tim_Olaguna on 2009-12-20
I've done everything described above and still no luck.  I'm actually running wine 1.2.35.  My problem is not getting the install program to eject the first disc.  It does that just fine.  My problem is the install program won't recognize the second disc, the cab file on the disc, or anything.  It just keeps telling me it can't find the file and to please insert the correct disc.

---

### Post by Tim_Olaguna on 2009-12-21
I spent about 6 hours on my effort last reported (should be immediately above this note) trying to get Civ IV and By The Sword (BTS) loaded.  Today I spent another 5 hours on this so-far fruitless effort.

This time I created two folders in my wine drive_c; one which contained all of the contents of my two Civ IV disks and one which contained all of the contents of the two BTS disks.  I then "installed" each one in order using the command "wine setup.exe".  Each went thru all of the expected installation steps and reported they were successfully installed, tho at the same time generating a host of errors in the background in the terminal window.  I then applied the patches as directed (including a newer BTS patch 3.19 which allows one to run the game WITHOUT having any disks in the cd-rom drive).  But, as reported by others, the game won't run at all.  Video and other error messages abounding in great volume.

It's obvious installing and playing this game in Windows is far more easier than doing so in Linux.  I'm going to go play in Windows for now.  Don't know when I'll be back to bang my head against this wall some more.

---

