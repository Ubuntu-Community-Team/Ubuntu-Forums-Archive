---
title: "Synaptic Package Manager will not load"
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by gifford on 2014-04-03
Synaptic package manger will not load after latest 14.04 update.
Forced to load it now from the command line.
Also, system is very slow after latest update.
Anyone else having these problems?

---

### Post by 23dornot23d on 2014-04-03
Is that 64 bit or 32 bit ............ 

I am about to upgrade the 64 bit version again to see whats changed lately.

But have you lost aptitude as well ..... or will I still be able to use it ......

well - if you can load it from the command line its probably ok .... so will upgrade now to see.

---

### Post by gifford on 2014-04-03
64 bit. The upgrade has really made my system buggy. Very slow and am not sure why.

---

### Post by 23dornot23d on 2014-04-03
Ok well I have a Timeshift backup - so if its really bad will go back to the last backup ..........

Cheers ....  for the info ..... will check htop out once I get in .........


One thing I have seen already is this again ............

> 
(gtk-update-icon-cache-3.0:31412): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.



I had to install this manually - is there a dependency missing somewhere ....

apt-get install libgdk-pixbuf2.0-dev

Then do

gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache

This was from a clean install of the 3.13.0-17-generic ...... 64 bit version .... well its now 3.13.0-22
or it should be - after reboot.

---

### Post by cariboo on 2014-04-03
@gifford, are you sure your latest update completed? I'd suggest you run:

```
sudo apt-get -f install
```

just to make sure.

---

### Post by zeke2135 on 2014-04-03
I've got miscellaneous problems including the synaptic issue: (edited to add a couple more issues)

synaptic will not load from launcher or dash - runs from command line only
system settings/network gives me an error message that the network services are incompatible with this version
sound does not work - I just get a dummy output entry in sound settings
system is slow and jerky
system settings/Appearances tends to crash (i.e. just shuts down the system settings dialog
can't restart from menu - only get dialog to log out (not 100% sure this is new))
can't shutdown from lightdm screen - it asks me if I'm sure I want to shut down, but I don't see a way to actually tell it yes (also not sure this is new)
unit-settings-daemon has crashed at least once

I tried a few things, like reinstalling pulseaudio, reinstalling the nvidia driver (331-updates), boot from 3.13.0-21 instead of 3.13.0-22. This is pretty much the extent of my troubleshooting abilities...

These issues by the way are pretty much the same on two machines, except the network error in system settings only happens on one of them.

---

### Post by 23dornot23d on 2014-04-03
Synaptic is running fine for me and the whole thing is very snappy and smooth ..... for the graphics and cairo-dock
[IMG]http://i.minus.com/ibldR8FuHvsdcZ.png[/IMG]

As you can see I am in KDE though - should I try Unity out now .......... 

* Unity slow laggy and no synaptic ......  and no top bar icons or logout .... nothing showing ..... black bar only ....

One thing it is asking again is to install flash for videos to play - does it not get installed in the latest version

_________________________________________________

I do get a warning in synaptic - but it worked ok in KDE
(synaptic:14595): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
Preconfiguring packages ...
Selecting previously unselected package libnss3-1d:amd64.
(Reading database ... 95%


No SOUND though ........ nothing showing in hardware to pick neither other than dummy output

---

### Post by plumlis on 2014-04-03
Same issue to me.
After upgrade 5 min ago,my system go slow.
synaptic and ubuntu Software centrer could not load.and network manager won't load too.
by the way,I even can't load 3D driver with my intel graph card,I checked and it said i'm running on Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits).

---

### Post by grumblebum2 on 2014-04-03
Appears to be a session/permissions start up issue.
Seeing the same with synaptic and
**polkit-gnome-authentication-agent-1** not running.
```
Trusty:~$ /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

** (polkit-gnome-authentication-agent-1:11186): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(polkit-gnome-authentication-agent-1:11186): polkit-gnome-1-WARNING **: Unable to determine the session we are in: No session for pid 11186
```

---

### Post by su:bhatta on 2014-04-03
> **23dornot23d said:**
> Synaptic is running fine for me and the whole thing is very snappy and smooth ..... for the graphics and cairo-dock

One thing it is asking again is to install flash for videos to play - does it not get installed in the latest version

_________________________________________________

I do get a warning in synaptic - but it worked ok in KDE
(synaptic:14595): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
Preconfiguring packages ...
Selecting previously unselected package libnss3-1d:amd64.
(Reading database ... 95%


No SOUND though ........ nothing showing in hardware to pick neither other than dummy output

I am having the Flash plugin thingy for weeks now. 
I never have chose to 'Run this Action Now', without that , my youtube works perfectly. 
I dont know why that message pops up in the KDE session only. 
In XFCE4 & Gnome it does not come up though.

Also, I have noticed 'synaptic:14595): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed' for sometime now, maybe a week.
But doesn't interrupt use of Synaptic or installing anything.

But sound is alright. 
Losing sound would have been ghastly, this is my audio production system

---

### Post by evan8 on 2014-04-04
same here  also just formatted and freshly installed. still not working. and software center just lags my computer and never starts. i seem to have no permission to do anything. can't even install gksu

---

### Post by su:bhatta on 2014-04-04
> **evan8 said:**
> same here  also just formatted and freshly installed. still not working. and software center just lags my computer and never starts. i seem to have no permission to do anything. can't even install gksu

Did you update and upgrade the fresh install?

```
sudo apt-get update
sudo apt-get upgrade
```

What is the output when you are running software-center from the terminal?

Maybe post a new thread with that ?

---

### Post by TomasKrchnak on 2014-04-04
I join you all with the same issues. So far what I can confirm:

- sound doesn't work (Dummy Output) 
- whole bunch of permission problems: Settings nearly paralized, can't change user details, additional drivers, ...
- Restart & Shutdown popups are gone, can't even use 'sudo shutdown now', always switches me to root AND NOTHING HAPPENING. can't turn my machine off without pushing the power button, or in my case holding it for a few seconds (since I don't have physical reboot button).
- Ubuntu Software Center unusable, crashes, permission problems, ...
- cannot mount external drives through GUI, but 'sudo mount /dev /media' works

[ATTACH=CONFIG]251703[/ATTACH][ATTACH=CONFIG]251704[/ATTACH]

In fact this is somewhat epic fail from Ubuntu, yesterday I finished clean install of 14.04 and this morning my PC is barely usable. But I guess we're still in beta though.. :-(

EDIT:// Just did a clean install, installed updates, rebooted and my system is AGAIN messed up as above. So beware, in today's updates there must be something rotten inside...

---

### Post by plumlis on 2014-04-04
one more issue:I'm on intel graph card and I cant get compiz working after this upgrade.

---

### Post by ajgreeny on 2014-04-04
I have just this minute updated my Ubuntu with unity, 64 bit using an intel integrated HD4000 graphic chip, and have had no problem at all with the update; everything is just as snappy as before, compiz is still working, and all still looks good.

I have lost the style of login greeter screen that I used to have, with the login box middle left of the screen, and it has since yesterday or the day before, changed to a login box bang in the middle of the screen, looking quite ugly, but it still works fine so I am not too worried by that, though it looks rather old fashioned compared to the old style greeter.

---

### Post by zeke2135 on 2014-04-04
After updates that showed up overnight, all the problems I was having cleared up and everything is working.

---

### Post by 23dornot23d on 2014-04-04
I have just done another upgrade - and the additional drivers dialogue is back ........ ;)

[IMG]http://i.minus.com/ibv5lH3CddMoru.png[/IMG]

and when I change to Unity = synaptic working again .....

but no top bar still or icons or choices from it ..... and lightdm does not show up - but at least now its re-instated it
does go straight through to unity. ( thing is no way to log out to lightdm ) so ctrl+alt+f1 stop lightdm and start kdm to get
to my other choices of desktops

[IMG]http://i.minus.com/ibmODFSaOpPjki.png[/IMG]


Sound is still NOT working - and pulseaudio is loaded .... etc ( might be able to make it out on this screenshot above )

---

### Post by TomasKrchnak on 2014-04-04
> **zeke2135 said:**
> After updates that showed up overnight, all the problems I was having cleared up and everything is working.

Can confirm that. If you're using anything else than Main Server as your download location, change it to Main. I was having issues with updates not showing up (Czech mirror), but after the change I managed to fix all of my issues mentioned above.

Direct steps:

1) delete all regional subdomains from the urls in this file (in my case "deb [http://**cz](http://**cz).**archive.ubuntu.com/ubuntu/ trusty main restricted" -> "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted"
```
sudo nano /etc/apt/sources.list
```

2) update
```
sudo apt-get update
```

3) upgrade
```
sudo apt-get upgrade
```

4) reboot
```
sudo reboot
```

It might as well be possible that in the next hours updates will be mirrored globally, so this won't be necessary. But if you're out of time like me :-) good luck

---

### Post by 23dornot23d on 2014-04-04
Cheers - the latest upgrades fixed most things now ..........

Only the top bar in Unity is not showing.

And cannot logout without doing - Ctrl+Alt+F1 then - reboot - or shutdown now

But its interesting using Unity ......** type Logout into it **...... see what you get .........

---

### Post by gifford on 2014-04-04
Latest upgrade does seem to have fixed most things. Everything was borked for me..graphics, permissions, etc.
I could not install with software updater, stated I did not have permission so used CL and it seems to have cleared it up.

---

### Post by kansasnoob on 2014-04-08
This hit me today for the first time :mad:

I can launch synaptic via terminal but not from the gui in the menu :(

Maybe some of the devs keep using old templates including broken code to apply updates?

---

### Post by ventrical on 2014-04-08
Actually .. just a while ago , synaptic from unity gui rescued a busted kernel in an original lubuntu install running unity-desktop overclocked @5.120GHz!

---

### Post by ventrical on 2014-04-08
> **ajgreeny said:**
> I have just this minute updated my Ubuntu with unity, 64 bit using an intel integrated HD4000 graphic chip, and have had no problem at all with the update; everything is just as snappy as before, compiz is still working, and all still looks good.

I have lost the style of login greeter screen that I used to have, with the login box middle left of the screen, and it has since yesterday or the day before, changed to a login box bang in the middle of the screen, looking quite ugly, but it still works fine so I am not too worried by that, though it looks rather old fashioned compared to the old style greeter.


 I had a very cool phenomenon happen to me while using synaptic package manager today from kernel 3.13.0-8 . I had originally updated from terminal <sudo apt-get update/dist-upgrade>  yesterday after first back-clocking to 4.GHz. After the update was done I had no network  and was pointed to llvmpipe with the new kernel 3.13.0-23 update. My desktop was useless pretty well. I decided (just on a fluke) to run synaptic after booting into the 3.13.0-8 kernel (which gave me network and proper graphics driver and it then proceded to re-install the kernels (actually it removed the original 3.13.0-23 and installed the newly downloaded 3.13.0.23 from synaptic). The result is that the unity0desktop installed on top of Lubuntu is working perfectly restored as it's previous kernel 3.13.0-8.

 basically .. synaptic is working excpetionally. well in these parts ! :)lol

edit:

ok .. didn't see any header on the OP but now see that this is 64 bit and I am running 32bit on my OC box.

---

### Post by kansasnoob on 2014-04-08
Currently the command called is:

```
synaptic-pkexec
```

Which is clearly wrong!

---

### Post by ventrical on 2014-04-08
Works fine on 64bit.

---

### Post by orj-gmail on 2014-04-08
> **kansasnoob said:**
> This hit me today for the first time :mad:

I can launch synaptic via terminal but not from the gui in the menu :(

Maybe some of the devs keep using old templates including broken code to apply updates?

since 2 or3 days synaptic is starting very slow (needs 1-2 minutes).

Edit: with the updates of today 09-04-14 the problem wit synaptic is gone.

---

### Post by cariboo on 2014-04-08
I had the problem with synaptic not starting a couple of days ago, but updates fixed it, the exec line in /usr/share/applications/synaptic.desktop looks like this:

```
Exec=synaptic-pkexec
```

@kansasnoob, are you using another mirror, instead of the main one?

---

### Post by kansasnoob on 2014-04-09
> **cariboo907 said:**
> I had the problem with synaptic not starting a couple of days ago, but updates fixed it, the exec line in /usr/share/applications/synaptic.desktop looks like this:

```
Exec=synaptic-pkexec
```

@kansasnoob, are you using another mirror, instead of the main one?

I'm OK now.

In between times I was dealing with a Saucy bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

Updating/upgrading Saucy packages was a freaking nightmare so I suspect there are just problems with the Ubuntu repos.

Maybe it has to do with dropping Ubuntu One?

Even zsync has been unreliable.

---

### Post by TBeholder on 2014-05-26
I got it funnier  - same ```
GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
``` in terminal - but after that it still works and installs packages. So much for "CRITICAL**".
Xubuntu trusty
synaptic v. 0.81.1
libglib2.0-* v. 2.40.0-2

---

### Post by philinux on 2014-05-26
> **TBeholder said:**
> I got it funnier  - same ```
GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
``` in terminal - but after that it still works and installs packages. So much for "CRITICAL**".
Xubuntu trusty
synaptic v. 0.81.1
libglib2.0-* v. 2.40.0-2

You must have missed the large banner on this forum. This is a thread related to Trusty 14.04 version

**This forum is for the discussion of Utopic Unicorn issues only.**

If you have trouble with 14.04 please create a thread in the main support forums.

Closed

---

