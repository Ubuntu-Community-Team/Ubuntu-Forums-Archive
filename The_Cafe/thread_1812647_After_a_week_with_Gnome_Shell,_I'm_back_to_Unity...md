---
title: "After a week with Gnome Shell, I'm back to Unity..."
date: 2011-07-26
forum: The Cafe
---

### Post by ninjaaron on 2011-07-26
I'm not a Unity hater.  I love flashy desktop effects and playing with new interface paradigms.  In fact, I nearly creamed my jeans when I saw the new Windows 8 teaser vids.  The window and the menu have served us well, but they are not the ultimate in interface design.  Even if they were, I'd be the guy ready to try something else just for the novelty.

Anyway, this is more why I tried Gnome Shell than out of any dissatisfaction with Unity.  It looks so cool in the demos.  Installed Fedora on a partition, played with it for a few days, then added the ubuntu PPA and played with that for a few more

I like Gnome shell A LOT.  The work-flow management is brilliant.  They've created an environment where just about everything is available from a single key stroke.  The whole thing can be endlessly extended (à la Firefox) using Java.  The effects are beautiful, and I find that they all seem to contribute to usability.  Having the important status info in the main panel with all the less-important systray items in a hidden panel below is genius.  Best of all, there is no desktop folder.  Sure, you have a background, and you technically can navigate to a folder called "desktop" in the file browser, but you never have any of this cluttered up icon-related nonsense.  It's a nice clean screen greeting you at boot.  Course, you can still have your conky and your widgets and whatever you want.

So Why did I come back to Unity?  Well, having used Natty almost exclusively  since it's alpha 3, I find myself unable to look at a screen where the top part is filled with space-stealing bars that deliver no content.  The global menu/window controls are what brought me back; Just a quarter inch of the screen at the top devoted to interface (and most of that displays useful info), and the rest is filled with sweet, beautiful content.

So I guess I've reached the place where Unity feels like home, even if it is a home with a horrid window management system.

---

### Post by 23dornot23d on 2011-07-26
You can have the best of both worlds as Unity and Gnome-Shell will run in Ubuntu 11.04  .....

and by having a 

gnome-shell --replace

unity --replace

on the desktop window ..... for me allows me to switch between them ..... this is in Ubuntu 11.04 64 bit.

( may take a little setting up ...... but there is a [[COLOR=Red]_***thread for this***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1754198") ..... where users on here have it all running )

---

### Post by ninjaaron on 2011-07-26
> **23dornot23d said:**
> You can have the best of both worlds as Unity and Gnome-Shell will run in Ubuntu 11.04  .....

and by having a 

gnome-shell --replace

unity --replace

on the desktop window ..... for me allows me to switch between them ..... this is in Ubuntu 11.04 64 bit.

( may take a little setting up ...... but there is a [[COLOR=Red]_***thread for this***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1754198") ..... where users on here have it all running )

I don't get how this is possible. Installing Gnome 3 normally breaks Unity in 11.04. Are you using an older version of Gnome Shell or Oneiric repos for Unity or something?

Or are you magic?

---

### Post by 23dornot23d on 2011-07-26
> 
Oneiric repos for Unity
I use this ......

But it is also possible to drop Gnome Shell back to Gnome 2.32 ....... so it is compatible with Unity ......

either way works ..... 

as I said it takes a little work to do it ...........

No Magic involved ....... ( Unity + Gnome-Shell  on Gnome 2.32) or ( Unity + Gnome-Shell on Gnome 3.0.x )
but there is a [[COLOR=Red]_***thread for this***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1754198")

> 
**Overview:**

This is a basic, stock Ubuntu 11.04 installation & live iso with the  inclusion of the latest Gnome 3.0 packages constructed with UCK. It is  based on the UGR (Ubuntu Gnome Remix) project, with the addition of the  rictotz/testing ppa and comes with themes & extensions to be  installed by the user.  Despite what some people think, Gnome 3.0 shell  & Unity can coexist in the same installation.
The Distro on there has it already set-up too for Gnome 2.32 ..... so little work other than a spare partition of 20 Gig .....

[COLOR=Blue][U][I][B]You want Magic here I have KDE and Gnome Shell working together too >>> [SCREENSHOT]("http://img163.imageshack.us/img163/494/snapshot29ey.jpg")

[COLOR=Black]a[/COLOR][/B][/I][/U][COLOR=Black]lso can run Unity with KDE .... but not advisable .. check memory usage on Conky and the Kernel .... 

I would stick with either one or the other ..... Unity or Gnome-Shell ..... 
( mixing and matching with KDE is not clever ....... but is interesting )
[/COLOR][/COLOR]

---

### Post by 3Miro on 2011-07-26
There is a test version of Gnome-shell that runs under Gnome 2, but I am not sure how well it works.

In 11.10 with Gnome 3, you cannot switch between shell and unity with --replace, you need to logout/login since they use incompatible standards.

---

### Post by DeadSuperHero on 2011-07-26
> **ninjaaron said:**
> I don't get how this is possible.

Actually, the reason of all the breakage is not because of Gnome Shell itself per se, but because Natty mainly uses GTK2 apps and dependencies, whereas pretty much everything is being moved over to GTK3 for Oneiric. 

Basically, the toolkit is updated in the new version, and so it won't matter what shell you use!

---

### Post by ninjaaron on 2011-07-26
> **DeadSuperHero said:**
> Actually, the reason of all the breakage is not because of Gnome Shell itself per se, but because Natty mainly uses GTK2 apps and dependencies, whereas pretty much everything is being moved over to GTK3 for Oneiric. 

Basically, the toolkit is updated in the new version, and so it won't matter what shell you use!

I know.

---

### Post by 23dornot23d on 2011-07-26
> 
In 11.10 with Gnome 3, you cannot switch between shell and unity with  --replace, you need to logout/login since they use incompatible  standards.
** ....... but I am quite happy in 11.04 doing this ...... as its not showing any adverse effects at the moment ......**

**In fact its quite the opposite ..... this is the fastest - coolest and best it has ever run .........** :D

Screenshot now .... [Gnome-shell]("http://img18.imageshack.us/img18/1307/screenshotat20110727002.jpg")

Screenshot now ... [URL="http://img820.imageshack.us/img820/3426/screenshotat20110727003.jpg"]Compiz + kde4
[/URL]

---

### Post by akand074 on 2011-07-26
I agree with just about everything the OP said regarding gnome-shell. I returned to Unity because of one thing: Gnome 3's nautilus didn't have a working nautilus-share. In Unity now running over gnome 2, I can just right click a folder and choose to share it and I'm done. I've been trying for weeks to get file sharing working in gnome 3. In my alpha 2 install of Oneiric. Unity using gnome 3 also doesn't have that feature. I sincerely hope they manage to put it in before the final release. Otherwise I likely won't be able to upgrade until I figure out how to successfully create a share folder.

---

### Post by neu5eeCh on 2011-07-26
> **23dornot23d said:**
> 
Screenshot now .... [Gnome-shell]("http://img18.imageshack.us/img18/1307/screenshotat20110727002.jpg")

Screenshot now ... [URL="http://img820.imageshack.us/img820/3426/screenshotat20110727003.jpg"]Compiz + kde4
[/URL]

So... um... why is she wearing a cordless waffle-iron on her back?

---

### Post by el_koraco on 2011-07-26
Can't begin to describe how much I don't care about the five pixels I get in Natty.

---

### Post by Roasted on 2011-07-26
> **akand074 said:**
> I agree with just about everything the OP said regarding gnome-shell. I returned to Unity because of one thing: Gnome 3's nautilus didn't have a working nautilus-share. In Unity now running over gnome 2, I can just right click a folder and choose to share it and I'm done. I've been trying for weeks to get file sharing working in gnome 3. In my alpha 2 install of Oneiric. Unity using gnome 3 also doesn't have that feature. I sincerely hope they manage to put it in before the final release. Otherwise I likely won't be able to upgrade until I figure out how to successfully create a share folder.

I find the sharing thing built in to nautilus to be sort of a joke. Maybe I'm just a security freak where I like to have structure, permissions, allowable users, etc., but the system-config-samba package provides an extremely simple gui to manage your shares over samba. I use it for everything, and it's part of my massive apt-get install *insert 500 packages here* command that I run each time I do an Ubuntu install.

---

### Post by trollolo on 2011-07-27
there's a lot of good concepts at work in unity, but they were botched, it makes me feel like a full on mac user. as for windows 8, it's eye cancer to the core. it seems that every operating system, from windows to mac to linux, seem to think that tablets are actually the future of computing. 

ugh

---

### Post by LowSky on 2011-07-27
> **VTPoet said:**
> So... um... why is she wearing a cordless waffle-iron on her back?

Watch the movie Tron Legacy and you will understand.

---

### Post by benerivo on 2011-07-27
> **ninjaaron said:**
> ...So Why did I come back to Unity?  Well, having used Natty almost exclusively  since it's alpha 3, I find myself unable to look at a screen where the top part is filled with space-stealing bars that deliver no content.  The global menu/window controls are what brought me back; Just a quarter inch of the screen at the top devoted to interface...

There's a Gnome3 extension

[http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html](http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html)

...that autohides the panel to give you a bit extra space back.

In Gnome3 the default theme (adwaita) doesn't help by being a bit oversized.

The gnome-shell-extensions packages like the autohide are great. See here for a reasonably current list...
[http://aur.archlinux.org/packages.php?O=0&K=gnome-shell-ex&do_Search=Go](http://aur.archlinux.org/packages.php?O=0&K=gnome-shell-ex&do_Search=Go)

...and i'm sure one for a global menu will appear soon...

[https://live.gnome.org/Design/Whiteboards/Menus](https://live.gnome.org/Design/Whiteboards/Menus)

---

### Post by Syndicalist on 2011-07-27
Now that XFCE has drag and drop, I think I am switching to a debian based distro that uses XFCE and adding Docky or even using Docky as a panel. Ubuntu has caused its derivatives to be unstable, so instead of going back to the source to deal with Unity Im leaving the Ubuntu family and going back to Debian. 

I might try installing Gnome shell over XFCE just to try it out.

Liquid Lemur is pretty good. I prefer it to LMDE-XFCE. I think it might have been based on Crunchbang? They use some of their tools, but they offer easy installers for graphics cards and a lot of the stuff that in the past kept me from going back to debian....its all solved now.

---

### Post by akand074 on 2011-07-27
> **Roasted said:**
> I find the sharing thing built in to nautilus to be sort of a joke. Maybe I'm just a security freak where I like to have structure, permissions, allowable users, etc., but the system-config-samba package provides an extremely simple gui to manage your shares over samba. I use it for everything, and it's part of my massive apt-get install *insert 500 packages here* command that I run each time I do an Ubuntu install.

With nautilus share I was able to set permissions and it needed my password to access it. I used system-config-samba as well as every other possible software that did the same thing and none of them worked. No matter what it wouldn't find my share folders in Windows (or even realize I existed). I would be just as content had it worked that way. Nautilus share is the only samba sharing that has ever worked for me.

---

### Post by ninjaaron on 2011-07-27
> **el_koraco said:**
> Can't begin to describe how much I don't care about the five pixels I get in Natty.
Not that it makes a difference to you, but it's about 40-46px, 20+ for the titlebar and 20+ for the application menus, just for the sake of pedanterie.

And I care about those pixels.  I care about all the pixels.  I hate looking at interface.  Controls should all be invisible when I'm not using them.

> **benerivo said:**
> There's a Gnome3 extension

[http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html](http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html)

...that autohides the panel to give you a bit extra space back.
I tried it, but I go crazy if I can't see the clock.  I could, theoretically, just fullscreen all my programs, but I need the clock.  This even irritates me when I'm watching movies, for some reason.  I know it's crazy.

> The gnome-shell-extensions packages like the autohide are great. See here for a reasonably current list...
[http://aur.archlinux.org/packages.php?O=0&K=gnome-shell-ex&do_Search=Go](http://aur.archlinux.org/packages.php?O=0&K=gnome-shell-ex&do_Search=Go)

...and i'm sure one for a global menu will appear soon...

[https://live.gnome.org/Design/Whiteboards/Menus](https://live.gnome.org/Design/Whiteboards/Menus)I know, I know.  I installed like 20 extensions to see how they worked.  I only ended up keeping like 5 or 6 on, but at least I got to see them all.

Global menu will probably come to Gnome-shell, but proper work-flow management is probably  coming in the next Ubuntu... we'll see what happens...

---

### Post by JDShu on 2011-07-27
I actually hate the autohiding global menu in Unity with a passion, and same with the new scroll bars. The autohiding dock annoys me too.

That said, I do wish I could disable the hot spot in Shell, and have less annoying notifications. Overall I prefer Shell at this point, since design issues aside, Unity is buggy.

---

### Post by wolfen69 on 2011-07-27
> **23dornot23d said:**
> You can have the best of both worlds as Unity and Gnome-Shell will run in Ubuntu 11.04  .....


No thanks. I'll wait until gnome shell is *properly* supported in 11.10

For now, fedora 15 with gnome shell fits the bill perfectly.

---

### Post by Syndicalist on 2011-07-28
Sounds a little optimistic. Maybe 12.04? 12.10 for Unity?

---

### Post by cloyd on 2011-07-28
I do like Unity. I also miss some things from Gnome. I wish I could place links to documents and places to the launcher.  I wish I could move workplace switcher, applications, and files and folders up higher in the launcher. I miss some of my applets in the top panel. However, I've found adequate replacements for the ones I  used the most. I loved my cube, but did it really do anything useful?  I have two machines. One would not boot the live usb for natty, and it so still has 10.04 on it . . . and probably will until the end of the LTS. To get work done, I'd much rather work with Unity . . . regardless of some of the things I miss. Natty is good for basic users who use their machines for work.

---

