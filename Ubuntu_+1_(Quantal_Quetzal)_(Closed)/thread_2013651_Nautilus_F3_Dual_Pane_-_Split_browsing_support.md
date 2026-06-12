---
title: "Nautilus F3 Dual Pane - Split browsing support"
date: 2012-07-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by glococo on 2012-07-01
Hi,

[-X
I saw that gnome drop this awesome feature.I dont know if were it possible to turn it on back, but please, it make nautilus usless for me.

Switching back to gnome-commander, which btw, is full of bugs.

PS: I'm switching back to /gnome-classic/, _UNITY_ is becoming a great block of concrete to any modern 1GB computer.

PS2: Even with compiz, gnome-classic run much efficient.

---

### Post by cmcanulty on 2012-07-01
+1

---

### Post by VinDSL on 2012-07-01
> **glococo said:**
> I saw that gnome drop this awesome feature.I dont know if were it possible to turn it on back, but please, it make nautilus usless for me.
If I remember correctly, split-screen didn't work properly with touchscreens, so they threw it out.

You could probably hack it up, or downgrade to an older version and get it back, but I doubt it's coming back (any time soon) in future releases.  

I dearly miss it too, but tabbed-windows are working well for me, so I'm sticking with Nautilus.  ;)

> **glococo said:**
> PS: I'm switching back to /gnome-classic/, _UNITY_ is becoming a great block of concrete to any modern 1GB computer.
Unity is a mess.  The biggest problem, for me, is I cannot choose anything in drop-down menus.  I just get a quivering pointer.

I check Unity after every update/upgrade, but the problem persists.  In the meantime, I'm just running LXDE/Openbox on top of Ubu 12.10 for production work.  

Actually, I think LXDE is a keeper.  I'll probably continue to have it available, even after Unity becomes stable.

---

### Post by jbicha on 2012-07-01
A workaround for dual-pane mode is to open two Nautilus windows and snap one to the left and one to the right.

---

### Post by VinDSL on 2012-07-01
> **jbicha said:**
> A workaround for dual-pane mode is to open two Nautilus windows and snap one to the left and one to the right.
Good idea!

I've been opening a new tab and doing a cut n' paste.

Heh!  Old habits die hard.  :D

---

### Post by mc4man on 2012-07-01
> **VinDSL said:**
> 

Unity is a mess.  The biggest problem, for me, is I cannot choose anything in drop-down menus.  I just get a quivering pointer.

I check Unity after every update/upgrade, but the problem persists.  
That should have been fixed as noted here in comment 10 (bug title is somewhat misleading, all gtk3 combo boxes were affected

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497)

But then again you never know - currently here 12.10 is completely unusable with nautilus on my hardware, nautilus crashes constantly
So myself will be dropping 12.10 very shortly, don't see the bug being fixed unless, in order of most likely

Inadvertently
Considerably more are affected, only 4 users reported so far
A gnome/nautilus dev has similar hardware, gets affected & decides to then show interest & fix

(For occasional 2 pane stuff I used to use Sunflower, but it broke last week in 12.10 with a python-2.7 segfault

---

### Post by EgoGratis on 2012-07-01
Removing features like dual pane is pure abuse of users and with GNOME 3 this became some kind of contest who will do the most stupid thing and i was tolerant in the past and a lot of things made sense but lately it's just a big pile of mess.

KDE became unstable mess after 4.
GNOME became unusable mess after 3.

---

### Post by VinDSL on 2012-07-01
> **mc4man said:**
> That should have been fixed as noted here in comment 10 (bug title is somewhat misleading, all gtk3 combo boxes were affected

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497)
Thanks for the link!  I read it, and worked on Unity for a few hours.

It's functioning now... nowhere near my satisfaction... but, it's working.

Here's a "dirty" screenie showing usable GTK3 pull-downs, et cetera...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-jul-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-jul-2012-3.png")[/INDENT]


BTW, Nautilus is working fine for me.  Only janky app is Inkscape, so far.  The extensions aren't playing nice.

Pretty obvious that the GTK3 themes are going to require some tweaking in UbuQQ  ;)

---

### Post by mc4man on 2012-07-01
> **VinDSL said:**
> 

BTW, Nautilus is working fine for me.  Only janky app is Inkscape, so far.    ;)
Inkscape broke here on extensions in 12.04 & even though it was fixed quite some time ago it has never made it into 12.04 or 12.10
(disappointing - don't really quite care at this point   whose  fault 

bug on - 
[https://bugs.launchpad.net/ubuntu/+source/inkscape/+bug/944077](https://bugs.launchpad.net/ubuntu/+source/inkscape/+bug/944077)

What you can do is use a ppa that has inkscape 0.48.4 or higher or even the  trunk ppa (at your own risk, blah, blah
[https://launchpad.net/~inkscape.dev/+archive/trunk](https://launchpad.net/~inkscape.dev/+archive/trunk)

The bug report has a workaround though is a bit of a pita, should just be upgraded in 12.10 & 12.04 to a fixed version

(the nautilus deal here must be hardware, (Dell 1330m), related to some unfortunate gtk3 code, don't have high hopes...
To bad my OLD p4 gamer finally died this winter, would have be serviceable at the least in 12.10

---

### Post by VinDSL on 2012-07-01
> **mc4man said:**
> What you can do is use a ppa that has inkscape 0.48.4 or higher or even the  trunk ppa (at your own risk, blah, blah
[https://launchpad.net/~inkscape.dev/+archive/trunk](https://launchpad.net/~inkscape.dev/+archive/trunk)
Heh!  Thanks, again!

Dev trunk worked a treat.  I've been trying to make a Guayadeque svg for my ACYL icon set.  

Extensions worked great!  :)

---

### Post by mc4man on 2012-07-02
> **VinDSL said:**
> 

Dev trunk worked a treat.   :)
Works well here too. What I do with such ppa's is if a package/package set works well then I'll copy out from /var/cache/apt/archives to somewhere else just in case any of the various 'whatever's' occurs

---

### Post by VinDSL on 2012-07-02
> **mc4man said:**
> What I do with such ppa's is if a package/package set works well then I'll copy out from /var/cache/apt/archives to somewhere else [...]
Heh!  I wonder if it would be "kosher" to store it here?!?!?

VinDSL Testing PPA: [https://launchpad.net/~perfect-pecker/+archive/testing](https://launchpad.net/~perfect-pecker/+archive/testing)

I'm like a kid with a new toy...  :)


**EDIT**


N/M

SOURCE: [https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)
> Note: **[COLOR="DarkRed"]We will not accept uploads of packages that are unmodified from their original source in Ubuntu or Debian, only packages that include your own changes[/COLOR]**. We ask that people include useful changelogs for each package so that users and other developers can understand what new features they are exploring in their work. Read the PPA Terms of Use for more information.

I guess this is where the "trust" issue comes into play.

I'd better stick to Conky Script uploads, for now, with an eye toward releasing Vinbuntu. LoL!  :D

[COLOR="DimGray"][SIZE="3"]Baby steps...[/SIZE] [SIZE="2"]baby steps...[/SIZE] [SIZE="1"]baby steps...[/SIZE][/COLOR]

---

### Post by sgage on 2012-07-02
> **VinDSL said:**
> If I remember correctly, split-screen didn't work properly with touchscreens, so they threw it out.

This one-size-fits-all madness has got to stop. If a very useful feature (I use it extensively) doesn't work properly on a touchscreen, either fix the damn thing, or disable it ON TOUCHSCREENS. Don't throw the baby out with the bathwater!

The whole Unity thing is bad enough (I use Gnome Shell, which, with extensions is quite usable). I remember when Unity first came out and people were complaining about shoe-horning a touchscreen interface onto the desktop, that Shuttleworth himself insisted that Unity wasn't designed for touchscreens. What a crock!

I've just about had it with Ubuntu...

---

### Post by Yahoé on 2012-07-02
F3 dual pane was a very efficient and quick feature that should be reactivated, tabs or dual windows just don't cut it.

---

### Post by EgoGratis on 2012-07-02
> The whole Unity thing is bad enough (I use Gnome Shell, which, with extensions is quite usable).

I don't agree on this one. 

GnomeShell is unusable for majority of users and probably you are more advanced user that knows how to use extensions for it and still you could not achieve the desktop you would like?

One word: fail?

Majority of users will NEVER say look it has extensions too let's see if we can make it usable it has to be usable by default if you want to attract users?

Unity still gives you desktop love it/hate it it does not make much difference user starts Ubuntu and at least it works and it has usable desktop? Sure it has launcher on the left side and user could just simply not like that fact  but everything else just works and user can start working?

GNOME 3 assumed desktop is not needed any more and bit by bit desktop features are removed and this is wrong. Launcher tool was removed quite some time back and still users need it decision to remove it was just plain wrong? The same will happen with dual pane mode it will be removed but the users still need it and will not get anything useful in return the result is and it will be the DE that lacks in many areas and nothing else!

And to be honest i see a lot of things that would need work to improve touch support and if somebody is really honest in intentions to fix it and not just searching for excuse to remove something i recommend he/she takes a better look at the priorities.

---

### Post by sgage on 2012-07-02
> **EgoGratis said:**
> I don't agree on this one. 

GnomeShell is unusable for majority of users and probably you are more advanced user that knows how to use extensions for it and still you could not achieve the desktop you would like?

One word: fail?.

Well, I don't agree with you on this one. I don't see how Unity is easier than GS - in fact, it's Gnome Shell tweaked to be a little more inconvenient and a lot less configurable.

Everyone has their own workflow - Gnome Shell is a lot more adaptable to mine than Unity is. I've tried to get into the Unity mindset, and it simply doesn't work for me.

To each, their own.

---

### Post by EgoGratis on 2012-07-02
> Well, I don't agree with you on this one. I don't see how Unity is  easier than GS - in fact, it's Gnome Shell tweaked to be a little more  inconvenient and a lot less configurable.

Everyone has their own workflow - Gnome Shell is a lot more adaptable to  mine than Unity is. I've tried to get into the Unity mindset, and it  simply doesn't work for me.

To each, their own.

I don't see much difference in workflow GNOME 2 offered compared to Unity. The main difference is launcher is on the left side and that's about it! Everything else pretty much works the same way Unity just offers more advanced integration.

The thing i miss the most (beside removing of Dodge Windows feature) are the things GNOME 3 removed for desktop usage.

---

### Post by sgage on 2012-07-02
> **EgoGratis said:**
> I don't see much difference in workflow GNOME 2 offered compared to Unity. The main difference is launcher is on the left side and that's about it! Everything else pretty much works the same way Unity just offers more advanced integration

Well, if you don't see the difference, there must not be one :KS

I guess we'll just have to agree to disagree, and be glad we have some choices...

---

### Post by EgoGratis on 2012-07-02
> I guess we'll just have to agree to disagree, and be glad we have some choices...

Yes we have some messy unusable choices and that is at least something yes. I agree.

---

### Post by sgage on 2012-07-02
> **EgoGratis said:**
> Yes we have some messy unusable choices and that is at least something yes. I agree.

Yes, it really is too bad about Unity... :lolflag:

---

### Post by EgoGratis on 2012-07-02
Yes and this is another thing that failed big we have around 1% market share and now we have two "clubs" of users that try to prove Unity or GnomeShell is better/worse to add to the confusion. Who cares we failed and basically i don't see the point in arguing who is in the bigger mess  because the mess is to big.

Dual Panel is being removed and it makes no difference if you use GnomeShell or Unity and if we wold have for example 10% market share maybe then it would make sense if we started the usual "fanboy debates" now it just does not make any big difference it's just a mess.

---

### Post by sgage on 2012-07-02
> **EgoGratis said:**
> Yes and this is another thing that failed big we have around 1% market share and now we have two "clubs" of users that try to prove Unity or GnomeShell is better/worse to add to the confusion. Who cares we failed and basically i don't see the point in arguing who is in the bigger mess  because the mess is to big.

Dual Panel is being removed and it makes no difference if you use GnomeShell or Unity and if we wold have for example 10% market share maybe then it would make sense if we started the usual "fanboy debates" now it just does not make any big difference it's just a mess.

My original point is that it seems to be all part of the rush to touch screen devices and mobile. I have nothing whatsoever against touch screen devices or mobile devices, but trying to make one UI that's best for those devices and for keyboard/mouse devices is a mistake, IMO.

Microsoft is now making the same mistake with Windows 8 and "Metro"...

In any case, I am neither debating nor arguing - one's preference of UI is based on how one works, one's aesthetics, and so on and so forth - not exactly objective, for the most part.

---

### Post by VinDSL on 2012-07-02
> **sgage said:**
> Microsoft is now making the same mistake with Windows 8 and "Metro" [...]
No kidding!  Boy, are they in for a rude awakening...

To make things worse, they mixed "8" & "Metro" together on the same desktop.  Hello!?!?!

At least, with Ubuntu, you can pick n' choose which DE/WM you want to use at login.

I've been customizing Unity since day-one, doing all sorts of things that shouldn't even be possible.  And, a large part of customizing Unity needs to be done in GS.  Soooo, IMO, based on a lot of experimentation is... GS augments Unity, and vice-versa.  Both are needed to succeed in rolling your own desktop.

I've been smitten with LXDE/Openbox lately, and loading it on top of Unity/GS has been quite rewarding.  That's what I'm using, as I type.  

All of this experimenting with LXDE started by using Lubuntu (Ubuntu based), but I found it exasperating because every update would wipe out any inroads that I'd made.  Next, I ran with Peppermint (Lubuntu based).  I'm still running it on my portables, but it left me hungry for more...

Anyway, it will all pan out, eventually.  Hang in there!

Having said that, I *think* the Microsoft "8" client-base is in for a world of hurt!  LoL!  :D

---

