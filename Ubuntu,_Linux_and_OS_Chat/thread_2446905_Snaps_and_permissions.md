---
title: "Snaps and permissions"
date: 2020-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by jerome1232 on 2020-07-08
I see a lot of snap hate floating around... 

But I actually love the simplicity of installing them, just if it weren't for those pesky permissions that don't seem to be implemented yet. I've had emacs crash and burn when adding spacemacs to it due to snap permissions. Other apps can't do their primary function because snaps haven't implemented x permission yet and more. When they work, they work beautifully, but I've been burnt more times than saved so far.

I don't know what to think of the emerging landscape, I do like the idea's of flatpack and snap, libraries can be such a pain as software ages. What I don't understand is why there is so much snap hate floating around, what's so great about flatpacks vs snaps that snaps get a cold shoulder?

---

### Post by wildmanne39 on 2020-07-08
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by TheFu on 2020-07-08
if your HOME directories use NFS, snaps don't work at all. Period.  inside a business using NFS for HOME directories is THE standard method.

Now suppose you work with a team of people and keep that data on NFS storage that is part of a 5 program workflow and cannot change where the mounts are located to meet the mandatory snap "approved" places.  Any snap packaged programs that need to access that data cannot.

Not so much hate as frustration.  Flatpaks have faults.  There are a few ways that people who want apps to run under constraints can set that up themselves, but with local controls.

Canonical has this thing about defaults and they aren't wrong, but when that breaks business workflows without any attempt to provide the ability for workarounds, people get frustrated.  LXD is only provided as a snap.  That's a problem.

---

### Post by monkeybrain20122 on 2020-07-08
> **jerome1232 said:**
> 

I don't know what to think of the emerging landscape, I do like the idea's of flatpack and snap, libraries can be such a pain as software ages. What I don't understand is why there is so much snap hate floating around, what's so great about flatpacks vs snaps that snaps get a cold shoulder?

I have tried both and my vote goes to flatpak. It is just as easy to install as snap with Ubuntu20.04 and up since gnome software now has flatpak plugin which works quite seamlessly (it existed in 18.04 but kind of awkward) If you use KDE discover (their app store) also has seamless integration with flatpak (and snap) Unlike snap, flatpak doesn't mount a whole bunch of volumes at start, in some systems it may drastically increase boot time. They might have fixed it in 20.04, I had a few snap packages installed but bootup was still lightning fast, in 18.04 on same machine the boot time almost doubleD with less snap packages (just the ones installed by default), but this may also depends on hardware so others may have different experience. 

Managing permission is very easy for flatpak with an app called flatseal, it is an unified gui to manage permission for different flatpak packages (or you can use command line of course), I don't think there is anything in snap to allow user to control permission and access.

But all these sandboxed apps have problems with integrating with external plugins, e.g gimp installed with snap or flatpak cannot find the darktable plugin even if darktable is installed (via apt).

---

### Post by &amp;KyT$0P# on 2020-07-09
> **jerome1232 said:**
> What I don't understand is why there is so much snap hate floating around, 

For one, because snapd [intentionally offers no way to completely disable automatic updates.]("https://forum.snapcraft.io/t/disabling-automatic-refresh-for-snap-from-store/707")  This gets seen as anti-user.  It spits in the face of many people's valid, solid stability and security models.

Separately, it appears that Ubuntu/Canonical is trying to 'push' snaps more and more.  They have already gone so far as to replace some deb packages with snaps (e.g. Chromium).

That combination drives some of the negative sentiment toward snap you're seeing 'floating around'.

---

### Post by mastablasta on 2020-07-09
heh, wasn't the snap supposed to be the solution to have old software installed along with new one?

---

### Post by TheFu on 2020-07-09
> **mastablasta said:**
> heh, wasn't the snap supposed to be the solution to have old software installed along with new one?

That was 1 purpose, but on my 16.04 systems, only about 20% of snaps actually work. The packagers don't include all the dependencies from core libraries that 18.04 and 20.04 include. That lack for libraries leads to failure at run time.

---

### Post by Dennis N on 2020-07-09
I've focused on using Snap or Flatpak packages in the LTS release to keep the major applications I frequently use up to date; for example: Gimp, Inkscape, Libre Office. Personally, I don't have any reason to avoid automatic updates. Many (most?) Flatpak applications also are updating automatically if you use Ubuntu 20.04 and Software (they didn't previously). 

Snap file-access permissions can be controlled to a limited extent from Software (gnome-software), or if you don't have Software installed, it can be done from the terminal.  

Due to the regular updates we normally get, there may not be much incentive to use a Firefox Snap. But I'll note that Firefox ESR release has a Snap version that works well if you're interested. I've been using it part of the time. There is no Flatpak Firefox ESR (yet). 

As mentioned previously, Flatseal is a nice tool to manage Flatpak permissions.

---

### Post by jerome1232 on 2020-07-09
It sounds like I'd like flatpacks, I'll have to give it an install and try some out.

---

### Post by mastablasta on 2020-07-10
> **TheFu said:**
> That was 1 purpose, but on my 16.04 systems, only about 20% of snaps actually work. The packagers don't include all the dependencies from core libraries that 18.04 and 20.04 include. That lack for libraries leads to failure at run time.

Canonical or community should put "pressure" on packagers then. I mean this kind of defeats the purpose With accurately maintained snaps, one should easily be able to install say old games or other applications. just like in windows where you can (with compatibility) load old apps and games from end of 90's.

---

### Post by TheFu on 2020-07-10
I've been a developer.  You would get what you got from my volunteer time. Nagging for things I considered unimportant would be ignored, since I had work, family, and personal goals which almost always came before the F/LOSS project. The F/LOSS stuff I worked on was directly related to my day job programming. The main developer had little interest in making the way config files worked follow the normal Unix hierarchy, so I wrote all the code to make that happen and submitted it.  In order:
[LIST=1]
[*]Command line entries
[*]Environment variables
[*]HOME directory settings
[*]System directory settings
[/LIST]
So any command line entry took priority over the others.  It was an itch that I had and our clients had, so I scratched it. Hardly difficult code, but much better than reading just 1 file in /etc/ ... for a program that would never run as root on multi-user systems.

Wish snaps would follow that priority for local configuration and not have only the packager in control of snap settings.

On Unix systems, the user is KING.  The current snap design has forgotten that.  IMHO.

---

