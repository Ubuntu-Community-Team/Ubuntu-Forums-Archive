---
title: "An overhaul of gDesklets"
date: 2007-10-22
forum: Ubuntu Brainstorm
---

### Post by rogerdean on 2007-10-22
Hello all

i really feel that hardy would be the appropriate point at which to make gDesklets more worthy. 

currently the user has to deal with a fairly odd selection of desklets, some of which work but many throw up errors. the gui lacks the polish we're enjoying in ubuntu

i guess gDesklets (including their website where i went in search of functional, useful applets) just feels like it's not being maintained or had any attention in a while.

these applets are a selling point (along with compiz etc) when ubuntu is competing on bling with Vista and OSX, so lets give them some love!

Allbest
Roger

---

### Post by Lozz on 2007-10-22
A good idea but would it not be easier to simply include screenlets in the repos instead?

---

### Post by rogerdean on 2007-10-22
ah, that's a bit better! hadn't heard of this package. should definitely go in the repos. i still reckon it could do with a bit more 'togetherness' though - 50 quality-certified applets available by default should be there. am sure this will come in time...
cheers
Roger

---

### Post by booljayj on 2007-10-31
Screenlets are definitely something that should be more closely mated with Ubuntu. Right now they aren't very well standardized and many of them have rampant unfixed bugs. Screenlets are, in my opinion, superior to gDesklets, which haven't been updated in quite some time.

---

### Post by coolen on 2007-11-01
Agreed. Screenlets for Hardy would be awesome (combined with Compiz's Widget Layer...we have a ripoff of the OSX Dashboard!).

---

### Post by Neon Lights on 2007-11-01
Go Screenlets. <3 I love them. They're way better than gDesklets. xP

---

### Post by kragen on 2007-11-02
I was going to suggest screenlets - they are very new at the moment, but progress is good :)

---

### Post by teasum on 2007-11-03
Another vote here for screenlets.  

Since Hardy is a LTS release, I would be comfortable with an effort to debug the basic screenlets that already exist and integrate this package into Ubuntu.  Then, perhaps for Hardy +1, there could be an effort to expand the range of screenlet offerings to make it truly robust.  This might be akin to Feisty, which had a very simple 'Desktop effects' option, folowed by Gutsy, with a fuller implementation of Compz.  

Just my .02.

---

### Post by rogerdean on 2007-11-03
teasum, i think that would be the right approach. anyone know how can we make sure this is noticed?

---

### Post by earobinson on 2007-11-03
another vote for screenlets

---

### Post by amiga_os on 2007-11-03
I'd suggest that more of the argument needs to be made first.

gDesklets itself is in Universe, and screenlets is - as already mentioned - not in the repos at all!

If the case was made that widgets like the *lets sets were more central to the os than they are currently treated, then we'd be on good ground.

As it is, I don't any use *lets anymore, because of the faff to install them (I had gDesklets on Dapper, then on my first Edgy install, since then I've not bothered).  That's mainly because they don't "just work" mostly.

I guess if someone packaged screenlets for Ubuntu, then tried to submit the package for consideration in the Universe repo that would be the first step.  Getting screenlets into main would then happen if the package was consistently stable, adn a good enough case was built for widgets being an integral part of the system.

I'd love to see a "widgets" section in System->Preferences.

So... actually the other route would be to either file a bug against Gnome in Launchpad saying "no default widgets interface"... which would probably get ignored 'cos it's an upstream thing... so/or to file a bug with the same name on teh Gnome website.

If there was a standard widget set integrated into Gnome... it would find it's way into Ubuntu.

---

### Post by rogerdean on 2007-11-03
right, thats sound and sobering advice. is anyone willing & able to take this forward? wish i had the knowledge...

so as a first step, is anyone able to make a deb of screenlets, and submit it to both getdeb and for inclusion in universe?

---

### Post by smartboyathome on 2007-11-03
> **rogerdean said:**
> right, thats sound and sobering advice. is anyone willing & able to take this forward? wish i had the knowledge...

so as a first step, is anyone able to make a deb of screenlets, and submit it to both getdeb and for inclusion in universe?

Packages are already made for screenlets, though I do not know if they are up to MOTU's standards.

---

### Post by rogerdean on 2007-11-03
good - where did you see them?
adding the screenlets repos is the only easy method i've found...

---

### Post by smartboyathome on 2007-11-03
[http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/)

The repo is back up on that site. I use the screenlets from there.

---

### Post by rogerdean on 2007-11-03
ah, very cool. right, so how would this now be proposed for universe? what's the system? maybe the screenlets team have already done that - i'll ask them too...

---

### Post by rogerdean on 2007-11-03
seems the debs are missing right now. never mind. anyway, how would one propose them for universe?

---

### Post by 23meg on 2007-11-04
You'd file a bug in Ubuntu (with no source package), and add the "needs-packaging" tag to it. It's been done for Screenlets, but later the bug was changed to a sync request from Debian, since the package arrived in Debian.

[https://bugs.launchpad.net/ubuntu/+bug/113785](https://bugs.launchpad.net/ubuntu/+bug/113785)

---

