---
title: "Cache Desktop at Login Screen"
date: 2007-12-15
forum: Ubuntu Brainstorm
---

### Post by Afoot on 2007-12-15
Here's the idea: cache the *default* desktop into memory at the login screen so that when the user logs in, the loading time for the desktop is slim to none. Seamless login you might call it. With Hardy Heron seeking to solidify and make transition periods in Ubuntu smoother, I think this fits quite comfortably in the idea pool.

**Launchpad Blueprint:** [https://blueprints.launchpad.net/ubuntu/+spec/cache-desktop-at-login-screen](https://blueprints.launchpad.net/ubuntu/+spec/cache-desktop-at-login-screen)

---

### Post by aaaantoine on 2007-12-15
If this precaching were done AT the login screen, it would make the most sense, since that's where the OS first waits for user input (usually).  Any time before that would be wasteful.

---

### Post by Afoot on 2007-12-16
> **aaaantoine said:**
> If this precaching were done AT the login screen, it would make the most sense, since that's where the OS first waits for user input (usually).  Any time before that would be wasteful.
Yeah, that makes more sense actually. The OP is now edited.

---

### Post by Ub1476 on 2007-12-16
+1

I would love this.

---

### Post by Lster on 2007-12-16
+1 from me!

---

### Post by smartboyathome on 2007-12-16
+1, but have it automatically disabled if GDM is set to log in automatically.

---

### Post by FuturePilot on 2007-12-16
Sounds like a great idea. I like it :)

---

### Post by Ub1476 on 2007-12-16
Does anyone know how hard this would be to do?

---

### Post by WinterWeaver on 2007-12-16
I too think this is a good idea, and have thought of it before. But this brings a question: What if different users, using the same box, have different desktop settings and preference?

So, wont it be impractical to load the desktop at the login screen?

---

### Post by Afoot on 2007-12-16
> **WinterWeaver said:**
> I too think this is a good idea, and have thought of it before. But this brings a question: What if different users, using the same box, have different desktop settings and preference?

So, wont it be impractical to load the desktop at the login screen?
You should of course be able to disable it or change its settings. What those settings are is something we might come up with in this thread.

---

### Post by Vadi on 2007-12-16
+1

---

### Post by Delvien on 2007-12-16
+1

---

### Post by Martje_001 on 2007-12-16
+1. Very good idea!

I think it is not too hard to programm. We just have to load 'kdeinit' for kde and for gnome '?*gnomeinit*?'.

---

### Post by diatribe on 2007-12-16
so now instead of waiting for X to load you wait just as long at the login screen so it can cache the desktop?  I am unimpressed

---

### Post by Vadi on 2007-12-16
You might not be, but otherwise, the waiting time will just merge into the initial booting time.

Plus, if you start the computer, go away, come back, all you need to do is login, and tada.

---

### Post by smartboyathome on 2007-12-16
> **Ub1476 said:**
> Does anyone know how hard this would be to do?

Pretty easy, actually, since you can already do it with software included with Ubuntu.

---

### Post by Afoot on 2007-12-16
> **diatribe said:**
> so now instead of waiting for X to load you wait just as long at the login screen so it can cache the desktop?  I am unimpressed
I don't know about you, but I don't usually sit and wait by the computer until the login screen appears for the sake of wasting no time. Mostly I just turn on the computer, perhaps brew some tea, and come back a few minutes later. To then be able to log in with no waiting time would be awesome.

By the way, how do I edit the thread title to something more accurate?

---

### Post by Nonno Bassotto on 2007-12-16
+1 :)

---

### Post by Vadi on 2007-12-16
I don't think you can edit the page title, only mods can.

Hm. I think the next step to go about this would be to file a blueprint on Launchpad.net

---

### Post by smartboyathome on 2007-12-16
Btw, if anyone wants to do this now, see [this thread]("http://ubuntuforums.org/showthread.php?t=56565"). :KS

---

### Post by Vadi on 2007-12-16
Wrong thread...

---

### Post by Afoot on 2007-12-17
OK, I registered a blueprint for it:
[https://blueprints.launchpad.net/ubuntu/+spec/cache-desktop-at-login-screen](https://blueprints.launchpad.net/ubuntu/+spec/cache-desktop-at-login-screen)

Anyone can modify it, right?

---

### Post by thisllub on 2007-12-17
I can think of a whole lot of security reasons why this isn't a good idea.

---

### Post by Afoot on 2007-12-17
> **thisllub said:**
> I can think of a whole lot of security reasons why this isn't a good idea.
Such as?

---

### Post by 23meg on 2007-12-17
What do you want to change the title to?

[QUOTE=Afoot]OK, I registered a blueprint for it:
[https://blueprints.launchpad.net/ubu...t-login-screen](https://blueprints.launchpad.net/ubu...t-login-screen)[/QUOTE]

Note that you only *registered* the blueprint at the moment. You need to actually *write* it. More about the blueprint procedure here:

[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)

[QUOTE=Afoot]Anyone can modify it, right?[/QUOTE]

Once you start writing it in the wiki, yes.

---

### Post by Afoot on 2007-12-17
> **23meg said:**
> What do you want to change the title to?



Note that you only *registered* the blueprint at the moment. You need to actually *write* it. More about the blueprint procedure here:

[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)



Once you start writing it in the wiki, yes.
Cache Desktop at Login Screen would be a great title.

OK, I'll take a look at the instructions there, thanks.

---

### Post by roaldz on 2007-12-17
> **Afoot said:**
> Cache Desktop at Login Screen would be a great title.

OK, I'll take a look at the instructions there, thanks.

I think the term ¨preload¨ or ¨precache¨ is up for the job:)

What´s in a name.. Its a good idea, and as long as there are no security threads, you should go for it!

roald

---

### Post by rockin_goliath on 2007-12-17
As far as implementation goes:
     I assume that there are certain services and programs that have to be initiated with every desktop session, such as things like gnome-mount and nautilus and the some fundamental panel applets. Is there a way to catalog these services (for the selected default desktop session) and have those things be preloaded? 
    I've also read that there are specifications to overhaul GDM with some more eye candy ([https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser](https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser)). Could it be set up that whatever subsequent loading of the desktop be done behind a progress bar at GDM, instead of watching the panels and background and applets appear one by one? I say this because streamlining the transition from GRUB to the desktop is apparently a priority for this release, and this would be a great way of doing so. It could even transition from GDM to the desktop with some cool, compiz-like animation :cool:

---

### Post by 23meg on 2007-12-17
As part of a Google SoC project, Lorenzo Colitti had made [a comprehensive analysis]("http://www.gnome.org/~lcolitti/gnome-startup/analysis/") of the GNOME startup process, filed bugs where appropriate, and submitted patches. As far as I know, all of this work went into GNOME 2.14, which was a release where performance improvements were a big priority.

I'm not sure how much room there is for further optimization. In any case, if there are things that can be improved, this should be handled upstream, not just in Ubuntu.

---

### Post by 23meg on 2007-12-18
Looks like [jdong's GDM readahead hack]("http://ubuntuforums.org/showthread.php?t=565651") can bring some improvement. I don't know if it's release-quality though.

---

### Post by LeAstrale on 2007-12-18
Personally i like the idea of a quicker boot/login but then again...

My daily job is as a System administrator on a factory with windows XP and 2000 only! Many users have extreme amounts of data on their desktops. were talking 5GB+ here and in Windows XP everything on the desktop is (as far as possible) in the RAM. On daily basis i tell the users at my work to only have shortcuts instead of huge folders on their desktops, but id doesn't help.

Thats why i would like to make this a choice of each single user. because if youre going to have these amounts of data on your desktop, then you DONT wanna load it into RAM when GDM starts..

---

### Post by smartboyathome on 2007-12-18
> **23meg said:**
> Looks like [jdong's GDM readahead hack]("http://ubuntuforums.org/showthread.php?t=565651") can bring some improvement. I don't know if it's release-quality though.

If that was used, it might also up the amount of RAM needed to use Ubuntu since you would need quite a bit to cache a lot of the desktop. I have sucessfully used it on my 512MB machine though. :)

---

### Post by Vadi on 2007-12-18
Well the feature would be simply disabled for machines with lower ram.

---

### Post by Asham on 2008-01-08
I would love this.

---

### Post by Afoot on 2008-01-10
> **astral-1 said:**
> Personally i like the idea of a quicker boot/login but then again...

My daily job is as a System administrator on a factory with windows XP and 2000 only! Many users have extreme amounts of data on their desktops. were talking 5GB+ here and in Windows XP everything on the desktop is (as far as possible) in the RAM. On daily basis i tell the users at my work to only have shortcuts instead of huge folders on their desktops, but id doesn't help.

Thats why i would like to make this a choice of each single user. because if youre going to have these amounts of data on your desktop, then you DONT wanna load it into RAM when GDM starts..
It wouldn't load stuff that was "physically" on the desktop, but rather the interface: the menus and so on. :)

---

