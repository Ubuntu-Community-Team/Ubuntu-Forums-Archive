---
title: "iTunes 9"
date: 2009-09-09
forum: Wine
---

### Post by Mutt77 on 2009-09-09
I did sucessfully (almost) installed iTunes 9 already. When I open iTunes it automatically goes to sleep so the program will not function after startup. Any suggestions? Jaunty 32 bit

---

### Post by Coder543 on 2009-09-09
I installed it, but when it runs it encounters a critical error and exits even after drawing the main window. So close, yet so far. Jaunty 32-bit, wine 1.1.29

---

### Post by murderslastcrow on 2009-09-10
Um- any possibility of changing the drawing method to GDI through editing some .xml or other settings file? It may just be that the usual drawing method is crashing the program.

It's worth a shot.

---

### Post by Oriana on 2009-09-10
Running GNOME 2.26.1 and WINE 1.1.29, on XP, and (without iTunes reinstall) on Vista. Searched for previous version of iTunes, but could not find download link. (I don't care about getting the latest version of iTunes as long as it talks to my 2nd gen iPod Nano without dropping data, rips mp3, and plays music if I want it to.)

My WINE/iTunes 9 says, upon running:

[quote=iTunes]
Apple Application Support was not found.

Apple Application Support is required to run iTunes. Please uninstall iTunes, then install iTunes again.

Error 2[/quote]

Interestingly, I came across this error several times when running iTunes on "school Macs"... Hm. 

How in the world do you uninstall programs in WINE?

---

### Post by Coder543 on 2009-09-12
"Applications -> Wine -> Uninstall Wine Software"

But, why don't you just use Songbird, Amarok, or Rhythmbox? Those work with everything except iPod Touches, as far as I know.

I do not think this has to do with iTunes' drawing routines or anything like that... it successfully draws itself before crashing, so... the problem should be somewhere else.

---

### Post by aysiu on 2009-09-12
My suggestion would be you find a native Linux alternative to iTunes **or** you do a dual-boote or virtualized Windows in order to run iTunes in Windows.

Thanks to Apple, iTunes does not function well in Wine.

---

### Post by cnschulz on 2009-09-13
because, unfortunately, they simply dont work as comprehensively as itunes.

songbird comes close but they seem to keep missing pretty key things, like son renaming... if it cant co-exist with itunes naming then its just not a viable option.



> **Coder543 said:**
> "Applications -> Wine -> Uninstall Wine Software"

But, why don't you just use Songbird, Amarok, or Rhythmbox? Those work with everything except iPod Touches, as far as I know.

I do not think this has to do with iTunes' drawing routines or anything like that... it successfully draws itself before crashing, so... the problem should be somewhere else.

---

### Post by aysiu on 2009-09-13
> **cnschulz said:**
> because, unfortunately, they simply dont work as comprehensively as itunes.

songbird comes close but they seem to keep missing pretty key things, like son renaming... if it cant co-exist with itunes naming then its just not a viable option. Well, if a native Linux app won't work, then dual-boot or virtualize Windows for iTunes.

**iTunes does not function fully in Wine**

---

### Post by rafttrip on 2009-11-07
I use floola for my iPod on Win and Linux. Works grate. 

Don't have to hold iTunes's hand any more to find files it keeps losing.

I would like to get iTunes working on Linux for my new Touch, but I wont hold my breath.;)

---

### Post by phillychease on 2009-12-13
> **aysiu said:**
> Well, if a native Linux app won't work, then dual-boot or virtualize Windows for iTunes.

**iTunes does not function fully in Wine**


what do you mean it doesnt function fully?
like what is missing? (i.e podcasts,buying music, etc)
all i use itunes for is to listen to music so is that alright?

---

### Post by aysiu on 2009-12-13
> **phillychease said:**
> what do you mean it doesnt function fully?
like what is missing? (i.e podcasts,buying music, etc)
all i use itunes for is to listen to music so is that alright?
More details here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

### Post by mkeyes001 on 2009-12-15
I installed itunes using wine and it runs terribly, I want to uninstall it but it hangs my session everytime I try.  Can I blow away my .wine to uninstall it?  Will that cause other problems?  (i've only got itunes install so far using wine so I won't loose anything I don't want to.)

---

### Post by xenosaga456 on 2009-12-15
i don't think that u should get rid of .wine to fix ur issues because as i have tried before for other problems when u delete .wine that i could not reinstall it....EVER i tried synaptic package manage and tried to fix broken packages and nothing worked for me .....the only way i ever fixed it was to reinstall ubuntu

---

### Post by hikaricore on 2009-12-15
> **mkeyes001 said:**
> I installed itunes using wine and it runs terribly, I want to uninstall it but it hangs my session everytime I try.  Can I blow away my .wine to uninstall it?  Will that cause other problems?  (i've only got itunes install so far using wine so I won't loose anything I don't want to.)

In the case that oyu've only installed itunes then yes you can just remove your .wine directory.

---

### Post by aysiu on 2009-12-15
If you're worried *removing* the .wine directory will screw things up, just rename it to .wine.old instead of completely deleting it. If there are no adverse effects, you can always delete the renamed file.

---

### Post by mkeyes001 on 2009-12-16
I was able to uninstall wine and removed the .wine directory with no issues, and also from command line it says no wine packages are installed.  But I have another issue now, when I look under applications I still see the WINE folder with itunes & quicktime still there.  I can't open them any longer but they are still there, why is this?

---

### Post by saltmore on 2009-12-17
you can delete the directory, and next time install something it makes another. No harm no foul.

---

### Post by heepie on 2010-01-15
I couple of days ago trying to install ie4linux i discoverd **playonlinux** application... Lets you install all kinds of windows applications: from ie, itunes, office 2007 and a tone of games

sudo apt-get playonlinux

or just go to the respiratories

---

### Post by aysiu on 2010-01-15
> **heepie said:**
> I couple of days ago trying to install ie4linux i discoverd **playonlinux** application... Lets you install all kinds of windows applications: from ie, itunes, office 2007 and a tone of games

sudo apt-get playonlinux

or just go to the respiratories
So iTunes is fully functional?

As far as I know, 1) [PlayOnLinux is really just a different skin for Wine](http://stuffem.wordpress.com/2009/09/04/playonlinux-another-human-face-for-wine/), and 2) [No version of iTunes gets more than a Silver rating for Wine](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

### Post by hikaricore on 2010-01-16
Posts like that are the exact reason I originally made the POL sticky.
The point of bumping this post with POL nonsense a month after it's been stale is what?

---

### Post by aysiu on 2010-01-16
> **hikaricore said:**
> Posts like that are the exact reason I originally made the POL sticky.
The point of bumping this post with POL nonsense a month after it's been stale is what?
Good point.

Your sticky:
[http://ubuntuforums.org/showthread.php?t=1226873](http://ubuntuforums.org/showthread.php?t=1226873)

Now, closed thread.

---

