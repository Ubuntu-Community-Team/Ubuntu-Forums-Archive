---
title: "GNOME 3 PPA for Raring"
date: 2013-03-02
forum: Ubuntu Development Version
---

### Post by jbicha on 2013-03-02
We've now pushed many pieces of the GNOME 3.8 Beta (3.7.90) to the GNOME 3 PPA.

If you have already been using the Staging PPA, be sure you alsohave the GNOME3 PPA enabled for raring as we will be removing the duplicate packages there soon. The Staging PPA is for the pieces of GNOME 3.7/3.8 that still need work or have known regressions. For a longer explanation, see my [email]("https://lists.launchpad.net/ubuntu-gnome/msg00273.html") to the ubuntu-gnome list.

---

### Post by screaminj3sus on 2013-03-02
added the ppa and most things seem to work alright, but the two finger scroll option in gnome control center is broken and has no effect, edge scrolls no matter what.

I noticed gnome-shell seems way quicker now :) Also fixed some very annoying bugs, like the memory leaks that plague gnome 3.6 still and tearing on intel ivybridge. Still got some rough edges (touch issue mentioned above, gnome-shell crashes sometimes, clicking networks settings from the gnome-shell network indicator does nothing) but the most part looks like gnome 3.8 will be a much better release than 3.6

EDIT: there seems to be a dependency issue with the librsvg package in the ppa, it can't be upgraded because it tries to remove a bunch of other packages.

---

### Post by VinDSL on 2013-03-02
> **jbicha said:**
> If you have already been using the Staging PPA, be sure you also have the GNOME3 PPA enabled [...]
Yep, had them both enabled for a week or two, plus ricotz testing.  ;)

---

### Post by jbicha on 2013-03-03
> **screaminj3sus said:**
> there seems to be a dependency issue with the librsvg package in the ppa, it can't be upgraded because it tries to remove a bunch of other packages.

I'm not sure whether we want the new pango in the GNOME3 PPA or not so I removed the new librsvg until we decide. You can revert to the regular raring version by running
 ```
sudo apt-get install librsvg2-2=2.36.4-1 librsvg2-common=2.36.4-1
```

---

### Post by Greg K Nicholson on 2013-03-12
I just tried upgrading Ubuntu 13.04 using the Gnome 3 team PPA, but after restarting I found a major bug.

The amount of memory used by Gnome Shell quickly grew; within minutes, top reported that gnome-shell was using about 2000 MB of virtual memory plus 850 MB of resident memory; my computer has 1 GB of memory. The shell was virtually unresponsive. Eventually the whole computer was so unresponsive that even holding the power button didn't kill the power. After a while the shell crashed.

Possibly related (or possibly not), Gnome Shell displayed a black desktop background. Before the shell started and after it crashed, my background image appeared properly, which suggests it was always present behind Gnome Shell.

I saw the same symptoms when I tried this upgrade a couple of hours ago, and a couple of days ago. This time I ensured no extensions were installed that might be incompatible.

The offending version of gnome-shell is 3.7.91-0ubuntu1~raring3. I have the standard ubuntu-gnome-desktop stack (congratulations on the promotion!) without ubuntu-desktop (but with ubuntu-standard, ubuntu-minimal, linux-generic, linux-firmware, language-pack-gnome-en and very little else). I don't have the staging PPA or any of its packages installed.

I've now removed the Gnome 3 team PPA using ppa-purge, and Gnome 3.6 is running nicely. Has anyone else experienced similar symptoms with Gnome 3.7 from the PPA? Any ideas what might be causing this?

---

### Post by cariboo on 2013-03-12
I ran into the same thing, with all 3 ppas enabled. Even after upgrading several times, it just kept looping, gnome-shell would run until it used all the ram and swap, then restart. I did a fresh install this past weekend, but haven't added the ppas back as of yet.

---

### Post by Harry33 on 2013-03-13
> **Greg K Nicholson said:**
> 
...
I've now removed the Gnome 3 team PPA using ppa-purge, and Gnome 3.6 is running nicely. Has anyone else experienced similar symptoms with Gnome 3.7 from the PPA? Any ideas what might be causing this?

I use constantly Gnome3 and Gnome3 Staging PPA's. No other PPA's enabled.
I use nvidia_313 proprietary drivers with my Nvidia 285GTX card.
No issues with gnome-shell ATM.

---

### Post by Mr.JJ on 2013-03-13
I had this issue but with backslide extension. Without that extension shell is working fine. You can create an issue in launchpad/bugzilla (gnome 3.8 is not released yet, so sooner the better).

---

### Post by dino99 on 2013-03-13
Have activated that ppa, then upgraded the packages. But now nautilus fail to load from the Places menu (silently). 
So going for a logout/in. Thats made the trick :P

---

### Post by VinDSL on 2013-03-13
> **Harry33 said:**
> I use constantly Gnome3 and Gnome3 Staging PPA's. No other PPA's enabled.[...]
I have those PPAs enabled, plus Ricotz Testing.  Nothing unusual is happening here, at the moment.

I turned on my rig 45 minutes ago.  

I'm listening to podcasts via Banshee (a heavy hitter Mono app) in the background.

I updated my FaceBook account via Chromium Canary 27, and played a Flash game (which is very resource intensive).

Then, I came over here to Ubu Forums.  Everything simmered down just fine.

Looking at my Conky widgets, nothing is looping, running away, maxing out, et cetera.

HTOP output...
```
Tasks: 216, 323 thr; 1 running
Load average: 0.89 1.04 1.28
Mem[459/1002MB]
Swp[381/1025MB]
Uptime: 00:46:42

```

Nautilus working fine from Places.  ;)

---

### Post by pferraro on 2013-03-13
@jbicha,
Do you have any intention of uploading evolution to the gnome3-staging ppa?  The version in the official raring repo does not play well with the 3.7.91 version of evolution-data-server.

---

### Post by sgage on 2013-03-13
When using the Gnome 3 PPA's, is it necessary/desirable to also enable proposed?

(BTW, I made a fresh UGR today, and the installation was smooth and fast. And the 'slide show' during installation even showed the version as Ubuntu GNOME 13.04.)

---

### Post by Harry33 on 2013-03-14
> **sgage said:**
> When using the Gnome 3 PPA's, is it necessary/desirable to also enable proposed?

(BTW, I made a fresh UGR today, and the installation was smooth and fast. And the 'slide show' during installation even showed the version as Ubuntu GNOME 13.04.)

Well, enabling RR-proposed with Gnome3 and Gnome3 Staging PPA's may create dependency issues.
One example here.

We have right now the new udev (175-0ubuntu20) and systemd (198-0ubuntu2) packages in RR-proposed.
The new libudev1 comes from systemd source and the the old libudev0 from udev source is dropped.
However, the gvs packages in Gnome3 Staging PPA (1.15.4-0ubuntu2~raring2) still depends on the droppped libudev0.
There is a new gvs in RR-proposed, depending on the new libudev1, but the numbering of this is lower and thus it does not get upgraded.

So, be carefull with RR-proposed when using additional PPA's.

---

### Post by zika on 2013-03-14
> **Harry33 said:**
> Well, enabling RR-proposed with Gnome3 and Gnome3 Staging PPA's may create dependency issues.
One example here.

We have right now the new udev (175-0ubuntu20) and systemd (198-0ubuntu2) packages in RR-proposed.
The new libudev1 comes from systemd source and the the old libudev0 from udev source is dropped.
However, the gvs packages in Gnome3 Staging PPA (1.15.4-0ubuntu2~raring2) still depends on the droppped libudev0.
There is a new gvs in RR-proposed, depending on the new libudev1, but the numbering of this is lower and thus it does not get upgraded.

So, be carefull with RR-proposed when using additional PPA's.
What is going to be the remedy: simple change of version for gvfs? Or ppa-purge of PPA?

---

### Post by Harry33 on 2013-03-14
> **zika said:**
> What is going to be the remedy: simple change of version for gvs? Or ppa-purge of PPA?

We now have the new gvs in Gnome3 Staging PPA (v.1.15.4-0ubuntu2~raring4) and this dependency issue is solved.
Now the old libudev0 can be removed.

---

### Post by zika on 2013-03-14
There is even ubuntu4 version of gvfs, I'll see where that comes from...

---

### Post by serdotlinecho on 2013-03-14
Ubuntu-GNOME 13.04 daily images available for [download]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/") :D

---

### Post by Harry33 on 2013-03-14
> **serdotlinecho said:**
> Ubuntu-GNOME 13.04 available for [download]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/") :D

More specifically, that is a daily development build of Ubuntu-Gnome 13.04.

---

### Post by zika on 2013-03-14
> **Harry33 said:**
> More specifically, that is a daily development build of Ubuntu-Gnome 13.04.Already zsync-ed and put in aliases... ;)
(Beware of the same name for .iso file...)

---

### Post by zika on 2013-03-15
Anyone else having truoble with awakening screen after blank i GnomeShell?

---

### Post by VinDSL on 2013-03-15
> **zika said:**
> Anyone else having truoble with awakening screen after blank i GnomeShell?
Yes, I am.  :(

I've been disabling screen blanking during the session, so I cannot speak to that.

However, if I power-up my rig and walk away -- and the screen blanks before I return -- I have to shell out & restart.

---

### Post by zika on 2013-03-15
> **VinDSL said:**
> Yes, I am.  :(

I've been disabling screen blanking during the session, so I cannot speak to that.

However, if I power-up my rig and walk away -- and the screen blanks before I return -- I have to shell out & restart.Mixed feelings:
- I'm happy that it is not me that broke that...
- I'm not happy for You/me that problem exists...
;)

---

### Post by zika on 2013-03-15
What are all GnomeShell available modes?

---

### Post by VinDSL on 2013-03-15
> **zika said:**
> Mixed feelings:
- I'm happy that it is not me that broke that...
- I'm not happy for You/me that problem exists...
;)
I enabled blanking during the session, and it won't awaken either, just like the blanking at the login screen.

So, back to "Never" blanking (during the session) for me.  ;)

---

### Post by zika on 2013-03-16
> **zika said:**
> What are all GnomeShell available modes?OK, not "all"... Name a few... ;)

---

### Post by VinDSL on 2013-03-16
> **zika said:**
> What are all GnomeShell available modes?

> **zika said:**
> OK, not "all"... Name a few... ;)
Not sure I understand the question :confused:

CLI reports...

```
vindsl@Zuul:~$ gnome-shell --list-modes
gdm
initial-setup
user
classic
vindsl@Zuul:~$ 
```

---

### Post by VinDSL on 2013-03-16
Hrm... Now you got me thinking.  It's sort of like phonetics.

How does one pronounce the word "the" -- hard or soft?!?!?

[LIST]
[*]Hard: "the" is spoken as 'thee'
[*]Soft: "the" is spoken as 'thuh' 
[/LIST]

Are you asking if 'thee' or 'thuh' mode options change with 'thee' or 'thuh' PPA that you use?

Here's my source...

```
vindsl@Zuul:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.7.91+git20130313.a87e0f02-0ubuntu1~13.04~ricotz0
  Candidate: 3.7.91+git20130313.a87e0f02-0ubuntu1~13.04~ricotz0
  Version table:
 *** 3.7.91+git20130313.a87e0f02-0ubuntu1~13.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     3.7.91-0ubuntu1~raring3 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     3.6.3.1-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages
     3.6.2-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
vindsl@Zuul:~$ 
```

I *suppose* it depends on how you break down the third "vowel".  LoL!  :D

Maybe I'll disable Ricotz Testing PPA, and see if Gnome 3 PPA offers different modes...

---

### Post by zika on 2013-03-16
> **VinDSL said:**
> Not sure I understand the question :confused:

CLI reports...

```
vindsl@Zuul:~$ gnome-shell --list-modes
gdm
initial-setup
user
classic
vindsl@Zuul:~$ 
```Thank You. I forgot to write that I've found that already... Nevertheless thank You, again...

---

### Post by VinDSL on 2013-03-16
You're welcome!

BTW, concerning other issues... 

I installed the latest Liquorix Kernel yesterday, to see if it made any diff.


```
vindsl@Zuul:~$ echo && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo

Kernel Release: Linux 3.7.0-10.dmz.2-liquorix-686

vindsl@Zuul:~$
```

On the screen blanking issue, I should quantify that my display DOES awake from blanking but, it is stuck on the huge 'digital clock screen'. No amount of dancing_on_the_keyboard would get me back to the desktop with the Ubu kernel.

With Liquorix, I'm able to break out of the 'digital clock display' by shelling out, and back in again.

I tried this shelling out workaround several times with Linux 3.9.0-rc2 with no joy.  Just saying...

Also, I don't know about you, but I haven't seen the Universal Access icon in the top panel (indicator/notification area) for a while.

The GDM login screen shows the Universal Access icon, in the top-right corner, but it disappears from the desktop, in both GS & Unity sessions.

Is your Universal Access icon still present?

---

### Post by VinDSL on 2013-03-16
> **Greg K Nicholson said:**
> I just tried upgrading Ubuntu 13.04 using the Gnome 3 team PPA, but after restarting I found a major bug.

The amount of memory used by Gnome Shell quickly grew; within minutes, top reported that gnome-shell was using about 2000 MB of virtual memory plus 850 MB of resident memory; my computer has 1 GB of memory. [...]
That reminds me (thanks)...

I ran across a similar situation, the other night.

Mem was bring consumed at an alarming rate -- dittos for CPU usage (pegged @ 100%).

Luckily, I was able to do forensics, before everything ground to a halt.

Offending package turned out to be Plank believe_it_or_not.  First problem I've had with Plank...

Anyway, I killed Plank.  Everything gradually returned to normal.  I reloaded Plank, and haven't had a problem since.

Go figure...  ;)

---

### Post by cariboo on 2013-03-16
I don't know if it is a Raring problem, or by design, but I don't have a Universal Access icon in Unity either.

---

### Post by zika on 2013-03-16
No UA icon either but I'm not sure if I'm to blame or...

---

### Post by VinDSL on 2013-03-16
> **cariboo907 said:**
> I don't know if it is a Raring problem, or by design, but I don't have a Universal Access icon in Unity either.> **zika said:**
> No UA icon either but I'm not sure if I'm to blame or...
Interesting!

If you'll remember, I was having a prob with (ahem) caribou-antler virtual keyboards popping up all over the place, for a week or so.

When I was trying to put_a_finger_on_it I noticed that the Universal Access icon would appear briefly in the panel (when loading the session) then almost immediately disappear, moments before the pesky virtual keyboard popped up.

Now, I'm not getting any virtual keyboards (yeeeaaah), but also no Universal Access icon.  It doesn't appear at all, on my desktops -- not even momentarily.

Anyway, thanks for the feedback!  ;)

---

### Post by zika on 2013-03-16
I do get virtual kb in GDM, but not any more in GS...

---

### Post by mc4man on 2013-03-16
> **cariboo907 said:**
> I don't know if it is a Raring problem, or by design, but I don't have a Universal Access icon in Unity either. 
Likely won't show unless some?? feature(s)  are  enabled in Universal Access (system settings

---

### Post by cariboo on 2013-03-16
I just enabled the Gnome3 team and Gnome3 staging ppas, did the update and dist-upgrade, and now it takes what seems forever after I click on my user name for the password box to come up, once I've entered my password, it never does load the desktop, or I'm too impatient as after an hour, still no joy. :(

---

### Post by zika on 2013-03-18
> **VinDSL said:**
> Yes, I am.  :(

I've been disabling screen blanking during the session, so I cannot speak to that.

However, if I power-up my rig and walk away -- and the screen blanks before I return -- I have to shell out & restart.
While tinkering and meddling today I've discovered that problem with screen blanking exists only if GDM is active. If I start SB in startx/xinit it works nicely in GS... At least we've got problem a bit more isolated...
I start SB manually```
/usr/bin/gnome-screensaver-command -a
```...

---

### Post by VinDSL on 2013-03-18
> **zika said:**
> While tinkering and meddling today I've discovered that problem with screen blanking exists only if GDM is active. If I start SB in startx/xinit it works nicely in GS... At least we've got problem a bit more isolated...
I start SB manually```
/usr/bin/gnome-screensaver-command -a
```...
A little tinkering, on my part...  ;)

I used GDM to start LXDE/Openbox, the other night, and blanking worked fine in the LXDE session.

Of course, when I'm exiting blanking in LXDE, it doesn't display the huge GDM digital clock screen (with the animated chevrons pointing to the time).  It just goes back to the desktop.

Personally, I think that digital clock screen is causing the blanking problem, e.g. not awaking in GS and Unity.

---

### Post by VinDSL on 2013-03-18
Here's another weird one for you...

After I did a daily update yesterday, window decoration in GS doesn't follow my theme.

So, for giggles, I just replaced gnome-shell from CLI *:

```
vindsl@Zuul:~$ gnome-shell --replace &
      JS LOG: IBus version is too old
Window manager warning: Log level 16: STACK_OP_REMOVE: window 0x24b not in stack
      JS LOG: GNOME Shell started at Mon Mar 18 2013 15:49:05 GMT-0700 (MST)
      JS LOG: loading user theme: /home/vindsl/.themes/GnomishDark/gnome-shell/gnome-shell.css

```

* If you want to try this, leave the terminal window open and minimize it.

After doing the above, window decorations are correct.  LoL! :D

Heh!  What does that IBus warning indicate?!?!?

Usually, it means just what it says.  Guess I should tinker around with IBus, too.

---

### Post by serdotlinecho on 2013-03-18
Alright, gnome-shell 3.7....do whatever you want...

[URL="http://imgur.com/YYGTN7A"]
[IMG]http://i.imgur.com/YYGTN7Al.png[/IMG][/URL]

---

### Post by zika on 2013-03-19
> **VinDSL said:**
> Here's another weird one for you...

After I did a daily update yesterday, window decoration in GS doesn't follow my theme.

So, for giggles, I just replaced gnome-shell from CLI *:

```
vindsl@Zuul:~$ gnome-shell --replace &
      JS LOG: IBus version is too old
Window manager warning: Log level 16: STACK_OP_REMOVE: window 0x24b not in stack
      JS LOG: GNOME Shell started at Mon Mar 18 2013 15:49:05 GMT-0700 (MST)
      JS LOG: loading user theme: /home/vindsl/.themes/GnomishDark/gnome-shell/gnome-shell.css

```

* If you want to try this, leave the terminal window open and minimize it.

After doing the above, window decorations are correct.  LoL! :D

Heh!  What does that IBus warning indicate?!?!?

Usually, it means just what it says.  Guess I should tinker around with IBus, too.
Most of the time I do not even notice decorations... I'll take a look.
Yes IBus warning is there for some time already... I've tried to investigate but no success... Will go back to that once I get some spare time...

---

### Post by zika on 2013-03-19
Any ideas when/if we could expect return of functional fallback sessions in GS?

---

### Post by Harry33 on 2013-03-20
After todays updates in Gnome3 PPA GDM seems to have some trouble starting.
GDM will, however, start but appearing of the login screen is much slower now.
I think this is due to the new gsettings-desktop-schemas (3.7.92).
We may need a newer GDM now.

---

### Post by dino99 on 2013-03-20
nautilus 3.7.90 does not like the latest gsettings-desktop-schemas 3.7.92 : it fails to open, due to an unknown "draw-background"
so hopes to see a new nautilus 3.7.92 landing soon.

---

### Post by Harry33 on 2013-03-20
> **dino99 said:**
> nautilus 3.7.90 does not like the latest gsettings-desktop-schemas 3.7.92 : it fails to open, due to an unknown "draw-background"
so hopes to see a new nautilus 3.7.92 landing soon.

True, I am seeing the same here in addition to the very slow appearing login screen of GDM.
Downgrading gsettings-desktop-schemas back to the version 3.7.5 solves this issue for now.

---

### Post by dino99 on 2013-03-20
> **Harry33 said:**
> True, I am seeing the same here in addition to the very slow appearing login screen of GDM.
Downgrading gsettings-desktop-schemas back to the version 3.7.5 solves this issue for now.

exact, the change made into the previous 3.7.91 have pushed that issue.
Major changes in 3.7.91
+=======================
+* Add keys for the screensaver wallpaper
+* Remove the obsolete draw-background key

so we need an update to nautilus 3.7.92 now

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1157494](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1157494)

---

### Post by Harry33 on 2013-03-20
We have new gsettings-desktop-schemas (v. 3.7.92-0ubuntu1~raring3) in Gnome3 PPA now.
The "draw-background key" is reverted.

---

### Post by dino99 on 2013-03-20
> **Harry33 said:**
> We have new gsettings-desktop-schemas (v. 3.7.92-0ubuntu1~raring3) in Gnome3 PPA now.
The "draw-background key" is reverted.

yes, i've sent an email about the nautilus issue. With that update nautilus now load again normally.

---

### Post by Harry33 on 2013-03-20
> **dino99 said:**
> yes, i've sent an email about the nautilus issue. With that update nautilus now load again normally.

Right, issue solved, for now.

---

### Post by MacBooom on 2013-03-21
Hiya,


Just made the upgrade to the Gnome3 ppa and was messing a bit around, found at that moment that that "Brightness and Lock" wouldn't open.
And then tried to open "gnome-control-center screen" from terminal, which gave me this error:
```
 (gnome-control-center:13835): GLib-GIO-ERROR **: Settings schema 'org.gnome.desktop.screensaver' does not contain a key named 'show-notifications'Trace/breakpoint trap
```


That lead me to [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1117637](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1117637)


And start reading gksu gedit /usr/share/glib-2.0/schemas/org.gnome.desktop.screensaver.gschema.xml , and couldn't find:
```
<key type="b" name="show-notifications">
```


So i followed the bug report and then copied this part from a Fresh Ubuntu-Gnome VM and inserted it, followed the rest of the commands posted in that bugreport:
```
<key type="b" name="show-notifications">
      <default>false</default>
      <summary>Show notifications in the lock screen</summary>
      <description>Whether notifications are shown in the lock screen or not. This only affects the standard experience.</description>
    </key>
```

```

macbooom@Rage-Gaming:~$  dpkg -l | grep gsettings-desktop-schemas 
ii  gsettings-desktop-schemas                 3.7.92-0ubuntu1~raring3                            all          GSettings deskop-wide schemas
macbooom@Rage-Gaming:~$ locate org.gnome.desktop.screensaver 
/usr/share/glib-2.0/schemas/org.gnome.desktop.screensaver.gschema.xml
macbooom@Rage-Gaming:~$ dpkg -S org.gnome.desktop.screensaver
gsettings-desktop-schemas: /usr/share/glib-2.0/schemas/org.gnome.desktop.screensaver.gschema.xml






```


And it's working again

---

### Post by dino99 on 2013-03-21
yes, its the same issue as nautilus had (new gsettings-desktop-schemas trouble). We should get the packages fixed in the coming hours/days/weeks/...  :guitar:

---

### Post by MilesRdz on 2013-03-21
[Gnome 3.8 RC was released...]("https://mail.gnome.org/archives/devel-announce-list/2013-March/msg00004.html")
More 3.8 components to arrive soon in this PPA?

---

### Post by Harry33 on 2013-03-22
> **MilesRdz said:**
> [Gnome 3.8 RC was released...]("https://mail.gnome.org/archives/devel-announce-list/2013-March/msg00004.html")
More 3.8 components to arrive soon in this PPA?

Gnome_3.8rc (=3.7.92) packages can be found also from Gnome3 Staging PPA.
The stable 3.8 will be published next week, on 27th March:

[https://live.gnome.org/action/show/ThreePointSeven](https://live.gnome.org/action/show/ThreePointSeven)

---

### Post by zika on 2013-03-22
Two issues that I was not sure where to put:
1. Evince is crashing after couple of PageDown/Up with a bit more complex documents...
2. Scroll slider vanishes after I release it when browsing folders, especially in OpenFile dialog...
I'm not sure who is to be &#8222;blamed&#8220; for these two because I have all G3 PPAs active and...
At the moment I'm bypassing 1. using Iron/Chromium/FF to read .pdf because even epdfview was not of much help... I hate to introduce Ocular since it would drag a ton of stuff with it... It does not matter, I've used Evince for a long time and it worked OK until recently...

---

### Post by screaminj3sus on 2013-03-22
does the automatic screen dimming on battery not work for anyone else in gnome 3.8? I haven't tried it on UGR yet, but I downloaded the fedora test day gnome 3.7.92 image to test on my laptop earlier, and when on battery with the "dim screen" option enabled it would just stay at full brightness even after like 5 minutes, but manually adjusting it worked fine.

---

### Post by zika on 2013-03-28
Just noticed: Gnome-Classic: I'm unable to change white background...
All 3 PPAs for GS are on and up-to-date...

---

### Post by mc4man on 2013-03-28
> **zika said:**
> Just noticed: Gnome-Classic: I'm unable to change white background...
All 3 PPAs for GS are on and up-to-date...

Is it a 'white background' or an empty ~/Desktop folder
(pretty easy to check

---

### Post by defconoii on 2013-03-28
i noticed the white background as well, so I can confirm this as a bug

---

### Post by zika on 2013-03-28
> **mc4man said:**
> Is it a 'white background' or an empty ~/Desktop folder
(pretty easy to checkFor years now, my Desktop folder is empty...
But, just several days ago, my desktop was black...
Update&#8321;: Yes, if I touch some file in ~/Desktop it shows on the screen (desktop)... If I change settings for background that does not affect Classic
In GnomeTweakTool it is set not to have FM deal with desktop... GTT settings about desktop (background) are not honored in Classic...
In GS background is properly set and honored...
Question: 2 fallback sessions are now depreciated... What is the proper porcedure to purge them from my machine since there is no use of them anymore (broken) and not make any harm to other sessions...?
Update&#8322;: Purge went suprisingly well... Done deal...
Update&#8323;: If I start Classic through startx/xinit only, everything works... Black background and it can be changed through usual channels... If I start through LightDM/GnomeDM it does not work... Ergo, DM are to blame... ;)

---

### Post by mc4man on 2013-03-28
> **zika said:**
> 
Update&#8323;: If I start Classic through startx/xinit only, everything works... Black background and it can be changed through usual channels... If I start through LightDM/GnomeDM it does not work... Ergo, DM are to blame... ;)
Possibly, or maybe something else at play - 
Had a new install don't care about so just added the gs3 ppa's, upgraded, ect.
(the Gnome 3 ppa's have to be the slowest ppa's I've come across in quite some time. Generally LP ppa's are slower than Ubuntu repo's but these take the cake (I do 2-3000+ kB/s with Ubuntu, Gnome 3 averages around 65 kB/s

Anyway noticed that in a Classic session toggling org.gnome.desktop.background On, then Off gives chosen background, picked from the r.click > Change background. (tweak-tool doesn't start
The first toggle lasts for about 10 sec.'s, the 2nd or possibly a 3rd lasts the session. A new login starts over on the Desktop folder, ect., ect.
This is with lightdm, didn't try gdm as of yet..

---

### Post by kevpan815 on 2013-03-28
Why do you need a Gnome PPA when there is now a Ubuntu Gnome Build Available at the Cdimage Server?

---

### Post by MilesRdz on 2013-03-29
> **kevpan815 said:**
> Why do you need a Gnome PPA when there is now a Ubuntu Gnome Build Available at the Cdimage Server?

For Gnome 3.8.

---

### Post by zika on 2013-03-29
> **mc4man said:**
> Possibly, or maybe something else at play - 
Had a new install don't care about so just added the gs3 ppa's, upgraded, ect.
(the Gnome 3 ppa's have to be the slowest ppa's I've come across in quite some time. Generally LP ppa's are slower than Ubuntu repo's but these take the cake (I do 2-3000+ kB/s with Ubuntu, Gnome 3 averages around 65 kB/s

Anyway noticed that in a Classic session toggling org.gnome.desktop.background On, then Off gives chosen background, picked from the r.click > Change background. (tweak-tool doesn't start
The first toggle lasts for about 10 sec.'s, the 2nd or possibly a 3rd lasts the session. A new login starts over on the Desktop folder, ect., ect.
This is with lightdm, didn't try gdm as of yet..I am OK with the fact that it works with startx/xinit since that is my prefered way of working... Less resources, easier to control, ... I'll try Your bypass as soon as I start LightDM/GDM...
Update&#8321;: Yes, it behaves just as You've described, I tried it in GDM, to have a complete set of tests (with Yours from LightDM...)... ;)
At my place I did not change background switch but the one about showing desktop icons...
So```
alias TB='gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.desktop.background show-desktop-icons false'
```does the job... Thank You for insight/hint...

---

### Post by AntoineT on 2013-03-29
> **zika said:**
> Two issues that I was not sure where to put:

2. Scroll slider vanishes after I release it when browsing folders, especially in OpenFile dialog...
I'm not sure who is to be „blamed“ for these two because I have all G3 PPAs active 


I have the same problem (raring+gnome-team/gnome3 PPA) with the scrollbars in nautilus, gedit, evince etc.
Did you by any chance manage to solve the issue?

---

### Post by VinDSL on 2013-03-29
> **AntoineT said:**
> I have the same problem (raring+gnome-team/gnome3 PPA) with the scrollbars in nautilus, gedit, evince etc. [...]
Me too!

I've never mentioned it, because I prefer to use the mouse wheel, anyway.

However, there are times (for instance, editing a large file) when a working scrollbar would be handy. ;)

---

### Post by dino99 on 2013-03-29
to work around that issue, i've set "legacy" option into dconf

---

### Post by Roasted on 2013-03-29
13.04, Gnome3 + Gnome3-Staging + Ricotz PPA installed. Running Gnome Shell 3.8.0.1.

So far I ran into this one issue where my background image is only present when in the activities menu. I took a 10 second screencast that can be seen here:

[http://www.youtube.com/watch?v=NJOoQPHSgxo](http://www.youtube.com/watch?v=NJOoQPHSgxo)

A suggestion in the Gnome IRC channel was to fire up Gnome Tweak Tool and uncheck "Have file manager handle the desktop."

I also ran into a funky issue with my desktop system which is running the Nvidia 313 drivers and has two monitors (primary center, secondary right). I noticed when I get to the login screen, it's entirely empty and gray. I see no icons, no username, no nothing. I also notice that my monitors are switched, as if the system thinks it's primary-right and secondary-left, where it's really primary-left and secondary-right. If I move the cursor up to the top of the screen so it brushes the top edge, the login screen appears but on my secondary monitor. At least at that point I can log in, but it's obvious GDM is out of whack in this setup. I wonder if a dpkg --reconfigure or whatever would realign it?

Other than that I'm liking what I'm seeing so far from Gnome 3.8. I was a little bummed at the removal of the scroll-to-zoom feature in the activities menu, but ironically just yesterday I was trying to find out if there was a hot key that I could hold and scroll to navigate through other workspaces. The lack of scroll-to-zoom, yet the inclusion of larger thumbnails that are laid out more intelligently, coupled with the scroll to navigate to other workspaces feature, is quite nice. I still loved my scroll to zoom, but I also never used workspaces that much. This should make it a bit easier to organize open windows accordingly.

So far, I dig it. Well done Gnome devs. :D

---

### Post by zika on 2013-03-29
> **AntoineT said:**
> I have the same problem (raring+gnome-team/gnome3 PPA) with the scrollbars in nautilus, gedit, evince etc.
Did you by any chance manage to solve the issue?
I have to pay attention to that... I did not notice problems these couple of days...

---

### Post by zika on 2013-03-29
> **dino99 said:**
> to work around that issue, i've set "legacy" option into dconfWhich schema/setting?

---

### Post by zika on 2013-03-29
> **zika said:**
> I am OK with the fact that it works with startx/xinit since that is my prefered way of working... Less resources, easier to control, ... I'll try Your bypass as soon as I start LightDM/GDM...
Update&#8321;: Yes, it behaves just as You've described, I tried it in GDM, to have a complete set of tests (with Yours from LightDM...)... ;)
At my place I did not change background switch but the one about showing desktop icons...
So```
alias TB='gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.desktop.background show-desktop-icons false'
```does the job... Thank You for insight/hint...Pleasant surprise: I've booted now, back from work, and it is black as it should be, in GDM... No need for tinkering... I did not have time to look what upgrades were done in the meantime...
Update&#8321;: Awakening from stand-by still doesn't work if I am in GDM/LightDM... In startx/xinit it does...

---

### Post by VinDSL on 2013-03-29
> **Roasted said:**
> I took a 10 second screencast [...]
Which screencast software are you using?

I haven't found one that's worth a Tinker's *you_know_what*!  ](*,)

That vid came out nice!

---

### Post by paulocr on 2013-03-29
Hello guys,

I have a small issue but still interested in seeing if anyone knows how to solve.
I am using 13.04 and gnome-shell 3.8 with a custom theme.
Once I login there's a small period of time when the default (black, large fonts, ugly theme imho) is displayed and then it switches to the one I like.
I tried checing if there's a place where the default theme is invoked and I also tried checking if I can edit the Default theme but I had no luck.

I made a small, low quality video but I think the issue can be seen.

[http://www.youtube.com/watch?v=xp1PQfREg78](http://www.youtube.com/watch?v=xp1PQfREg78)

I experienced the same issue with gnome 3.7, I upgraded using the testing PPAs hoping it would go away but it didn't.

Thanks!

---

### Post by mc4man on 2013-03-29
> **zika said:**
> Pleasant surprise: I've booted now, back from work, and it is black as it should be, in GDM... No need for tinkering... I did not have time to look what upgrades were done in the meantime...
Update&#8321;: Awakening from stand-by still doesn't work if I am in GDM/LightDM... In startx/xinit it does...
(yeah - meant toggle the show-desktop-icons, guess I truncated that comment a bit.

figure this will get squared away at some point, don't really know if it's a gnome classic bug or gnome classic from ppa on Ubuntu bug, nothing else around atm to compare.
Seems like it ignores that or any?? gsetting on login & uses some 'default' setting(s), though that doesn't explain why it usually resets once after 10 secs or so, then is fine (haven't yet found anything  running around that 10 sec mark...

(on a fresh boot do get the proper background for about a sec or 2, then it goes to Desktop, so it seems to be something at login or so.

---

### Post by Roasted on 2013-03-29
> **VinDSL said:**
> Which screencast software are you using?

I haven't found one that's worth a Tinker's *you_know_what*!  ](*,)

That vid came out nice!

I used Kazam in that video. It works decent. Haven't really had any problems with it.

---

### Post by VinDSL on 2013-03-30
> **Roasted said:**
> I used Kazam in that video. It works decent. Haven't really had any problems with it.
Thanks!  I'll give it a whirl...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-30-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-mar-2013-1.png")[/INDENT]

* Gnome-Shell 3.8.0.1

---

### Post by VinDSL on 2013-03-30
~Cool!  Works!

Unity on GS 3.8:  [http://youtu.be/L8pULM87DgA](http://youtu.be/L8pULM87DgA)  LoL!  :D

Okay, back on topic...

---

### Post by Rukiri on 2013-03-30
Has anyone gave classic mode a whirl?

---

### Post by VinDSL on 2013-03-30
> **Rukiri said:**
> Has anyone gave classic mode a whirl?
WoW!  Classic mode works!

And, an even bigger surprise... I walked away, while it was booting, and came back to find the screensaver had activated.

For the past few weeks, I couldn't escape screen blanking.  Now, it wakes_up just fine!

Everything looks pretty good.  Guess I'll play around in "Classic" for a while...

---

### Post by VinDSL on 2013-03-30
Been playing with Gnome Classic for 4 hours.

Only problem I've discovered is with gnome-clocks.

Gnome-clocks worked for a while, then quit...

```
vindsl@Zuul:~$ gnome-clocks
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gnomeclocks/app.py", line 401, in do_activate
    self.win = Window(self)
  File "/usr/lib/python2.7/dist-packages/gnomeclocks/app.py", line 58, in __init__
    self.world = World()
  File "/usr/lib/python2.7/dist-packages/gnomeclocks/world.py", line 331, in __init__
    self.load_clocks()
  File "/usr/lib/python2.7/dist-packages/gnomeclocks/world.py", line 389, in load_clocks
    self.clocks = self.storage.load()
  File "/usr/lib/python2.7/dist-packages/gnomeclocks/world.py", line 53, in load
    location = GWeather.Location.find_by_station_code(gweather_world, l)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 113, in function
    return info.invoke(*args, **kwargs)
TypeError: Argument 1 does not allow None as a value
```

I'll try 'clocks' again, when I log into GS.  ;)

---

### Post by Rukiri on 2013-03-31
I'd update with apt-get update than download gnome-clocks, I can't confirm the error though.  
Is the new note taking app available or was it a preview for 3.10?

Curious, I know you can pin apps to the gnome-panel?  Wish there was a way to not display the opened app on the top panel, isn't that what the bottom panel is for? I'd remove the bottom panel anyway and add a dock but that's my pref mainly considering I've been using Mac since 90s (mac classic allowed you to pin apps to the bottom like a task bar, don't remember if it was a dock or taskbar as I haven't ran os 9 since 2001 when OS X was released).

---

### Post by VinDSL on 2013-03-31
> **Rukiri said:**
> Wish there was a way to not display the opened app on the top panel, isn't that what the bottom panel is for?
True!

At least they finally added a "Clear Messages" function to 'Notifications'.

Heh!  My weather app updates every 15 minutes, and adds yet_another notification to that panel.

"Clear Messages" will save me a LOT of time/clicking...

---

### Post by Harry33 on 2013-04-05
The Gnome3 PPA starts to look good now with lots of gnome 3.8 updates available.
It is not complete yet, however.
We still need packages (v. 3.8.0) like evince, file-roller, gedit, gnome-online-accounts, gnome-themes-standard and GTK+3.

---

### Post by Stinger on 2013-04-05
Sorry wrong thread :oops:

---

### Post by zika on 2013-04-06
> **AntoineT said:**
> I have the same problem (raring+gnome-team/gnome3 PPA) with the scrollbars in nautilus, gedit, evince etc.
Did you by any chance manage to solve the issue?
I thought it was (re)solved but... I just fired up Nautilus to see that control over scroll bar vanishes after first use...
So, at my place it still is not solved...

---

### Post by VinDSL on 2013-04-06
> **zika said:**
> I thought it was (re)solved but... I just fired up Nautilus to see that **[COLOR="#A52A2A"]control over scroll bar vanishes[/COLOR]** after first use...
So, at my place it still is not solved...
Same here...

You know, this no_scroll_bar_control situation (in certain apps) has been going on for so long, I cannot even remember when it started.

I *don't think* I've ever mentioned it in the threads, because I normally use the mouse_wheel to scroll vertically. Chromium web browser is thankfully impervious to this problem, thus no harm, no foul when surfing the web, blogging, et cetera.

However, the mouse_wheel doesn't do jack horizontally, which (for instance) makes hacking code a nightmare. Instead, I need to edit long lines of code using the home/end/spacebar buttons & arrow keys on the keyboard, which is a major PITA.

Sometimes, the only way I can hack a long line of code in gedit is to insert linefeeds into the code (e.g. convert a single horizontal line of code into 20-30 vertical lines), make the changes, then remove the linefeeds when I'm done.  Sheesh!

Anyway, rant over.  :D

I wish some dev(s) would take note of this situation and fix it...

---

### Post by zika on 2013-04-06
> **VinDSL said:**
> Same here...

You know, this no_scroll_bar_control situation has been going on for so long, I cannot even remember when it started.

I *don't think* I've ever mentioned it in the threads, because I normally use the mouse_wheel to scroll vertically.

However, the mouse_wheel doesn't do jack horizontally, which makes hacking code a nightmare. Instead, I need to edit long lines of code using the home/end/spacebar buttons & arrow keys on the keyboard, which is a major PITA.

Sometimes, the only way I can hack a long line of code in gedit is to insert linefeeds into the code (so I can scroll it vertically, instead of horizontally), make the changes, then remove the linefeeds when I'm done.  Sheesh!

Anyway, rant over.  :D

I wish some dev(s) would take note of this situation and fix it...I've noticed it when my son brought me (I've been wanting that for very long time) trackball mouse from USA, but I've ordered one without scroll-wheel, fearing about compatibility... Silly old fool... I've found way to get it back (for one try, again) in Nautilus: switch display mode (list->thumb etc.)... Silly but it works for me... ;)

---

