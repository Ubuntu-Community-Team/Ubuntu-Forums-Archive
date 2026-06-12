---
title: "Parole Media PLayer"
date: 2009-11-15
forum: The Cafe
---

### Post by Praxicoide on 2009-11-15
This is an Xfce media player available in the Xfce Goodies project:

[http://goodies.xfce.org/projects/applications/parole](http://goodies.xfce.org/projects/applications/parole)

Has anyone tried this yet? I'm curious, but it's not in the repositories and I would like an opinion before compiling it.

---

### Post by K.Mandla on 2009-11-15
> **Praxicoide said:**
> This is an Xfce media player available in the Xfce Goodies project:

[http://goodies.xfce.org/projects/applications/parole](http://goodies.xfce.org/projects/applications/parole)

Has anyone tried this yet? I'm curious, but it's not in the repositories and I would like an opinion before compiling it.
I've not tried it, but I've had good luck with other applications in the goodies list.

---

### Post by picpak on 2009-11-15
Looks like Xfce's answer to Totem. Could be good.

---

### Post by RiceMonster on 2009-11-15
It's really nothing special. If you want something with bare bones functionality (ie just opening and playing files) I guess it'll suite you.

---

### Post by Praxicoide on 2009-11-15
> I've not tried it, but I've had good luck with other applications in the goodies list.

So have I. Midori takes the cake, but the other apps and tools there are very nice.

> It's really nothing special. If you want something with bare bones functionality (ie just opening and playing files) I guess it'll suite you.

It has a browser plugin.

> Looks like Xfce's answer to Totem. Could be good.

I hope so.

I guess I'll give it a shot.

---

### Post by Praxicoide on 2009-11-15
Some help here would be appreciated:

I cloned the repository with git, moved into the directory and then
I put:
./autogen.sh --prefix=/usr

and I got:
xdt-autogen: Directory "~/parole" does not look like a package
             directory, neither configure.ac nor configure.in is present.

The directory has a configure.ac.in file. So, should I rename it or what should I do?

EDIT: I renamed it, and I'm bumping into a bunch of dependencies that I'm slowly working through. I'll keep you posted.

---

### Post by Praxicoide on 2009-11-16
I managed to get through the configuration, even if it was with no notification (at least the browser plugin was enabled), but ran into an error when making.

"Entering directory ~/parole/po
No rule to build objective `@LINGUAS@.gmo' necessary for all=yes"

I have no clue about this. I guess this is the end of the line for me. :(

EDIT: Mon dieu! I installed I don't know how many dev packages for nothing. [Le bazar de Stemp](http://stemp.wordpress.com/) has a .deb.

I just installed it, but I don't see the browser plugin. Maybe that has to be built.

---

### Post by Stemp on 2009-11-16
> **Praxicoide said:**
> EDIT: Mon dieu! I installed I don't know how many dev packages for nothing. [Le bazar de Stemp](http://stemp.wordpress.com/) has a .deb.

I just installed it, but I don't see the browser plugin. Maybe that has to be built.

This plugin is only available in git, the 0.1.91 version doesn't have it.
You'll have to wait for 0.1.92 ;)

---

### Post by coldReactive on 2009-11-16
Does this have a repeat function, also, when opening files, does it replace the entire playlist with the opened file and then immediately start playing the file?

If so, I've found a new favorite media player for when I switch to xfce.

---

### Post by Simian Man on 2009-11-16
It's in the Fedora 12 repos.  I have been using it for a while and it's nice.  I've not found it to be any better or worse than Totem, though it does have a few more features.  It does of course have a repeat function.  I don't know about the other one because I haven't tried it and am not on my computer where I have any videos to try it out on.

---

### Post by Praxicoide on 2009-11-16
> **Stemp said:**
> This plugin is only available in git, the 0.1.91 version doesn't have it.
You'll have to wait for 0.1.92 ;)

Thenk you very much for the .deb, and the other xfce stuff in general.

I don't suppose you know why I couldn't build this package?

---

### Post by Stemp on 2009-11-16
> **Praxicoide said:**
> I don't suppose you know why I couldn't build this package?

I created a git version package, in [My PPA]("https://edge.launchpad.net/~stemp/+archive/ppa/+packages") (don't add it, just pick the package). But anyway the browser plugin is crashing for me ;)

---

### Post by Praxicoide on 2009-11-16
You're awesome! I'll let you know how it goes after work.

Merci beaucoup.

---

### Post by pwnst*r on 2009-11-16
> **coldReactive said:**
> Does this have a repeat function, 

pretty sad if you have to ask that.

---

### Post by coldReactive on 2009-11-16
> **pwnst*r said:**
> pretty sad if you have to ask that.

Yeah, I repeat tracks over and over, and I hate playlists.

---

### Post by Simian Man on 2009-11-16
> **coldReactive said:**
> Yeah, I repeat tracks over and over, and I hate playlists.

I think he meant it's such an obvious and easy feature to implement, why would anybody not have it.

---

### Post by Praxicoide on 2009-11-16
Moving on...

I downloaded and installed the latest build, and now Midori is marking the plugin. I'm testing the media from [this site](http://home.att.net/~cherokee67/mediatests.html).Everything crashes, with the terminal states it's a segmentation fault. Oddly, the audios played without problem.

Someone should check with a different browser. This is a very old machine, and I don't want to install Firefox on it.

The player itself seems niche, though.

---

### Post by pwnst*r on 2009-11-16
> **chris4585 said:**
> You could be less of a douche.

i was talking about the software.  care more.

---

### Post by pwnst*r on 2009-11-16
> **Simian Man said:**
> I think he meant it's such an obvious and easy feature to implement, why would anybody not have it.

ding ding

---

### Post by misfitpierce on 2009-11-16
Back to jail with that one... Parole Denied - Haha! Just messing it looks alright but it looks just like totem basically for xfce which is good I guess.

---

### Post by coldReactive on 2009-11-16
Shiznat, opening a file adds it to the playlist, rather than replacing the playlist. Repeat is repeat the entire playlist and not one track.

Looks like I'll be sticking with totem! Unless this bug gets approved: [http://bugzilla.xfce.org/show_bug.cgi?id=5990](http://bugzilla.xfce.org/show_bug.cgi?id=5990)

---

### Post by Psumi on 2009-11-19
> **coldReactive said:**
> Looks like I'll be sticking with totem! Unless this bug gets approved: [http://bugzilla.xfce.org/show_bug.cgi?id=5990](http://bugzilla.xfce.org/show_bug.cgi?id=5990)

Seems to me, your prayers have been answered.

---

### Post by Psumi on 2009-11-19
> **Stemp said:**
> I created a git version package, in [My PPA]("https://edge.launchpad.net/~stemp/+archive/ppa/+packages") (don't add it, just pick the package). But anyway the browser plugin is crashing for me ;)

There was a problem with the git build, it wouldn't compile, can you force your PPA to compile using a new git?

---

### Post by Stemp on 2009-11-19
> **Psumi said:**
> There was a problem with the git build, it wouldn't compile, can you force your PPA to compile using a new git?

Nope I can't the actual git is broken.

```
make[4]: *** No rule to make target `gstmarshal.c', needed by `libparolegst_la-gstmarshal.lo'.  Stop.
```

We will have to wait, but the 0.1.91 version is still in my [Xfce PPA]("https://launchpad.net/~stemp/+archive/xfce") ;)

---

### Post by Psumi on 2009-11-19
> **Stemp said:**
> Nope I can't the actual git is broken.

```
make[4]: *** No rule to make target `gstmarshal.c', needed by `libparolegst_la-gstmarshal.lo'.  Stop.
```

We will have to wait, but the 0.1.91 version is still in my [Xfce PPA]("https://launchpad.net/~stemp/+archive/xfce") ;)

Have you filed a bug under parole at the XFCE Bugzilla?

[http://bugzilla.xfce.org](http://bugzilla.xfce.org)

---

### Post by Stemp on 2009-11-25
Version 0.1.95 is ready in my [Xfce PPA]("https://launchpad.net/~stemp/+archive/xfce")

---

### Post by Praxicoide on 2009-11-25
Great news. I'll test it this evening.

Thank you very much.

---

### Post by Praxicoide on 2009-11-26
I'm testing the plugin now on Midori and it doesn't crash anymore. The audio and video play just fine.

Once again, thank you very much!

---

### Post by Stemp on 2009-11-26
> **Praxicoide said:**
> I'm testing the plugin now on Midori and it doesn't crash anymore. The audio and video play just fine.

Once again, thank you very much!

Embedded WMV Video files doesn't work for me.
I'm testing from [http://home.att.net/~cherokee67/mediatests.html](http://home.att.net/~cherokee67/mediatests.html)

---

### Post by ASriazh on 2009-11-26
> **Praxicoide said:**
> This is an Xfce media player available in the Xfce Goodies project:

[http://goodies.xfce.org/projects/applications/parole](http://goodies.xfce.org/projects/applications/parole)

Has anyone tried this yet? I'm curious, but it's not in the repositories and I would like an opinion before compiling it.

It's not a bug really. youre just missing the XFCE4 dev tools from here

git://git.xfce.org/xfce/xfce4-dev-tools

-Asriazh

---

### Post by Exodist on 2009-11-26
Looks nice. Almost like a remix of totem.

---

### Post by Stemp on 2010-01-05
Parole 0.2.0 is ready.
[http://releases.xfce.org/feeds/project/parole](http://releases.xfce.org/feeds/project/parole)
[PPA]("https://edge.launchpad.net/~stemp/+archive/xfce/+packages")

Release notes for 0.2.0
=======================

I'm very happy to announce the first stable release of parole.

* Use g_key_file_get_locale_string to load plugin name and description.
* Fix unused Gst overlay expose on READY state.
* Provide a command line to be used to enable/disable xv, X Video
support might be missing for some drivers.
* Set the _NET_WM_WINDOW_OPACITY_LOCKED wm hint, so xfwm4 keep us
opaque.
* Provide an option to Enable/Disable resetting X screen saver counter
while playing movies
* Check for stream type before settings the live bit.
* Don't popup errors in the browser plugin.
* Fix seek backwards+add mouse wheel on the volume slider, patches by
Enrico Troger.

---

### Post by Psumi on 2010-01-30
hey Stemp. Your application may make it into Lucid+1.

[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/504341](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/504341)

---

### Post by Stemp on 2010-01-30
> **Psumi said:**
> hey Stemp. Your application may make it into Lucid+1.

Great ! But it's not my applications (the dev is Ali Abdallah), I only created the package. And anyway this package is still waiting in Revu, but I'm pretty sure someone from Debian will recreate it and bring it to unstable.

---

### Post by Psumi on 2010-01-30
> **Stemp said:**
> Great ! But it's not my applications (the dev is Ali Abdallah), I only created the package. And anyway this package is still waiting in Revu, but I'm pretty sure someone from Debian will recreate it and bring it to unstable.

Debian has SLiM but ubuntu karmic doesn't... so... sometimes what Debian has doesn't go into ubuntu.

---

### Post by Psumi on 2010-04-08
Do you have a debian package? Debian packaging isn't the same as ubuntu.

---

