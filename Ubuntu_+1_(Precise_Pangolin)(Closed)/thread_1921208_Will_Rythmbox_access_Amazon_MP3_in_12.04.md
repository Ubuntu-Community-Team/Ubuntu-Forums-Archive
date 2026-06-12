---
title: "Will Rythmbox access Amazon MP3 in 12.04?"
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Dragonbite on 2012-02-06
I read somewhere that Rythmbox is coming back as the default Music player for Ubuntu in 12.04 (such a short life for Banshee).

When the UbuntuOne music store was announced there was a plugin for Rythmbox to access it like a mini "iTunes store" so I think it would be safe to assume that it will be included again too.

Banshee, though, allowed for purchasing and downloading music from Amazon (with the controversial revenue sharing).

So is this going to be dropped with 12.04?  I am talking about more out-of-the-box setting. I know I can install Banshee and the extensions on my own later.

---

### Post by sffvba[e0rt on 2012-02-06
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by Dragonbite on 2012-02-06
I also wonder if Canonical is still taking their portion of the revenue Banshee makes from Amazon MP3 sales if it is not the default player for Ubuntu?

---

### Post by Yellow Pasque on 2012-02-07
The ubuntuone rb plugin is now in the precise repo, but it crashes on me when I try to use it.

---

### Post by Dragonbite on 2012-02-07
I'm not so worried about the UbuntuOne plug-in.  It worked in the past and there has been a lot of changes in U1 lately that I'm sure they will fix any issues before release.

I'm not even 100% sure they are replacing Banshee with Rythmbox yet, to be honest.

---

### Post by sffvba[e0rt on 2012-02-07
> **Dragonbite said:**
> I'm not even 100% sure they are replacing Banshee with Rythmbox yet, to be honest.

Why?


404

---

### Post by Dragonbite on 2012-02-07
Ok, I think I found the article that started this (for me).

[[COLOR="Blue"]http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html[/COLOR]]("http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html")

> As for the second session, most people who have attended the default applications session today at UDS-P have agreed to replace Banshee with Rhythmbox by default. However, decision is not final as there are a few things that need to be checked first (like Unity Music Lens integration, etc.).

The main reason for this is that Banshee still uses GTK2 and the GTK3 branch is currently blocked by some missing GTK# 3 features. And this blocks porting the Ubuntu One Music Store plugin to GTK 3 and it prevents it from working properly on ARM.

So it isn't a done deal as of this point, but I haven't heard anything one way or the other since.

---

### Post by sffvba[e0rt on 2012-02-07
> **Dragonbite said:**
> Ok, I think I found the article that started this (for me).

[[COLOR="Blue"]http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html[/COLOR]]("http://www.webupd8.org/2011/11/rhythmbox-might-replace-banshee-in.html")



So it isn't a done deal as of this point, but I haven't heard anything one way or the other since.

AFAIK it is the default (but I am not finding any definitive links to back that up at the moment :D)


404

PS - Got one [https://lists.ubuntu.com/archives/ubuntu-desktop/2011-November/003467.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2011-November/003467.html)
Another - [https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-default-apps](https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-default-apps)
Another - [https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha1)

---

### Post by cariboo on 2012-02-07
On my last fresh install (alpha 2 last Thursday) Banshee wasn't included, so I'd suggest that Rhythmbox is now the default.

---

### Post by Dragonbite on 2012-02-08
> **cariboo907 said:**
> On my last fresh install (alpha 2 last Thursday) Banshee wasn't included, so I'd suggest that Rhythmbox is now the default.

Is there an Amazon plug-in for Rythmbox?

I like the idea of UbuntuOne Music Store, and have no problem with using them and Canonical getting some money from each purchase.  I was all excited with that prospect.  Unfortunately the selection is limited.

Now if UbuntuOne Music Store could have a front end similar to what is currently used, but has Amazon in the back-end for selection and Cloud-Player sync then I wouldn't care whether it was Banshee or Rythmbox!

---

### Post by ubuntukid on 2012-02-08
If, like me, you only have access to the EU store, the selection in the Ubuntu One store is lackluster. The front page with "EU Store Top Picks" and "Recommendations" hasn't changed since I made my first purchase over half a year ago. Also, the actual downloading of songs has never been particularily impressive for me. It almost always takes me over half an hour before songs show up on my computer after purchase. When running iTunes on Windows, they appear in less than a min with my internet connection.

---

