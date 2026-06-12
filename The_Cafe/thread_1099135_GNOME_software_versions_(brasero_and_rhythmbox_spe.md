---
title: "GNOME software versions (brasero and rhythmbox specifically)"
date: 2009-03-17
forum: The Cafe
---

### Post by altonbr on 2009-03-17
I noticed that Brasero is now 2.26.0 in Jaunty but Rhythmbox is still 0.11 (or soon to be 0.12). Why is it that a program that has been in GNOME for as long as Rhythmbox is still not using GNOME's versioning number (2.26 in this case)?

Are they missing some sort of functionality that GNOME requires? Are the numbers really just arbitrary? Does anyone have information on this?

---

### Post by 23meg on 2009-03-17
[QUOTE=altonbr]Why is it that a program that has been in GNOME for as long as Rhythmbox is still not using GNOME's versioning number (2.26 in this case)?[/QUOTE]

Rhythmbox isn't part of GNOME.

The [GNOME Module Requirements]("http://live.gnome.org/ReleasePlanning/ModuleRequirements") state the following regarding version numbers for GNOME module releases:

> Please either (a) at least use GNOME's minor version number (e.g. 1.17.6 for a GNOME 2.17.x release) or (b) prominently specify in either your changelog or README which version of GNOME you are targetting with each release of your software.

---

### Post by altonbr on 2009-03-19
> **23meg said:**
> Rhythmbox isn't part of GNOME.

The [GNOME Module Requirements]("http://live.gnome.org/ReleasePlanning/ModuleRequirements") state the following regarding version numbers for GNOME module releases:

But see, that's what confuses me; Why is Rhythmbox under GNOME's homepage? Rhythmbox has no other website but that site and it's even using GNOME's SVN.

[http://projects.gnome.org/rhythmbox/](http://projects.gnome.org/rhythmbox/)

So it's almost like Banshee is as much a part of GNOME as Rhythmbox is because it "works well under GNOME" except for that fact that is uses Mono/C#.

I'll hop on IRC to see what GNOME's plan is for a music player.

Thanks for the info!

---

### Post by deepclutch on 2009-03-19
there are quiet a few software which are kind of part of gnome(annexed).

---

### Post by 23meg on 2009-03-19
> **altonbr]But see, that's what confuses me said:**
> 

GNOME provides web space, bug tracker and VCS hosting to some GNOME-related projects. This may lead to the false assumption that these projects are official parts of the various GNOME release sets, but that's not the case. From [http://projects.gnome.org/](http://projects.gnome.org/) , the parent URL:

> This page is a listing of GNOME-related projects and their related web pages. 

Many other projects which aren't part of GNOME live in projects.gnome.org, GNOME Bugzilla and GNOME SVN. 

> **altonbr]So it's almost like Banshee is as much a part of GNOME as Rhythmbox

I would omit the "It's almost like" said:**
> I'll hop on IRC to see what GNOME's plan is for a music player.

GNOME's official media player is Totem, and it plays audio files. I don't think there are any plans at hand for changing that.

[QUOTE=altonbr]Thanks for the info![/QUOTE]

You're welcome.

---

