---
title: "Why is Ubuntu 16.04 including a featureless Totem release?"
date: 2016-07-13
forum: Ubuntu, Linux and OS Chat
---

### Post by lads on 2016-07-13
Hi everyone,

I understand these questions may not be entirely comfortable to everyone. But I do not wish to condemn or judge the decisions that led to this situation, I would just like to know the reasons that lead to them.

I have been upgrading the desktop systems on which I work from 14.04 to 16.04 and one thing that soon became apparent is a number of features missing from Totem, most notably [the playlist]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1600606"). The GUI to this programme has been so shorn that is practically useless as it stands.

Apparently, this was known to the Ubuntu developers, but still they decided to go ahead with this newer despoiled Totem instead of sticking to an earlier and full featured release. The question is: why? Are there technical reasons?

A similar story happened with Nautilus, but these days it takes just a few minutes to replace it with Nemo. Then it was Evince but luckily Okular is available directly from the Software Centre. Where will this end?

---

### Post by sudodus on 2016-07-13
[https://wiki.gnome.org/Apps/Videos](https://wiki.gnome.org/Apps/Videos)

Totem (as well as Nautilus and Evince) is Gnome software. What you notice is due to Gnome's current policy, that you might like or dislike. Ubuntu uses the upstream version of Totem as well as other software.

Fortunately it is easy to remove program packages and install one of many alternatives.

It is not feasible to maintain own versions, except the big exception: MATE. If you prefer the old style Gnome software and appearance, I suggest that you try ***Ubuntu MATE***.

-o-

If you want Ubuntu to replace program packages, please try to create opinion about it (for example here), and after that, you can try to convince those responsible for the selection of program packages. They are seldom active at our Ubuntu Forums, but you can reach them via IRC or mailing lists. You find some links near the top of the Ubuntu Forums pages 'Forum Community', 'Ubuntu Community', 'Other Support', ...

---

### Post by lads on 2016-07-14
In Software Engineering, requirements and functionality are not a matter of taste.

I am pretty happy with Unity, I do not wish to change to a different DE. I am just interested in understanding why are developers apparently not involved in Unity/Ubuntu having such a big impact on the ultimate performance of the distribution.

Cheers.

---

### Post by grahammechanical on 2016-07-14
Gnome is not a commercial organization. In commerce if a product does not do what the customers want it does not sell and the organization goes out of business. At the moment Ubuntu is built on Gnome desktop environment and it makes use of many Gnome applications. It is convenient at present to do that.

I think about the Ubuntu phone OS. New core applications are being built and designed for convergence. We may yet see some useful Community/Canonical developed desktop applications come out of the Ubuntu phone/tablet development process.

I also wonder just how much of the Gnome Desktop Environment is in the Ubuntu phone/tablet OS. Even though Ubuntu itself is not a commercial product Ubuntu phones, tablets and laptops are commercial products and the customer has to be kept satisfied.

Regards.

---

### Post by uNoubu8a on 2016-07-15
Many distro's are facing the issue of having upstream software that has become lacking in what they deem fit (or troublesome to make compatible).  This is one of the reason for Linux Mint forking so many applications and creating there x-applications.  What Gnome is doing is not working for them any longer.  Problem is this is something that takes a lot of resources that previous was spent on something else.

Like has been posted already, thank goodness for alternatives that are easily install-able.

---

### Post by mastablasta on 2016-07-16
snaps will provide solution - one could then easilly install older version of the app.

---

### Post by uNoubu8a on 2016-07-16
> **mastablasta said:**
> snaps will provide solution - one could then easilly install older version of the app.

...security issues and all...

---

### Post by mc4man on 2016-07-16
Ot to actual question but if wanting a 'totem' like previously inc. the browser plugin then take a look here - 
[https://launchpad.net/~embrosyn/+archive/ubuntu/xapps](https://launchpad.net/~embrosyn/+archive/ubuntu/xapps)

To note: 
As it's pretty much a port of totem the app name & .desktop Name= is Videos. The icon used is similar to what Totem/Videos but different. So while the command to open is different (xplayer) it will at a quick glance appear to be totem in the Dash
It also includes a thumbnailer but that isn't a drop in replacement for the totem thumbnailer that is used by nautilus so totem should be kept (- though one can make nautilus use the xplayer thumbnailer
grilo plugin support is not included, may not be possible though I'm looking at. (the current grilo plugin support in totem is pretty crappy anyway

I'm looking at some possible improvements, is they work out will also be available  [here]("https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media") at some point

---

### Post by mastablasta on 2016-07-16
> **work-work said:**
> ...security issues and all...

should not be an issue as they are self contained/sandboxed/jailed whatever you call it. besides not all apps are connected outside. numerous games for example are local versions only.

---

### Post by uNoubu8a on 2016-07-16
> **mastablasta said:**
> should not be an issue as they are self contained/sandboxed/jailed whatever you call it. besides not all apps are connected outside. numerous games for example are local versions only.

Ok[ from this article ]("http://www.infoworld.com/article/3060246/security/ubuntu-snap-doesnt-have-the-security-issue-x11-does.html")I read some time ago it mentions that the way X11 does security eliminates some of the benefits of the way snaps are sand boxed.  So they don't introduce more risks (that we are aware of) but aren't as secure as they claim (currently)

---

### Post by lads on 2016-07-18
Thank you all for the many replies, very interesting information gathered here.

So far the only arguments provided to justify the adherence to defective software is that it is either impractical or that it consumes too many resources. However, another GNome based distribution, Mint, has been thoroughly tackling the issue with a workforce of three (3) developers. Therefore the reasons to keep rolling this ever degrading GNome applications may have a different nature.

Finally I would like to note that at this time it is easier to shift to Mint and then install Unity on it, than to go with Ubuntu and fix/replace all the broken GNome applications one by one.

Regards.

---

### Post by vasa1 on 2016-07-18
All the best with your move to Mint.

While there is a subforum for posts related to Mint [here]("https://ubuntuforums.org/forumdisplay.php?f=453"), [https://forums.linuxmint.com/](https://forums.linuxmint.com/) is the official support venue for Mint.

---

### Post by lads on 2016-07-22
> **vasa1 said:**
> All the best with your move to Mint.

That is an elegant way of avoiding the subject. Cheers.

---

### Post by QIII on 2016-07-22
No, it was not avoiding the subject.  It was simply acknowledging that you are a wise person who, knowing that a move to Mint would be easier, would surely be pragmatic and practical enough to take that route.  Hence, the well wishes.

As you are seeking a direct answer to your question and none of us here is an employee of Canonical, Ltd, the distributor of Ubuntu, I suggest you direct your query at Canonical's developers.  We cannot answer for them, neither are we responsible for their decisions.

You might first start here:  [email]ubuntu-devel-discuss@lists.ubuntu.com[/email]

Thread closed.

---

