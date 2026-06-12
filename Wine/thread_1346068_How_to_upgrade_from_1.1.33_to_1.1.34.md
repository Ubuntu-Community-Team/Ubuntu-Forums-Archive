---
title: "How to upgrade from 1.1.33 to 1.1.34"
date: 2009-12-04
forum: Wine
---

### Post by BAMF1501 on 2009-12-04
title explains all

---

### Post by Liolikas on 2009-12-04
Wait few hours system updates are automatic. Check for updates in synaptic.

---

### Post by BAMF1501 on 2009-12-05
still no update :(

---

### Post by karth on 2009-12-05
Things are not automatic, the maintainer (namely, Scott Ritchie) has to build the package before it is released on the repository.

I'd suggest patience.

---

### Post by brian70809 on 2009-12-05
or you can compile your own from their source file.. takes about 5 mins to do.

do a google on "How to compile wine"...

Download their source, unpack into a folder and compile as root.

good luck!

---

### Post by BAMF1501 on 2009-12-06
2 days still no deb :(

---

### Post by beastrace91 on 2009-12-06
Yea... I just got bored and compiled it from Source :)

Its easy really... Check the link in my sig for some halp on the subject ;)

~Jeff

---

### Post by BAMF1501 on 2009-12-06
I tried that it game me some x server error in terminial

---

### Post by dino99 on 2009-12-07
downloaded & installed on Karmic32 & Jaunty32: work very nicely.
With 1.1.33 i was having crash when changing settings; with this one, crashes are gone  :D

---

### Post by Duskao on 2009-12-08
The repo has been updated now. Update your system.

---

### Post by ltrinh on 2009-12-08
I've updated the repos and still no update to wine.  Synaptic only shows 1.1.33.  Any ideas?


Specs:
AMD64 3800+
Nvidia GT250
2 gigs ram
Jaunty

Thanks

---

### Post by dino99 on 2009-12-09
> **ltrinh said:**
> I've updated the repos and still no update to wine.  Synaptic only shows 1.1.33.  Any ideas?


Specs:
AMD64 3800+
Nvidia GT250
2 gigs ram
Jaunty

Thanks


[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by Rody on 2009-12-09
sudo add-apt-repository ppa:ubuntu-wine/ppa

---

### Post by ltrinh on 2009-12-09
Hi Rody and Dino99,

I added the new PPA repositories along with the new pgp key and removed the old winehq repository but still only 1.1.33 shows up after a reload.  Did I put in the wrong pgp key?  The key wasn't easy to find.

Let me know and thanks for the help.

---

### Post by BAMF1501 on 2009-12-09
run sudo apt-get update

then sudo apt-get upgrade

---

### Post by ltrinh on 2009-12-09
Hi Bamf1501,

Did as you said and after sudo apt-get upgrade here's what I got:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Checked update manager and still no wine update. If you used the wrong authentification key then it wouldn't update correctly right?  I'm not getting any warnings like I did before I added the key so it seems fine but just want to make sure.

Now what?

---

### Post by BAMF1501 on 2009-12-09
well if you using 9.10 you dont need a key it automaticly adds one

---

### Post by ltrinh on 2009-12-09
Hmmmmm....

Well I'm using 9.04 Jaunty.  So with that being said do I need a specific authentication key?

---

### Post by Soulcage on 2009-12-10
[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa") only has 1.1.33~winehq0~ubuntu~9.04-0ubuntu1 for jaunty.

---

### Post by ltrinh on 2009-12-10
I guess that would explain why there's no upgrade to 1.1.34 for me then.  Thanks Soulcage.

---

### Post by ltrinh on 2009-12-10
My next question is this then.....


Is there going to be a 1.1.34 release for jaunty?

---

### Post by YokoZar on 2009-12-10
Sorry I fell behind and only updated karmic on the weekend.  Doing Jaunty and earlier now.

---

### Post by ltrinh on 2009-12-10
Thanks Yokozar.  Looking forward to the upgrade.

---

