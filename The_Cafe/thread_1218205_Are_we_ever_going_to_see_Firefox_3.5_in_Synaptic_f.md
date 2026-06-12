---
title: "Are we ever going to see Firefox 3.5 in Synaptic for Intrepid?"
date: 2009-07-20
forum: The Cafe
---

### Post by bluelamp999 on 2009-07-20
I only ask because it's weeks now since the release of 3.5...

---

### Post by moster on 2009-07-20
You have it. It came few days after mozilla gave it on their web page.

install it like this:

```
sudo apt-get install firefox-3.5
```

:)

(I guess you can click on it in synaptic but there are more stuff related so better is like this)

edit:
And it is called shiretoko and have blue icon. :)

---

### Post by Mr. Picklesworth on 2009-07-20
Moster, he's asking if it will be in there for *Intrepid* :)
In that case, no, it will not be. The official repositories do not see major upgrades (or new releases) mid release except in special circumstances.

There is always this PPA: [https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa)
There isn't a 3.5 build for Intrepid, but it's possible that the Jaunty one *may* cooperate.

---

### Post by aysiu on 2009-07-20
No, it won't ever be released for Intrepid or Hardy.

You can add a PPA for it, but I think that's a little annoying, since it doesn't have the Firefox branding or user agent string, and then you also have to manually switch over your launchers or preferred applications to the non-branded Firefox.

It's probably best to use one of these two methods to just get the Mozilla-branded Firefox straight from Mozilla:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by MaxIBoy on 2009-07-20
Most programs do not get updated after the release of the distro version, **unless the update is a security update.** And they'd rather go for a single patch to the old one, than an all-out conversion to the new one.

What version of the program each package will have, is set in stone just before the release candidate phase. (That is, Intrepid's version of Firefox was the most-recent as of a few weeks before Intrepid's release.)


Which is why I am always on the pre-alpha releases on my desktop (Debian is on my laptop,) and I wish Ubuntu would switch to a rolling release.

---

### Post by bluelamp999 on 2009-07-20
Hi moster,

Sorry if I'm being a bit dumb but will that install an entirely new instance of FF (alongside 3.0.11)?

Or will it upgrade my existing FF to 3.5, thus keeping extensions, passwords, history etc.?

Cheers

---

### Post by aysiu on 2009-07-20
> **bluelamp999 said:**
> Hi moster,

Sorry if I'm being a bit dumb but will that install an entirely new instance of FF (alongside 3.0.11)?

Or will it upgrade my existing FF to 3.5, thus keeping extensions, passwords, history etc.?

Cheers
Both.

It will install the newer Firefox alongside the old one, but it will keep your extensions, history, passwords, etc.

In the cases of the two methods I recommended, the command *firefox* will launch Firefox 3.5.1, and the command *firefox.ubuntu* will launch the old 3.0.11.

If you use the PPA method, the command *firefox* will launch Firefox 3.0.11, and the command *firefox-3.5* will launch Firefox 3.5.1, so you'll have to manually change your launcher and/or preferred application settings to get Firefox 3.5 to launch.

---

### Post by moster on 2009-07-20
Haha, sorry :) I was thinking you are in Jaunty 9.4.

You can add repositories manualy like they said... that is best way for sure.

Or you can just try it by extracting archive and double clicking on "firefox" in that directory and "run".

Can I ask why you are not in jaunty? It is still free and hardware demands are same :)

---

### Post by bluelamp999 on 2009-07-20
Thank you very much Aysiu...

That's cleared it up for me, I'm off to try the psychocats method now...

---

### Post by bluelamp999 on 2009-07-20
> **moster said:**
> Can I ask why you are not in jaunty? It is still free and hardware demands are same :)

My graphics card is an ATI Mobility X300. 

ATI has dropped support for this card in their latest Catalyst driver which is the only driver supported by Xorg 1.6 which is the Xorg version installed with Jaunty.

If I want to keep decent 3D performance I feel I have to stick with Intrepid as AFAIK the open-source ATI drivers are not too hot with 3D.

---

### Post by moster on 2009-07-20
Yes, pity. I was thinking you will say something like that. I too have similar situation. I would say even worse.

Not only I have ati x1250 but problematic sb600 chipset and broadcom wirelles card. I have problem with EVERYTHING. I am waiting carmic koala,

---

### Post by bluelamp999 on 2009-07-20
Hey Moster,

Intrepid has been rock-solid for me but I do like to keep up with the cutting edge and I must say the ATI issue bugs me.

But hey, maybe Karmic will solve both our problems!

Keep the faith...

---

### Post by oldsoundguy on 2009-07-20
along this same line, any clue when it might finally show up at Unbuntuzilla?   (since I run one box with 8.4 LTS for VIDEO reasons, that is the way I update both FF and TB.)

---

### Post by An85Zk9tc8rfjV8i on 2009-09-13
[IMG]http://www.latko.org/wp-content/uploads/2009/02/picture-1.png[/IMG]

---

