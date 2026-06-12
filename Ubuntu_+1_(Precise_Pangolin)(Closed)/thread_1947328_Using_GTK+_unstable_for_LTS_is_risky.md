---
title: "Using GTK+ unstable for LTS is risky"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-03-26
Why is the LTS being built on unstable GTK (3.3.20 as of today)?  So many moving parts right now is bound to make for a buggy release.

---

### Post by ScislaC on 2012-03-26
Because this is normal for Ubuntu releases. GTK 3.4 should be released real soon now. They do also maintain the packages after release.

---

### Post by jbicha on 2012-03-26
GTK 3.4 was released today and I expect it to go to precise-proposed later today and then moved to the normal precise archives at the end of this week. (The delay is because we're in freeze for Beta 2).

GTK 3.4 is required for GNOME 3.4 which a lot of people want. GNOME 3.4's official release is later this week, which gives a few more weeks for bug fixing even before 12.04 is released.

For what it's worth, there was some debate/questions about how much of GNOME 3.4 we wanted for this cycle, but it turns out we're getting nearly all of it.

---

### Post by dino99 on 2012-03-26
final cairo 1.12 is out too, do we get it on Precise too ?

---

### Post by tekstr1der on 2012-03-26
> **jbicha said:**
> For what it's worth, there was some debate/questions about how much of GNOME 3.4 we wanted for this cycle, but it turns out we're getting nearly all of it.

That will be for the better in the long run. Good news!

---

### Post by Harry33 on 2012-03-26
GTK 3.4.0-0ubuntu1 is being built already for the proposed repo of Precise.

Here:
[https://launchpad.net/ubuntu/precise/+source/gtk+3.0/3.4.0-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/gtk+3.0/3.4.0-0ubuntu1)

And a more thing. There is no Precise LTS yet, only a dev version (beta).

---

### Post by dino99 on 2012-03-26
> **Harry33 said:**
> 
And a more thing. There is no Precise LTS yet, only a dev version (beta).

but Hope makes life easier :)

---

### Post by NHclimber on 2012-03-26
> **jbicha said:**
> GTK 3.4 was released today ...

That's just an API freeze - that doesn't mean the code is stable.

How long before the serious bugs are going to be shaken out of GTK 3.4?
Then, how long before the serious bugs are going to be shaken out of everything that depends on GTK?

Example: Comments on the implications and ramifications of the wip/cssvalue branch merge from 20 days ago!?

> **jbicha said:**
> For what it's worth, there was some debate/questions about how much of GNOME 3.4 we wanted for this cycle, but it turns out we're getting nearly all of it.

Do you remember the too-early-inclusion of PulseAudio?  What a s***storm -- at least that wasn't for an LTS.

What this decision is really going to do is further narrow the definition of what constitutes a 'stable' release to what runs on a dozen machines without crashing.

Seriously -- trying to install 'desktop' Beta 2 on this amd64 development box produced 3 crashing bugs right away.  These *might* be easily fixable except for the 1 bug with the 'Apport retracing service' because it can't do an automated stack backtrace for devs to track down crashing bugs because the debug symbol packages that it uses are outdated relative to the iso (bug# 962470).

The alternate iso hangs after selecting the language -- probably related to one of the 3 crashing bugs mentioned before -- but then again, maybe not.  Won't know because it hangs rather than displaying a message that it died.

In terms of share, a rock-solid installer is worth gtk3.4 + lightdm + unity combined.

---

### Post by 3rdalbum on 2012-03-26
> **NHclimber said:**
> Do you remember the too-early-inclusion of PulseAudio?  What a s***storm -- at least that wasn't for an LTS.

GTK 3.4 is a new "evolutionary" version of software that already exists in the default Ubuntu. Pulseaudio was a new piece of software entirely. GTK 3.x is more mature now than Pulseaudio was at the time.

I don't believe things could get too serious and buggy in a new minor version of a GUI toolkit.

Incidentally, I believe Pulseaudio was introduced in 8.04 LTS.

---

### Post by screaminj3sus on 2012-03-26
I think you are exaggerating a bit. So far 12.04 has been one of the most stable ubuntu testing releases I've ever used. And having most of gnome 3.4 is a good thing. Ubuntu almost always included the newest version of gnome/gtk...

---

### Post by ranch hand on 2012-03-26
Seeing that Ubuntu is based on Gnome3 it will not run on GTK2.  Simple as that.

Having no stability problems in Debian testing or Sid what so ever.

---

### Post by VinDSL on 2012-03-27
> **NHclimber said:**
> Why is the LTS being built on unstable GTK (3.3.20 as of today)?  So many moving parts right now is bound to make for a buggy release.
Stands to reason...  After all, Ubuntu is a Debian Unstable/Testing based release.

It's like grabbing a handful of jelly.  And, strangely, the bugs are a major reason for it's success, IMO.

It certainly brings ppl together, trying to sort the problems... ;)

---

### Post by NHclimber on 2012-03-27
> **VinDSL said:**
> Stands to reason...  After all, Ubuntu is a Debian Unstable/Testing based release.

It's like grabbing a handful of jelly.  And, strangely, the bugs are a major reason for it's success, IMO.

It certainly brings ppl together, trying to sort the problems... ;)

All three are good points -- especially the "brings ppl together".  Very Ubuntu thought, that.

---

### Post by ScislaC on 2012-03-27
> **screaminj3sus said:**
> So far 12.04 has been one of the most stable ubuntu testing releases I've ever used.

Stable? I believe you misspelled "boring and uneventful". ;) Seriously though, definitely one of the most stable dev cycles I can remember.

---

### Post by VinDSL on 2012-03-28
> **ScislaC said:**
> [...] definitely one of the most stable dev cycles I can remember.
The devs are less tempestuous, when it comes to LTS releases...  :)

---

### Post by lucazade on 2012-03-28
Seems a bit unstable for me too.. sometimes the gtk widgets lose their properties like borders and colors.
Look at this screenshot.. the entry/input widget is broken and it is not a issue of unico-engine or light-themes but a gtk bug.

[http://i.imgur.com/xxwMr.png](http://i.imgur.com/xxwMr.png)

[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/966940](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/966940)

---

### Post by Harry33 on 2012-03-28
> **lucazade said:**
> Seems a bit unstable for me too.. sometimes the gtk widgets lose their properties like borders and colors.
Look at this screenshot.. the entry/input widget is broken and it is not a issue of unico-engine or light-themes but a gtk bug.

[http://i.imgur.com/xxwMr.png](http://i.imgur.com/xxwMr.png)

[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/966940](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/966940)

It might also be an issue of a certain theme still being incompatible with the new GTK+3.

---

### Post by lucazade on 2012-03-28
> **Harry33 said:**
> It might also be an issue of a certain theme still being incompatible with the new GTK+3.

it happens with both updated Ambiance/Radiance and with my homemade theme derived from light-themes. 
Cimitan says it is not a unico/light-themes issue but an upstream gtk bug. I trust him :)

---

### Post by MacUntu on 2012-03-28
Noticed some color issues too.

[img]http://assets.diylol.com/hfs/c88/aae/bb5/resized/the-most-interesting-man-in-the-world-meme-generator-i-don-t-always-see-bugs-in-ubuntu-1-but-when-i-do-it-s-close-to-the-release-16c7d1.jpg[/img]

---

### Post by MacUntu on 2012-04-13
Any news on this? Are there any bug reports?

I'm seeing weird stuff on long running systems like items not maintaining the right height/width. E.g.: Sometimes menu items would appear less high when hovered, therefore causing the items below it to "jump" upwards. In Nautilus bread crumbs view I can observe the same behavior vertically. Also, sometimes in Nautilus I get wrong highlight colors for some items. Unfortunately I found no way to reproduce it, happens seemingly randomly.

---

### Post by NHclimber on 2012-04-13
> **MacUntu said:**
> Any news on this? Are there any bug reports?
A large tree merge is coming soon that means to address most of the shortcomings of the current CSS handling.  The introductory email was just this week here [http://mail.gnome.org/archives/gtk-devel-list/2012-April/msg00027.html](http://mail.gnome.org/archives/gtk-devel-list/2012-April/msg00027.html)

The good news is that it will dramatically improve both performance and correctness. But I can't see this large a merge coming any sooner than Ubuntu +2, if even. And these aren't the kind of fixes that get cherry-picked for backports.

> **MacUntu said:**
> I'm seeing weird stuff on long running systems like items not maintaining the right height/width. E.g.: Sometimes menu items would appear less high when hovered, therefore causing the items below it to "jump" upwards. In Nautilus bread crumbs view I can observe the same behavior vertically. Also, sometimes in Nautilus I get wrong highlight colors for some items. Unfortunately I found no way to reproduce it, happens seemingly randomly.
I see this stuff all the time too. It's not my experience that it gets worse with running time -- seems bad all the time. Menus are the worst.

There are plenty of gnome bugs filed against these problems (some even with easy-to-compile-and-run-testcases :) )

---

### Post by MacUntu on 2012-04-14
Thanks for the update. ;-)

---

