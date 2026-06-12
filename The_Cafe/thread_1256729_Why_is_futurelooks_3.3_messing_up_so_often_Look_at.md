---
title: "Why is futurelooks 3.3 messing up so often? Look at these images. Thanks. ;)"
date: 2009-09-03
forum: The Cafe
---

### Post by gymophett on 2009-09-03
It is horrid, it was really nice. I love this theme, and I can't stand it doing this. It is being very buggy.
Look at these pictures...
Do I need to install anything? Murrine is installed.
It happens in the terminal, and quite a few other things.
It should look like these pictures:
[http://linux.softpedia.com/progScreenshots/FutureLooks-Screenshot-48398.html](http://linux.softpedia.com/progScreenshots/FutureLooks-Screenshot-48398.html)

But.. It looks like the thumbnails I attached.. Help?

---

### Post by steveneddy on 2009-09-03
You've got to install the Emerald themes and use Emerald as the WM.

Look here:

[http://ubuntuforums.org/showthread.php?t=796572](http://ubuntuforums.org/showthread.php?t=796572)

---

### Post by gymophett on 2009-09-03
> **steveneddy said:**
> You've got to install the Emerald themes and use Emerald as the WM.

Look here:

[http://ubuntuforums.org/showthread.php?t=796572](http://ubuntuforums.org/showthread.php?t=796572)

No you don't. They put it out for metacity now. Thats old.
The GTK part is messing up anyway. GTK is not Emerald.. Vise Versa.

---

### Post by steveneddy on 2009-09-03
To get that look you MUST install the emerald theme and run emerald.

Emerald folder is in the DL folder. (see pic)

Now you need these mods to the CCSM and you are ready to go:

 	Quote:
 	 	 		[SIZE=2] 			 				## make gnome bar true transparent

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent 			 		[/SIZE]    	 	 
 	Quote:
 	 	 		 			 				[SIZE=2]## removing gnome panel drop shadow
You can set the Shadow Windows (Windows Decoration)option in CCSM Window Decorations from "any" to "any & !(type=dock)" to remove the shadow from the panel

## Also make panel and menus transparent

Open CCSM

Go to General Settings

Go to Tab - Opacity Settings

Settings as follows:

dock 67
Menu 90
DropdownMenu 92
popupmenu 93

Link: [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)[/SIZE]        			 		 	 	 
Old stuff from the Beryl days but it still works in Compiz.

Good Luck and have fun.

Maybe you really wanna look cool and start messing with RGBA:

Look at this thread posting:

[http://ubuntuforums.org/showthread.php?p=7889745](http://ubuntuforums.org/showthread.php?p=7889745)

Look at the transparency in that second photo.

---

### Post by steveneddy on 2009-09-03
You might also be interested in these themes:

[http://www.bisigi-project.org/?lang=en](http://www.bisigi-project.org/?lang=en)

Just install the ppa and install away.

---

### Post by ad_267 on 2009-09-03
> **steveneddy said:**
> To get that look you MUST install the emerald theme and run emerald.

Just look at his screenshots. He's using the metacity theme and is happy with that, it's the GTK theme which isn't being applied. I haven't tried this theme myself, but from what I've read it should work with the default Murrine in Jaunty. Have you installed the Murrine engine from another source perhaps?

---

### Post by pwnst*r on 2009-09-03
> **steveneddy said:**
> You might also be interested in these themes:

[http://www.bisigi-project.org/?lang=en](http://www.bisigi-project.org/?lang=en)

Just install the ppa and install away.

damn, those are nice

---

### Post by gymophett on 2009-09-03
> **ad_267 said:**
> Just look at his screenshots. He's using the metacity theme and is happy with that, it's the GTK theme which isn't being applied. I haven't tried this theme myself, but from what I've read it should work with the default Murrine in Jaunty. Have you installed the Murrine engine from another source perhaps?

THANK YOU!
And I've tried both ways. From Synaptic, Defaulty, and from online.

---

### Post by steveneddy on 2009-09-03
Maybe murrine really isn't installed?

```
sudo apt-get install gtk2-engines-murrine
```

I installed it and here are the screenshots with and without emerald.

---

### Post by ad_267 on 2009-09-03
I tried it myself and it works, I'm using the the default murrine engine from the Ubuntu repositories. You could check your sources.list file and make sure there's no Murrine PPA there then do a "sudo aptitude reinstall gtk2-engines-murrine".

The author of the theme has a thread here so you could ask them: [http://ubuntuforums.org/showthread.php?t=1138897](http://ubuntuforums.org/showthread.php?t=1138897)

Alternatively, you could try the MurrinaBlu theme which is somewhat similar to the future looks theme: [http://www.cimitan.com/murrine/node/184](http://www.cimitan.com/murrine/node/184), although it's based on Murrine again so it might not work either.

---

### Post by steveneddy on 2009-09-03
Yeah - I'm running Intrepid and running murrine from the repos and working great.

---

### Post by gymophett on 2009-09-03
I have many Murrine themes. I don't know whats wrong with this one.

---

### Post by Dagonn on 2009-09-03
Just my cents: i got exactly the same problem.. running on jaunty and having the murrine from the repos installed, but well.. doesn't work.

too bad, looked like a nice light theme

---

### Post by hockeytux on 2009-09-03
> **steveneddy said:**
> You might also be interested in these themes:

[http://www.bisigi-project.org/?lang=en](http://www.bisigi-project.org/?lang=en)

Just install the ppa and install away.


Superb themes. Thanks for the link.

---

### Post by steveneddy on 2009-09-08
> **hockeytux said:**
> Superb themes. Thanks for the link.

You're welcome.

---

### Post by Exodist on 2009-09-08
> **steveneddy said:**
> You might also be interested in these themes:

[http://www.bisigi-project.org/?lang=en](http://www.bisigi-project.org/?lang=en)

Just install the ppa and install away.


I am not very impressed :confused:

---

### Post by Exodist on 2009-09-08
> **gymophett said:**
> It is horrid, it was really nice. I love this theme, and I can't stand it doing this. It is being very buggy.
Look at these pictures...
Do I need to install anything? Murrine is installed.
It happens in the terminal, and quite a few other things.
It should look like these pictures:
[http://linux.softpedia.com/progScreenshots/FutureLooks-Screenshot-48398.html](http://linux.softpedia.com/progScreenshots/FutureLooks-Screenshot-48398.html)

But.. It looks like the thumbnails I attached.. Help?

If the theme "ENGINE" is installed. It may be the theme itsself.

GTKRC files are really easy to screw up. if you forget a simple " or forget to keep something enclosed in { } it will completely FAIL. If the theme is not perfect code wise it will not load.
Just FYI..

---

