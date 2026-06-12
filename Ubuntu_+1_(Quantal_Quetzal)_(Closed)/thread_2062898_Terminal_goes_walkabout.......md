---
title: "Terminal goes walkabout......"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by robert shearer on 2012-09-25
Today the terminal has to be re-added to my launcher on every boot.
This is despite locking it to the launcher each time I add it. It remains for the remainder of the session whether in use or not.
However, upon reboot it has done a runner.

Is it only me it skips out on or are others seeing this too and if so any thoughts..?


Oh, and anyone else getting an **Amazon** icon in the launcher !! on boot or have I got the "extra-special indicator-shopping app"...???  :-)  
(Or is it pay-back for deleting indicator-shopping immediately after install.)

---

### Post by cariboo on 2012-09-26
The terminal icon stays where it's supposed on my install.

> Oh, and anyone else getting an Amazon icon in the launcher !! on boot or have I got the "extra-special indicator-shopping app"...???   
(Or is it pay-back for deleting indicator-shopping immediately after install.)

The Amazon and Ubuntu One icons are now a part of the default launcher, I removed both, as soon as I saw them on my install. :)

---

### Post by mc4man on 2012-09-26
There is a current bug about adding icons to the launcher
If you start an app & r. click > lock to launcher then it will only last for the session

To make persistent remove launcher if there, then  drag & drop from the Dash (or wherever else the <whatever>.desktop resides
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054645](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054645)

---

### Post by robert shearer on 2012-09-26
Thanks for the prompt replies...
Additional to you useful instructions I have now found the following...
When I start new applications their icon appears **below **the floppy and disk icons.
Anything locked to the launcher there will be lost at logout or reboot.

However, if I lock to launcher and then **drag the icon up above the workspace-switcher** it will remain persistant.

Marking as solved.

@cariboo > The Amazon and Ubuntu One icons are now a part of the default launcher

Choke !
If only, instead of trying to emulate all the other bigger players, Conanical were to apply niche marketing strategy.... sigh,...
 I would have been thrilled to find a HDTracks scope in place of the Amazon one. (of which we cannot use down here at the bottom of the world)

Real music for people with ears and not lossy mp3 pap.

[https://www.hdtracks.com/](https://www.hdtracks.com/)

---

### Post by mc4man on 2012-09-26
> **robert shearer said:**
> Thanks for the prompt replies...
Additional to you useful instructions I have now found the following...
When I start new applications their icon appears **below **the floppy and disk icons.

That may be because you dragged the device/Ws icons above the current favorites?

Or - there is a new way launcher icons are ordered in dconf & a 'placeholder' for running apps (apps started that aren't currently in the launcher

It's called 'unity://running-apps' & by default would be listed above the expo & devices  ones - see screen
It's possible 'unity://running-apps' has been moved to the last listed or may have been removed from list altogether

You can check in dconf-editor or from gsettings
(note that that line in dconf can be very frustrating to manually edit in dconf-editor, gsettings is easier

*I think there may be a way that entry for running apps can be 'inadvertently' removed, if so then all running apps will go to the bottom of launcher

Edit: 
The best way to see what goes on is to open dconf-editor go to com.canonical.Unity.Launcher, then start moving things around & watch what happens in that key

---

### Post by robert shearer on 2012-09-26
> That may be because you dragged the device icons above the current favorites?

Nope,new install and I had not had time to drag anything then it all went south after running an update when the launcher aquired the Ubuntu music store and Amazon icons.
These both appeared below the disk/floppy & expo icons and from there the odd behaviour with other apps icons opening below became the norm.

> It's called 'unity://running-apps' & by default would be listed above the expo & devices ones - see screen
Checked and mine looks like yours.'unity://running-apps'where they should be.

Perhaps when I dragged the terminal up that has reset it as now apps are opening above the expo.
Methinks it was the update that moved things and by removing Amazon and lifting the Music store icon this has restored 'unity://running-apps' to its proper place ??

---

### Post by mc4man on 2012-09-26
> **robert shearer said:**
> 
Perhaps when I dragged the terminal up that has reset it as now apps are opening above the expo.
Methinks it was the update that moved things and by removing Amazon and lifting the Music store icon this has restored 'unity://running-apps' to its proper place ??
Could be? If I fool around with it enough there are some weird things that can happen. Likely will shake out at some point
(I've yet to get the amazon & music store icons on this install, 1 wk. old, fully updated

What's clear though is if you pin a running app you need to move it or it will disappear next session (or DnD to add to launcher which is basically what you're doing when moving

---

### Post by robert shearer on 2012-09-26
> I've yet to get the amazon & music store icons on this install, 1 wk. old, fully updated

Here is how it went for me....
```
sudo apt-get purge indicator-shopping
```
then
```
sudo apt-get update
sudo apt-get upgrade
```

and ta daa, Amazon and Ubuntu music store icons appeared in the launcher.
(hence my comments in the first post...:) )
I wonder if it is an either/or situation and, "damnit, you're going to have shopping  no matter what..."  :-)

---

