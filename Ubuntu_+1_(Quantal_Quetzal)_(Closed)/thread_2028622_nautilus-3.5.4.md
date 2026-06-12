---
title: "nautilus-3.5.4"
date: 2012-07-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-07-18
The new styled nautilus is now available, for the most part is ok here
There are a few break like nav. keybindings, & some things removed like 'open with' on folders. 
At least here the toolbar looks a bit fat & ambiance will need some help at some point, ect.

There will be some further slimming of the menu options, I gather Ubuntu will be taking this into consideration as to what's best for unity, ect.

Some current bugs or wishlists under consideration

typeahead - [https://bugzilla.gnome.org/show_bug.cgi?id=680118](https://bugzilla.gnome.org/show_bug.cgi?id=680118)
New Document option - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1014876](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1014876)
Open with on Folders - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254)
Navigation with keyboard - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026236](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026236)
Time setting - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026175](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026175)
Missing sidebar 'recent files place' - [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1026431](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1026431) - will be self fixing

---

### Post by philinux on 2012-07-18
Crashed here or refused to start. I put a couple of links in the changes and updates sticky. Seems in a state of flux at the moment.

---

### Post by hugmenot on 2012-07-18
It also searches immediately when you start typing

[https://bugzilla.gnome.org/show_bug.cgi?id=680118](https://bugzilla.gnome.org/show_bug.cgi?id=680118)

---

### Post by mc4man on 2012-07-18
> **hugmenot said:**
> It also searches immediately when you start typing

[https://bugzilla.gnome.org/show_bug.cgi?id=680118](https://bugzilla.gnome.org/show_bug.cgi?id=680118)
That's a change that possibly some Ubuntu users may not like though as stated the # of files in the pwd will vastly affect time. I did a git build the other day with tracker enabled & it seemed a bit better though didn't really spend much time at.
When it works quickly i sorta like it seperating out search returns in the window

It will be interesting to see what shakes down over the next couple > 8 months..

(myself am collecting some of these commits to help fashion a local nautilus that works better here.
As mentioned in prev. naut thread here is a good place to see, generally well described
[https://code.launchpad.net/~vcs-imports/nautilus/master-git](https://code.launchpad.net/~vcs-imports/nautilus/master-git)

---

### Post by mc4man on 2012-07-18
> **philinux said:**
> Crashed here or refused to start. I put a couple of links in the changes and updates sticky. Seems in a state of flux at the moment.

Try upgrading gtk* in proposed to 3.5.8-0ubuntu2 (or higher if it re-ups

That reverts some gtk code that was causing nautilus segfaults in varying degree's over the last couple of weeks

Here nautilus crashed constantly in a default setup. Has fixed totally, (here),  when nautilus handles the Desktop
(though reverting is not as good as fixing..

---

### Post by hugmenot on 2012-07-18
Improving search is appreciated, but in a list of files it’s essential to be able to jump around by typing the initial letters.

---

### Post by mc4man on 2012-07-18
> **hugmenot said:**
> Improving search is appreciated, but in a list of files it&#8217;s essential to be able to jump around by typing the initial letters.
I guess one of the  things with the search is it searches for character(s) anywhere in the file name vs 1st or 1st+2nd in the file name, ect.

So in a bin folder here ar will return arip & any other file that has an ar anywhere in file name

So obliviously searching just a single letter or even two  may be unproductive

---

### Post by hugmenot on 2012-07-18
But if you are in a folder with lots of files you might want to jump to a letter, say H. It&#8217;s like thumbing through a phone book. You go for initial letter first.

---

### Post by hugmenot on 2012-07-19
This too [https://bugzilla.gnome.org/show_bug.cgi?id=504869](https://bugzilla.gnome.org/show_bug.cgi?id=504869)

(they removed the little expander triangles in list view)

---

### Post by mc4man on 2012-07-19
> **hugmenot said:**
> This too [https://bugzilla.gnome.org/show_bug.cgi?id=504869](https://bugzilla.gnome.org/show_bug.cgi?id=504869)

(they removed the little expander triangles in list view)

That was a while ago, part of the ["Make nautilus a bit more GNOME 3 style"]("https://bugzilla.gnome.org/show_bug.cgi?id=676531") bug series
likely this, short rational given
[http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16049](http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16049)

It was suggested here about providing 3.4 as an alternate because it's only going to continue along the current path
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254/comments/2](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254/comments/2)

(though not sure if he meant 3.4.X or 3.5.4, I'd think many would be happy with 3.5.3 at the very  least

The file search is going to be frustrating for many, at least for a while, (probably quite a while

I would suspect there may be some ppa's popping up this fall with modified nautilus packages...,

---

### Post by dino99 on 2012-07-19
cant set the "modified" time colomn to 24H format.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026175](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026175)

---

### Post by effenberg0x0 on 2012-07-19
When the DE starts, I don't have a right-click menu on the desktop until I click on the "Home" launcher for a first time. At this point I can right-click anywhere on the desktop and get a menu again. 

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-07-19
Random crashes when starting a second, third, 4th, etc instance of "Home" (clicking the "Home" launcher with middle mouse button - wheel).

> 
[113154.563503] nautilus[12304]: segfault at 18 ip 00007f84fbfa4580 sp 00007fffaa1101c8 error 4 in libgtk-3.so.0.506.0[7f84fbcc7000+4d1000]



Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-07-19
When I have an open Nautilus window and click on the icons in the notification area, like volume for example, the Nautilus window contents redraw constantly.

Regards,
Effenberg

---

### Post by ventrical on 2012-07-19
> **effenberg0x0 said:**
> Random crashes when starting a second, third, 4th, etc instance of "Home" (clicking the "Home" launcher with middle mouse button - wheel).



Regards,
Effenberg

Yep .. I'm getting random crashes also. Popping in and out. Titles on menubar will come up, then go. 

Rough shape.

---

### Post by Yahoé on 2012-07-19
> **hugmenot said:**
> It also searches immediately when you start typing

[https://bugzilla.gnome.org/show_bug.cgi?id=680118](https://bugzilla.gnome.org/show_bug.cgi?id=680118)

Reading this bug report sums it all. For me the new search is a loss of functionality.  Certainly not instantaneous anymore as it use to be on a 106 095 items 1,4 Tb Music folder, but it's still a work in progress so hopefully they will make it lightning fast, hopefully...

---

### Post by mc4man on 2012-07-19
> **effenberg0x0 said:**
> Random crashes when starting a second, third, 4th, etc instance of "Home" (clicking the "Home" launcher with middle mouse button - wheel).
Regards,
Effenberg

Did you upgrade gtk* yet as mentioned in post 5 - was in proposed, may be in main now

---

### Post by Yahoé on 2012-07-19
When opening a folder in Nautilus Files 3.5.4 ,  ctrl-V copies the data to the search bar instead of the selected  folder.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026659](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026659)

---

### Post by effenberg0x0 on 2012-07-19
> **mc4man said:**
> Did you upgrade gtk* yet as mentioned in post 5 - was in proposed, may be in main now

My mc4man, 

Yep, I did. I think I'll give up on my current main setups (desktop and laptop) and will reinstall from scratch. That's the first time I have to do it since testing 10.04. Right now I have serious problems with NVidia, Flash, VLC, rdesktop, Nautilus, Compiz/Unity, Cups, Samba, NFS/idmapd, apt-get, my mouse buttons/gestures are messed up (Logitech Wireless Touchpad), so is the keyboard (MS ARC Wireless) mapping on remote sessions and there's probably more things I'm forgetting right now. On the laptop I'm also experiencing a higher power drain (from 7 to 4 hours). It's just too much weird things going on simultaneously and it looks like most users are not having such a borked experience, so its more likely I did something stupid in a recent update. 

Regards,
Effenberg

---

### Post by ventrical on 2012-07-19
I re-booted and ... awesome!

 The search tool now behaves like the search dialog box in synaptic package manager treating all my files as a complete library - so - if I enter in the letter 't' all files and folders with the letter 't' will display !! etc...

 Every once in a while it will not maximize from the Unity menu dash.

---

### Post by pressureman on 2012-07-19
I just noticed that in a directory that contains files and subdirectories, the subdirectories are no longer listed first.

Do the Nautilus devs realise how unintuitive this is? Subdirectories have been listed first in just about every file manager since the dawn of time.

Is this yet another MacOS wannabe?

---

### Post by effenberg0x0 on 2012-07-19
> **pressureman said:**
> I just noticed that in a directory that contains files and subdirectories, the subdirectories are no longer listed first.

Do the Nautilus devs realise how unintuitive this is? Subdirectories have been listed first in just about every file manager since the dawn of time.

Is this yet another MacOS wannabe?

That's is really counterintuitive :\

BTW, I had to work to fix a Macbook Pro (my wife's) last weekend. The thing wouldn't even boot. My previous experiences with MacOS were brief (presentations, ms-office, etc) so that was a first for me. I wasted a ton of hours understanding the file system, config files, permissions/users, services, hardware, etc. Let me tell you this: I'll never complain about Ubuntu again :P That thing is manufactured in hell by the devil himself.

Regards,
Effenberg

---

### Post by mc4man on 2012-07-19
> **pressureman said:**
> I just noticed that in a directory that contains files and subdirectories, the subdirectories are no longer listed first.

Do the Nautilus devs realise how unintuitive this is? Subdirectories have been listed first in just about every file manager since the dawn of time.

Is this yet another MacOS wannabe?
The default for that was changed, just change back or file an Ubuntu bug on 
For reference
[http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16121](http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16121)

Set in preferences > views

---

### Post by mc4man on 2012-07-19
> **effenberg0x0 said:**
> My mc4man, 

Yep, I did. I think I'll give up on my current main setups (desktop and laptop) and will reinstall from scratch.\ 

Regards,
Effenberg
Wouldn't hurt
The gtk revert to stop crashes should be effective - I had the bug in an extreme here, nautilus would crash every other use or every 30 sec's or so. (unless I disabled nautilus handling the Desktop, then it would only crash every once & a while or thru a certain repetitive action
The gtk revert patch has fixed here..

---

### Post by screemo on 2012-07-23
I would love a nautilus ppa with the 'type-a-head' removed.

Anyone ?

PS: Nice job to slash functions that are central to filebrowsing... *sarcasm*.

And where the heck is the configurable shortcuts for new tabs, and switching between them... Really hope this is development stuff.

---

### Post by screemo on 2012-07-23
> **Yahoé said:**
> When opening a folder in Nautilus Files 3.5.4 ,  ctrl-V copies the data to the search bar instead of the selected  folder.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026659](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026659)

I'm so frustrated with this.... This cant be a regression, they removed it because it wasn't needed anymore ... right? :-({|=

---

### Post by sgage on 2012-07-27
After taking a break in the action for a couple of weeks, I installed a fresh Alpha 3 this morning. I am horrified at what they've done to Nautilus. 

What's up with removing the "extra pane" feature?
Why can't I minimize the window?
Where are the preferences?
WTF?

Nautilus is unusable in its current form. Back to Filerunner :KS

---

### Post by philinux on 2012-07-27
Prefs are under the Gear on the right.

---

### Post by philinux on 2012-07-29
Nautilus vs Marlin comparison.

[http://www.iloveubuntu.net/latest-nautilus-and-marlin-side-side-comparison](http://www.iloveubuntu.net/latest-nautilus-and-marlin-side-side-comparison)

---

### Post by screemo on 2012-07-29
> **philinux said:**
> Nautilus vs Marlin comparison.

[http://www.iloveubuntu.net/latest-nautilus-and-marlin-side-side-comparison](http://www.iloveubuntu.net/latest-nautilus-and-marlin-side-side-comparison)

Switched to marlin - it works as intended. bye-bye nautilus for now.

---

### Post by ronacc on 2012-07-29
> **screemo said:**
> Switched to marlin - it works as intended. bye-bye nautilus for now.

link to the one you d/l'd please .  I installed the dev daily ppa and that one is a bit unstable for me .

---

### Post by philinux on 2012-07-30
[http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Is The New Nautilus A Step In The RIght Direction?

---

### Post by ronacc on 2012-07-30
> **philinux said:**
> [http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Is The New Nautilus A Step In The RIght Direction?

Is a hippotomi any prettier than I ? It depends on how you look at things !

---

### Post by effenberg0x0 on 2012-07-30
> **philinux said:**
> [http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29]("http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29")

Is The New Nautilus A Step In The RIght Direction?

I think there's no right direction. There has never been a right GUI or a better set of functionalities for all users.

We now have a lot of polemics when any Linux program changes GUI and/or functionality, etc.Just think Unity, Gnome, now Nautilus, so many others. IMO, these small changes were not relevant in the past because we had extensive configuration / customization built in everything - they were optional. I think the real problem is this trend of removing (or hiding) customization from users, in order to force a single / unified visual identity - which is much more interesting from a vendor/branding perspective than for end-users. People constantly bash new Linux software and GUI and compare it to tablets or smartphones (unfairly, in many cases). What we really got from these devices (and also from MacOS, and what we see in the new MS-Windows now) - the real thing that causes confusion, dissatisfaction and conflict - is taking customization / configurations away from users.

In this sense, IMO (again!) all software that are following this trend are taking a step in the wrong direction. Looking into the future, I don't see this trend as something that will survive anyway. Eventually people will see that being as monolithic as MS or Apple software is not good: The most valuable asset/feature of FOSS for end users, was (and still is in many cases) the freedom to customize the OS, specially the desktop experience. 

Regards,
Effenberg

---

### Post by mc4man on 2012-07-30
Whether i like or dislike, other than being irrelevant, may depend on what Ubuntu does, swallow hook,line, & sinker or modify. (latter is more likely, though how so will be interesting.

So there is a newly exposed 'feature' in the sidebar 'places' - that would be a recent folder. There doesn't appear to be any way yet, (or ever??),  to adjust what it shows, though items can be 'deleted' from recent  ( not actually deleted

---

### Post by mc4man on 2012-07-30
> **philinux said:**
> Nautilus vs Marlin comparison.

[http://www.iloveubuntu.net/latest-nautilus-and-marlin-side-side-comparison](http://www.iloveubuntu.net/latest-nautilus-and-marlin-side-side-comparison)
What I found more interesting there was the drawers app, may keep one in the launcher for files/folders of current interest, precise version works in 12.10
[http://www.iloveubuntu.net/drawers-12079-released-drop-items-unity-dash-persistent-mode-new-configuration-options-and-bug-fixes](http://www.iloveubuntu.net/drawers-12079-released-drop-items-unity-dash-persistent-mode-new-configuration-options-and-bug-fixes)

---

### Post by EgoGratis on 2012-07-30
I recommend Drawers too and too bad developer didn't make it on time and can not compete in The Ubuntu App Showdown contest. 

About Nautilus the problem is there are some new features in "redesigned Nautilus" that do make sense and are welcomed but on the other hand there are some things like removing dual pane mode that are just to hard on users and because of that it's hard to enjoy new features if you strongly disagree with removal of those things u use a lot and expect in modern file manager and where there in the past!

**Bookmark menu items removed** i can't test this right now but does this remove bookmark functionality in Nautilus i sure hope not?

**Application Menu removed** this probably will present some issues with Unity and Application Menu?

---

### Post by mc4man on 2012-07-30
> **EgoGratis said:**
> !

**Bookmark menu items removed** i can't test this right now but does this remove bookmark functionality in Nautilus i sure hope not?

**Application Menu removed** this probably will present some issues with Unity and Application Menu?

Bookmarks menus (add & edit) remain in the gear menu, bindings of ctrl+d, ctrl+b

Some other bindings are broken but should be fixed like alt+arrows for back,forward & up

The old app menu is gone, I'd expect something from ubuntu there, currently it shows some redundant menu items that were placed in GS's nautilus app menu

The New Document template still exists but users have to place a template in ~/Templates to expose it, preferably a template for anything but /text/plain

Open with on folders is gone, i've a bug on that as it would be non-intrusive to return & is quite useful for multimedia & opening a dir. from nautilus with another file manager like a dual pane one or one better for root browsing

---

### Post by EgoGratis on 2012-07-30
> Bookmarks menus (add & edit) remain in the gear menu, bindings of ctrl+d, ctrl+b

Great!

> The old app menu is gone, I'd expect something from ubuntu there,  currently it shows some redundant menu items that were placed in GS's  nautilus app menu


Yes this kind of things will probably become big problem in future when Unity/GnomeShell differ more.

---

### Post by dp_wiz on 2012-08-03
> **hugmenot said:**
> It also searches immediately when you start typing

[https://bugzilla.gnome.org/show_bug.cgi?id=680118](https://bugzilla.gnome.org/show_bug.cgi?id=680118)

OMG it's so annoying and totally should be on a hotkey (where it is already, ctr+f) and not to eschew some unrelated essential feature.

Even on my SSD drive navigation is slowed to a crawl, not to speak of intercontinental SFTP connection where it's just. do. not. work. at all.

---

### Post by philinux on 2012-08-05
Looks like some others do not like the new nautilus.

Mint have forked 3.4.x into Nemo.

[http://www.webupd8.org/2012/08/nemo-linux-mint-team-forks-nautilus.html](http://www.webupd8.org/2012/08/nemo-linux-mint-team-forks-nautilus.html)

---

### Post by effenberg0x0 on 2012-08-05
I have always used tuxcmd in parallel to Nautilus, because I used midnight-commander for too long in MS platform and it feels natural to me. I stuck to it when Nautilus began to change. 
BTW, there's also gnome-commander and mc in the repos.

A couple weeks ago I installed Merlin and, so far, it hasn't crashed once, all features work as expected, it's very comfortable for people used to Nautilus IMO. 

Although I am usually not too excited about testing with non-standard PPAs and packages (or telling people to do it), I gotta say I really recommend Marlin to everyone, given the circumstances. I have researched a little and really appreciated the development platform and goals of the developers. I feel like it's something we should support in Ubuntu.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-05
> **effenberg0x0 said:**
> 

A couple weeks ago I installed Merlin and, so far, it hasn't crashed once, all features work as expected, it's very comfortable for people used to Nautilus IMO. 

Although I am usually not too excited about testing with non-standard PPAs and packages (or telling people to do it), I gotta say I really recommend Marlin to everyone, given the circumstances. I have researched a little and really appreciated the development platform and goals of the developers. I feel like it's something we should support in Ubuntu.

Regards,
Effenberg

I've seen it crash several times, have you checked in /var/crash?
At least here it, (marlin), has some wired things with the back,forward buttons not being visible/highlighting correctly.

Another small break at times is, unless i'm missing something, that bookmarks are set by DnD to personal. For that I've seen it not let go of a grabbed folder, nor return it to orig. So you need to drop somewhere & then retrieve
(created an interesting when I decided to see if it would allow adding Desktop to personal, (wouldn't), then wouldn't release back into home...

There are others related to using proper, then improper icons for the default xdg dir folders, ect.
Anyway 12.10 is going to use nautilus, maybe they'll alter a few things, maybe, (remote) they'll offer a 3.4.X alt. if enough usability bugs are filed


(spacefm is in interesting advanced FM

---

### Post by effenberg0x0 on 2012-08-05
> **mc4man said:**
> I've seen it crash several times, have you checked in /var/crash?
At least here it, (marlin), has some wired things with the back,forward buttons not being visible/highlighting correctly.

Another small break at times is, unless i'm missing something, that bookmarks are set by DnD to personal. For that I've seen it not let go of a grabbed folder, nor return it to orig. So you need to drop somewhere & then retrieve
(created an interesting when I decided to see if it would allow adding Desktop to personal, (wouldn't), then wouldn't release back into home...

There are others related to using proper, then improper icons for the default xdg dir folders, ect.
Anyway 12.10 is going to use nautilus, maybe they'll alter a few things, maybe, (remote) they'll offer a 3.4.X alt. if enough usability bugs are filed


(spacefm is in interesting advanced FM


Hi mc4man, 

I think my usage is probably not as heavy as your: I have no marlin *.crash in /var/crash. I grepped logs and old logs too and found nothing. Maybe it is because my usage is very simple and light: I just browse LAN shares and local mounts, move and delete stuff from $HOME only. For all the heavier stuff and things outside $HOME I use a lot of console and tux-commander. I have also missed anything  weird with the Forward / Back / Up buttons so far - I think I don't have a good eye for design stuff like active/inactive highlights, etc. And about the bookmarks, I'm pretty sure they are always there, because they have my remote mounts, etc, which I use all the time - this one I'm confident it's working as expected. I'll pay attention to the points you mentioned.

Regards,
Effenberg

---

### Post by ronacc on 2012-08-05
what PPA are you using for marlin ? I have tried both the quantal-builds and the marlin-daily and both crash as soon as I start marlin (marlin not the system) . I'm AMD64 here .

---

### Post by effenberg0x0 on 2012-08-05
Hey, here it goes:
```

[14:23:36] [email]ahsl@AL-DESK01:[/etc/apt/sources.list[/email].d]: listppa --show *marlin*
01 PPA matches your query (*marlin*)

PPA 01 File: 
/etc/apt/sources.list.d/marlin-devs-marlin-daily-quantal.list
PPA 01 Contents:
<START>
deb [http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu) quantal main
deb-src [http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu) quantal main
<END>

```
I think I got this ppa from omgubuntu or webupd8 a while ago. Let me search my browser history and I'll post the link here in a while.

Regards,
Effenberg

**EDIT:** It looks like I read [this link]("http://www.omgubuntu.co.uk/2011/11/how-to-install-marlin-file-browser-in-ubuntu-11-10") and got the ppa there. I may have manually edited the ppa file to replace precise for quantal and apt-updated. Sometimes I do that (or the opposite) depending on the package.

---

### Post by mc4man on 2012-08-05
I'm using this one which seems the same as mentioned above though no need to edit, has quantal 
[http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu)

The things I mentioned are intermittent, working fine atm. At least here have returned the 'open with' on dir.'s so generally have tested other Fm's from a r. click in nautilus which may or may not be a factor

(as a side note I've spent a few hr.'s with "plank" which I actually like alot - supports Desktop Actions & has window lists thru r.click, ect. May end up using GS with plank though it works fine in ubuntu session with the unity launcher hidden.

2 small new nautilus bug reports - 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1032835](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1032835)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1032833](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1032833)

---

### Post by effenberg0x0 on 2012-08-05
The things that are bothering me more in Nautilus right now are:

- I click it (Home) in the Launcher and nothing happens. It's intermittent. Sometimes it will open  a window normally, sometimes it won't do or say anything (no crash dialog, nothing), other times it will open the window and close in a second with no crash message, and sometimes all I get is the crash dialog).  

- Then, minutes after, I'm doing something else and out of the blue it opens 10's of Nautilus windows covering my desktop (all the clicks I did on it on the Launcher that resulted in no action minutes ago get processed at once).

- Clicking on my quicklist items on the Home icon on the Launcher almost never works. It works very consistently with Marlin.

I'm gonna browse through Nautilus reports later today to see if I can add something. Haven't had the time yet.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-05
> - Clicking on my quicklist items on the Home icon on the Launcher almost never works. It works very consistently with Marlin.
Curious - does marlin show your quicklist entries from launcher when marlin is not yet opened?
Here marlin has 3 'built-in' quicklists, then after opening will add all bookmarks (personal) items
Edit - after a reboot then the Marlin launcher shows default 3 + personal

As far as the default 3, marlin should switch from "X-Ayatana-Desktop-Shortcuts=" to Actions= (Desktop Actions

Also  - are you letting the file manager handle the Desktop?, most issues here with marlin occur when that option is enabled, marlin works better, (here), when it's disabled. 
(unity/nautilus is likely better when the FM handles the Desktop

---

### Post by ronacc on 2012-08-05
what am I missing here ? ppa-purged everything to do with marlin , completey
removed marlin readded the marlin-devs pps reinstalled marlin , I still get this ```
[INFO 15:57:58.710735] Welcome to Marlin
[INFO 15:57:58.710830] Version: 0.1
[INFO 15:57:58.710879] Report any issues/bugs you might find to http://bugs.launchpad.net/marlin
[FATAL 15:57:58.866842] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.866919] marlin will not function properly.
[FATAL 15:57:58.866970] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.867006] marlin will not function properly.
[FATAL 15:57:58.867081] [GLib-GObject] g_object_unref: assertion `G_IS_OBJECT (object)' failed
[FATAL 15:57:58.867118] marlin will not function properly.
[FATAL 15:57:58.905227] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.905296] marlin will not function properly.
[FATAL 15:57:58.905340] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.905377] marlin will not function properly.
[FATAL 15:57:58.905450] [GLib-GObject] g_object_unref: assertion `G_IS_OBJECT (object)' failed
[FATAL 15:57:58.905485] marlin will not function properly.
[WARN 15:57:58.934966] gof-directory-async.vala:92: dir file:///home/ron ref_count 2
[INFO 15:57:58.935205] plugin.vala:121: CANCEL
[WARN 15:57:58.935257] plugin.vala:136: CTags Plugin dir file:///home/ron
[INFO 15:57:58.940636] slot_active file:///home/ron
[INFO 15:57:58.940733] slot_active > merge menus
[FATAL 15:57:58.953683] [GLib] g_strsplit: assertion `string != NULL' failed
[FATAL 15:57:58.953764] marlin will not function properly.
Segmentation fault (core dumped)

```

sys is a fresh install of aug 3 daily updated to the 3.5.0-8 kernel about an hour ago . Note I have been getting the same on my updated precise with both the 3.5.0-7 and -8 kernels .

---

### Post by mc4man on 2012-08-05
> **ronacc said:**
> what am I missing here ? ppa-purged everything to do with marlin , completey
removed marlin readded the marlin-devs pps reinstalled marlin , I still get this ```
[INFO 15:57:58.710735] Welcome to Marlin
[INFO 15:57:58.710830] Version: 0.1
[INFO 15:57:58.710879] Report any issues/bugs you might find to http://bugs.launchpad.net/marlin
[FATAL 15:57:58.866842] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.866919] marlin will not function properly.
[FATAL 15:57:58.866970] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.867006] marlin will not function properly.
[FATAL 15:57:58.867081] [GLib-GObject] g_object_unref: assertion `G_IS_OBJECT (object)' failed
[FATAL 15:57:58.867118] marlin will not function properly.
[FATAL 15:57:58.905227] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.905296] marlin will not function properly.
[FATAL 15:57:58.905340] [GLib-GIO] g_file_info_get_attribute_uint64: assertion `G_IS_FILE_INFO (info)' failed
[FATAL 15:57:58.905377] marlin will not function properly.
[FATAL 15:57:58.905450] [GLib-GObject] g_object_unref: assertion `G_IS_OBJECT (object)' failed
[FATAL 15:57:58.905485] marlin will not function properly.
[WARN 15:57:58.934966] gof-directory-async.vala:92: dir file:///home/ron ref_count 2
[INFO 15:57:58.935205] plugin.vala:121: CANCEL
[WARN 15:57:58.935257] plugin.vala:136: CTags Plugin dir file:///home/ron
[INFO 15:57:58.940636] slot_active file:///home/ron
[INFO 15:57:58.940733] slot_active > merge menus
[FATAL 15:57:58.953683] [GLib] g_strsplit: assertion `string != NULL' failed
[FATAL 15:57:58.953764] marlin will not function properly.
Segmentation fault (core dumped)

```

sys is a fresh install of aug 3 daily updated to the 3.5.0-8 kernel about an hour ago . Note I have been getting the same on my updated precise with both the 3.5.0-7 and -8 kernels .

I can eventually force marlin to produce the same & or similar 'fatals', see screen, though it doesn't segfault here because of.
I'd try disabling the Desktop & or in a new user.
Otherwise maybe install marlin-dbg, run it thru the debugger & get a bt

---

### Post by effenberg0x0 on 2012-08-05
> **mc4man said:**
> Curious - does marlin show your quicklist entries from launcher when marlin is not yet opened?
Here marlin has 3 'built-in' quicklists, then after opening will add all bookmarks (personal) items
Edit - after a reboot then the Marlin launcher shows default 3 + personal

I'm not sure I understand your question right, let me know if I missed it. I restarted the PC (and thus a fresh new Unity session), only executed a terminal, ps ax | grep -i Marlin (to make sure it was not running) and right-clicked Marlin in the Launcher. It shows me everything (default + custom):
- Standard entries/Bookmarks: Documents, Music, Pictures, Videos, Downloads, Ubuntu One.
- 4 personalized quicklist items (all remote mounts)
- New Window/New Window as root
- Marlin File Manager
- Unlock from Launcher
This exact same items continue to show if I open a Marlin window.

> **mc4man said:**
> As far as the default 3, marlin should switch from "X-Ayatana-Desktop-Shortcuts=" to Actions= (Desktop Actions
Preferably on Tuesdays, except when it's raining :)

> **mc4man said:**
> Also  - are you letting the file manager handle the Desktop?, most issues here with marlin occur when that option is enabled, marlin works better, (here), when it's disabled. 
(unity/nautilus is likely better when the FM handles the Desktop

I have set "File manager handles the desktop" using gnome-tweak-tool, but I'm not sure it still works for Unity. I'll have to check on that, not sure where this key is now. Additionally, I have set Marlin as my default File Manager in Marlin Preferences / Behavior.

---

### Post by mc4man on 2012-08-05
Finally figured out "my" issues with adding folders to 'Personal' in marlin
I guess the idea that you can DnD them isn't correct??, what happens here is you can DnD but only if the folder grabbed doesn't touch any other folder on the way to the sidebar.
If it does then the touched folder is the only place you can DnD

So how to add to Personal?

---

### Post by effenberg0x0 on 2012-08-05
I saw in your video that you use the "icons" view. I've always used the "list" view in Nautilus and now in Marlin. 

On the "list" view, I can DnD them normally to "Personal". Even if the folder you grab touches others in the way. I have switched to "icon" view and indeed I can't drop the folder into the "personal" area if it has touched others in the way there. 

I believe you found a bug :)

Regards,
Effenberg

---

### Post by mc4man on 2012-08-06
You're right - no issue for Marlin in list view

The other way here is while nautilus no longer uses ~/.gtk-bookmarks, other Fm's still do like /marlin & pcmanfm, so can also be added/ordered there.

An 'interesting' addition to ~/.gtk-bookmarks is something like this - 
```
recent:/// Recent
```
The various Fm's that can access it all appear use the same .xbel to populate  initially though after that not sure what goes on.. 

Am still wondering how nautilus deals with Recent over a period of time..

---

