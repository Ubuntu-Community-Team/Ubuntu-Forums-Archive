---
title: "nvidia-96 ripped from kubuntu repos"
date: 2013-01-08
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-01-08
Just unbelivable!!.  I was working this great, excellent Raring install using an old 01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) and then I went to update (after eyeballing the Compiz Topic in another forum) and much to my dismay that driver (nvidia-96) is no longer available in the repos (synaptic) and it now will not allow any desktop effects.

Also, another anomoly, Using the 3.8.x.xRC kernel  on Lucid and it too just outright bumped (nvidia-96) but it is at least still in the repos.

  So for a newbie or oldtimer using older equipment - beware.. that nvidia-96 will get ripped from your repos.

---

### Post by |{urse on 2013-01-08
Very helpful, glad I read this first.

---

### Post by ventrical on 2013-01-08
> **|{urse said:**
> Very helpful, glad I read this first.


..and..

```

ventrical@ventrical-desktop:~$ sudo apt-get install nvidia-96
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-96 is a virtual package provided by:
  nvidia-experimental-310 310.14-0ubuntu2
  nvidia-experimental-304 304.48-0ubuntu1
  nvidia-current-updates 304.64-0ubuntu1
  nvidia-current 304.51.really.304.43-0ubuntu2
  nvidia-173-updates 173.14.35-0ubuntu3
  nvidia-173 173.14.36-0ubuntu1
  fglrx-updates 2:9.000-0ubuntu5
  fglrx 2:9.000-0ubuntu4
You should explicitly select one to install.

E: Package 'nvidia-96' has no installation candidate

```

...the regressions just keep getting worse.

---

### Post by Pjotr123 on 2013-01-08
Yes, and the sad thing is, that after considerable clamour from the user base, Nvidia has kindly released a final edition of nvidia-96 that will work with the Xorg of Ubuntu 12.04 (not with the Xorg of Ubuntu 12.10 and higher).

Debian has added this "new" nvidia-96 to it's repo's months ago. I contacted the Ubuntu repo maintainer who's responsible for Nvidia about this, but he hasn't found time yet to add it.... :(

---

### Post by ventrical on 2013-01-08
> **Pjotr123 said:**
> Yes, and the sad thing is, that after considerable clamour from the user base, Nvidia has kindly released a final edition of nvidia-96 that will work with the Xorg of Ubuntu 12.04 (not with the Xorg of Ubuntu 12.10 and higher).

Debian has added this "new" nvidia-96 to it's repo's months ago. I contacted the Ubuntu repo maintainer who's responsible for Nvidia about this, but he hasn't found time yet to add it.... :(

 Thanks for this information. The strange thing is that when I first upgraded my 12.04 kubuntu install to Raring (kubuntu) it worked like a charm through several updates afterwards.  I was just prompted recently to update it yesterday and now the BIG surprise.

  However, part of my volunteering here in the forums is to expect the unexpected no matter how ridiculously illogical it is. Oddly enough Unity 2D will work just fine with Precise on that same machine  with that same video adapter card but Precise is  so slow (now-a-days) that it is actually boring on older machines. Early Kubuntu Raring was really snappy (with KWIN effects) but all the distros , during their development, seem to gather moss, luggage and other baggage and what is once a snappy, whimsical desktop experience eventually regresses into a crumudgeon  of an old grumpy pants.  :)

 edit* I mean I am laughing here ..:) I just don't get it.

---

### Post by Pjotr123 on 2013-01-08
You might find this background info useful:

1. Announcement of the new nvidia-96.43.23 from upstream:
[https://plus.google.com/118125769023950376556/posts/RfCBEGaPHnX](https://plus.google.com/118125769023950376556/posts/RfCBEGaPHnX)

Note that it adds support for X.Org 1.11 and 1.12, not higher. Good enough for 12.04 LTS, which is why it would be great to have it....

2. The Debian repo for 96.43.23-x:
[http://packages.debian.org/sid/nvidia-glx-legacy-96xx](http://packages.debian.org/sid/nvidia-glx-legacy-96xx)

The important minor release number is 23. 

It should be very easy for a developer to cherry-pick this from the Debian repo, I suppose....

---

### Post by ventrical on 2013-01-08
Yes.. we are at  x.org 1.13 now. Guess I'll just eat crow and install Precise.

Thanks you for your research.

regards,
ventrical

---

### Post by bird1500 on 2013-01-08
Nouveau isn't good enough for such old hardware?

---

### Post by Pjotr123 on 2013-01-09
> **ventrical said:**
> Yes.. we are at  x.org 1.13 now. Guess I'll just eat crow and install Precise.


Note that it's not available yet for Precise.... I'm not even sure whether it'll ever become available at all. :-(

---

### Post by ventrical on 2013-01-09
> **bird1500 said:**
> Nouveau isn't good enough for such old hardware?


It will keep comming up with this nouveau:loop error at start up.

---

### Post by ventrical on 2013-01-09
> **Pjotr123 said:**
> Note that it's not available yet for Precise.... I'm not even sure whether it'll ever become available at all. :-(


What I meant is that I would install Precise and settle for Unity 2D on these older cards. I really appreciate Unity 2D, but it's just too bad that I can't continue testing that in U+1.

 I went out and got a Radeon 9600 ATi cards so I'll see what happens from there.

---

### Post by ventrical on 2013-01-09
Ok.. I went and aquired an old 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AP [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AP [Radeon 9600] (Secondary)
ventrical@ventrical-desktop:~$ 

and Kubuntu works just beautiful as well as Unity 3D and all my other experimentals.  I will use the old nvidia card for a precise install.

Thanks all.

---

### Post by TREESofRIGHTEOUSNESS on 2013-01-09
> **Pjotr123 said:**
> 

It should be very easy for a developer to cherry-pick this from the Debian repo, I suppose....

You could make a bzr branch and propose it for merging, for 13.04, and then do a SRU to get it into precise, if you are very interested and have the time, that is :)

---

### Post by ventrical on 2013-01-10
Testing Ubuntu versions is all about time and having it! There are all sorts of surplus adaptor  cards in these parts.  It is a lot easier to just go out and get another card thats listed.  Going through this experience however, demonstrates to me that there is nothing safe in the Ubuntu U+1 repos. There will always be changes in the infrastructure of how the GUI is rendered (no matter what desktop experience) and any video adapter card may find itself victim to become obsolete during the development cycle.

  But it should be:* FOSS end_user beware*, especially in Ubuntu's case, because unsuspecting end_users with installs of Precise Pangolin ,or previous, will be prompted to upgrade to Quantal or ... Raring Ringtail only to find that , not only is their previous install busted and not recoverable, but there current *upgrade* is inoperable. 

 Not everyone has the expertise or experience to install video adaptor cards (most application end_users don't even know what a motherboard is). Although I do understand that Ubuntu versions are currently  being developed to  be more 'sexy', a lot of end users are being left in the dust and excluded. And telling persons who fall victim to this type of obsoletion to try a different version such as Lubuntu or Xubuntu does not really address the matter squarely.

---

### Post by tepsipakki on 2013-01-10
Eh, just enable precise-proposed and install the update. You'd know if you were subscribed to the bugreport:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/948053)

note that unity won't work with effects, since the driver doesn't support some GL features unity depends on.

---

### Post by Pjotr123 on 2013-01-10
Excellent news! Thanks. :D

---

### Post by ventrical on 2013-01-10
> **tepsipakki said:**
> Eh, just enable precise-proposed and install the update. You'd know if you were subscribed to the bugreport:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/948053)

note that unity won't work with effects, since the driver doesn't support some GL features unity depends on.

 Ummm... but this happened on a Raring Ringtail install, not Precise.

So what am I missing here?

Thank-you.

Regards,
Ventrical

---

### Post by tepsipakki on 2013-01-10
What happened? The unity features? Those probably got backported, so there you go.

---

### Post by ventrical on 2013-01-10
> **tepsipakki said:**
> What happened? The unity features? Those probably got backported, so there you go.


The KWIN effects will not work because the nvidia-96  driver is no longer in the repos.

Hello!?

When I updated it ripped (extracted) the nvidia-96 driver. Kubuntu does not use Unity Features.

---

### Post by tepsipakki on 2013-01-14
So you missed the fact that the last xserver release nvidia-96 supports is 1.12? Quantal and raring both have 1.13, and raring will get 1.14 at some point.

IOW there's no point in keeping a non-functional and abandoned driver in the repo.

---

### Post by ventrical on 2013-01-14
> **tepsipakki said:**
> So you missed the fact that the last xserver release nvidia-96 supports is 1.12? Quantal and raring both have 1.13, and raring will get 1.14 at some point.

IOW there's no point in keeping a non-functional and abandoned driver in the repo.


No .. I never missed that fact .. only the surprise that there was no warning or notification of any kind.  That kubuntu install was working great until I *updated*.. and then from there it went south (that means borked!). 

 So I am just pointing out the fact that raring  (13.04) is leaving debris in it's path as it updates. It is slowly obsoleting older hardware as it regressively develops.  And this is a regression.  It is certainly not an improvement - perhaps for tablet PCs .. yes .. but not for legacy hardware.

  However .. the fault is mine in that I erroneously assumed that Kubuntu was immune to the erratic development blunders that have been par for the course over the last three ubuntu developments and ,as a beta tester, I know this  breakage  is also par for the course. It was not my intent to whine , belly ache or complain. I am just making a note that as this current development progresses, an otherwise good working alpha install will get ripped - hence end_user beware!

 And thank you for confirming the facts for me.

regards,
ventrical

---

### Post by tepsipakki on 2013-01-16
Updated from where? There was no functional driver since 11.10. Precise and quantal were equally broken with that driver, as raring was from day 1.

NVIDIA stopped supporting the hw, not us. Don't know how well nouveau works with old cards, YMMV.

---

### Post by Hairy_Palms on 2013-01-16
to be fair its good of nvidia to keep the linux driver running this long, there was never even a vista driver for the geforce 2 mx, let alone win7 or win8

---

### Post by ventrical on 2013-01-16
> **tepsipakki said:**
> Updated from where? There was no functional driver since 11.10. Precise and quantal were equally broken with that driver, as raring was from day 1.

NVIDIA stopped supporting the hw, not us. Don't know how well nouveau works with old cards, YMMV.

 Well that is NEWS to me because I had the nvidia-96 driver in there when I had *upgraded* a 12.04 install to Raring Ringtail as far back as the toolchain! I had updated that install every other day and then I let it sit for a few weeks without updating. Then (on the date that I wrote this original post) I updated and it completely broke the install.

  The way I solved it was buy putting in a compliant ATi radeon 9600 card. So I still have the original install. That means that most of the .log files are still there. So  what would be the best log file to look at to authenticate my declarations?

thanks in advance

---

