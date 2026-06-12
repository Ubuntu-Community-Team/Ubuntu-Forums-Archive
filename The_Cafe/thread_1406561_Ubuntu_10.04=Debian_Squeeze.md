---
title: "Ubuntu 10.04=Debian Squeeze?"
date: 2010-02-14
forum: The Cafe
---

### Post by ene_dene on 2010-02-14
I've read that Ubuntu 10.04 will be based on Debian testing branch. Debian Squeeze is now in testing state. Does that mean that Ubuntu 10.04 will have Debian Squeeze stable packages once Squeeze is out?

---

### Post by Tibuda on 2010-02-14
No. Ubuntu packages are freezed before that.

---

### Post by ene_dene on 2010-02-14
> **danielrmt said:**
> No. Ubuntu packages are freezed before that.
Ok, I understand.
So the good thing for Ubuntu stability would be if they synchronized freeze with Debian freeze for LTS versions.

---

### Post by Hallvor on 2010-02-14
> **ene_dene said:**
> Ok, I understand.
So the good thing for Ubuntu stability would be if they synchronized freeze with Debian freeze for LTS versions.

Yes, that was also the Emperor`s plan. The Debian developers will probably freeze it after Ubuntu LTS is launched, or slightly before. Squeeze will probably be ready many months after that.

---

### Post by snowpine on 2010-02-14
The Ubuntu and Debian projects have different goals. The best way to enjoy the stability of Debian Stable is to use Debian Stable. :)

---

### Post by skymera on 2010-02-14
> **snowpine said:**
> The Ubuntu and Debian projects have different goals. The best way to enjoy the stability of Debian Stable is to use Debian Stable. :)

Along with Packages so old that came out before the can of Pepsi i'm drinking was even given life..

---

### Post by snowpine on 2010-02-14
> **skymera said:**
> Along with Packages so old that came out before the can of Pepsi i'm drinking was even given life..

I realize you're just trying to be funny :) but if you actually compare the lists, Debian Stable (Lenny) stacks up pretty well against Ubuntu LTS (Hardy):

[http://distrowatch.com/table.php?distribution=debian](http://distrowatch.com/table.php?distribution=debian)
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

---

### Post by ene_dene on 2010-02-14
> **snowpine said:**
> The Ubuntu and Debian projects have different goals. The best way to enjoy the stability of Debian Stable is to use Debian Stable. :)
Yes, but it makes sense for me, if we're talking about LTS, that should have the same purpose as Debian stable. They are doing double the work. What I mean by that is that bug that is being fixed in Debian stable would be automatically fixed in Ubuntu LTS.

There is nothing wrong in wanting a modern and stable desktop I don't think that they should mutually necessarily be exclusive.

For example, what I like about Debian stable is general system stability, x windows, gnome etc.
But what I like about Ubuntu is that even if I have the older version I can still add repositories for most of the software that I like that has newer packages and that doesn't effect the general stability of system. For example, it can be new Rhythmbox, Miro or newer browser version.

So I think that Ubuntu would highly benefit if they tried to synchronize LTS releases with Debian freeze.

---

### Post by snowpine on 2010-02-14
I think you would really like Mepis: it's based on Debian Stable, but with up to date versions of end-user apps.

---

### Post by Zoot7 on 2010-02-14
> **Hallvor said:**
> Yes, that was also the Emperor`s plan. The Debian developers will probably freeze it after Ubuntu LTS is launched, or slightly before. Squeeze will probably be ready many months after that.
March was the date the Debian developers were hoping for the big freeze I think, but I gather it's going to be a good bit later than that.

> **skymera said:**
> Along with Packages so old that came out before the can of Pepsi i'm drinking was even given life..
Haha, actually if you want more up to date software you can generally grab the source from the testing repos and build it against stable. Not the most convienent or optimum of solutions but it *almost* always works.

---

### Post by ene_dene on 2010-02-14
> **snowpine said:**
> I think you would really like Mepis: it's based on Debian Stable, but with up to date versions of end-user apps.
Yeah, I thought so too but it's KDE, I prefer GNOME.

[QUOTE=Zoot7]Haha, actually if you want more up to date software you can generally grab the source from the testing repos and build it against stable. Not the most convienent or optimum of solutions but it almost always works.[/QUOTE]
Hehe, I actually did that for my server for ufw firewall, but on on desktop... to tell you the truth, I haven't tried it, but I bet it's quite a bit of work. :)

But never mind all that, I got the answer to my question.

---

### Post by Hallvor on 2010-02-14
> **Zoot7 said:**
> 
Haha, actually if you want more up to date software you can generally grab the source from the testing repos and build it against stable. Not the most convienent or optimum of solutions but it *almost* always works.

You might pronounce the word "up-to-date software" but it could just as well be spelt "b-u-g-s". A cutting edge system means just that: Bugs.

Debian Lenny is by far the best distro I have tried. Ubuntu Dapper wasn`t that bad either. But stability is number one for me. I don`t mind sticking with older applications as long as they are well tested.

Others prefer stable with backports, Debian testing/squeeze, Debian sid or even Debian experimental. It can be as stable or cutting edge as you want.

---

### Post by Hallvor on 2010-02-14
> **ene_dene said:**
> Yeah, I thought so too but it's KDE, I prefer GNOME.


Hehe, I actually did that for my server for ufw firewall, but on on desktop... to tell you the truth, I haven't tried it, but I bet it's quite a bit of work. :)

But never mind all that, I got the answer to my question.

If you want to test it in a VM or install it, try the Debian Squeeze netinstall, [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/) It should be more up-to date than Ubuntu and much less work than compiling what you need.

Other architectures are found here:
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by sgosnell on 2010-02-14
In Debian, 'stable' doesn't mean what many people think it means.  Stable means there is no more development at all, not that there are no crashes.  Unstable means that bug fixes and improvements are still being made.  The unstable version might actually have fewer crashes than the stable version on some systems, but there is still active development on the unstable version, while it has completely ceased on the stable version.

---

### Post by ene_dene on 2010-02-14
> **sgosnell said:**
> In Debian, 'stable' doesn't mean what many people think it means.  Stable means there is no more development at all, not that there are no crashes.  Unstable means that bug fixes and improvements are still being made.  The unstable version might actually have fewer crashes than the stable version on some systems, but there is still active development on the unstable version, while it has completely ceased on the stable version.
But in case of Debian stable it's safe to assume true stability as well since packages are extensively tested. It's probably the most stable system out there.

---

### Post by snowpine on 2010-02-14
> **sgosnell said:**
> In Debian, 'stable' doesn't mean what many people think it means.  Stable means there is no more development at all, not that there are no crashes.  Unstable means that bug fixes and improvements are still being made.  The unstable version might actually have fewer crashes than the stable version on some systems, but there is still active development on the unstable version, while it has completely ceased on the stable version.

That's simply not true. :) Debian Stable (as with all "stable" distributions including Ubuntu) continues to receive bug fixes and security patches throughout its lifespan. (1 year after the next stable release, in Debian's case.) Release day is the *beginning* of support and maintenence for a stable release, not the *end*.

---

### Post by Zoot7 on 2010-02-14
> **ene_dene said:**
> Hehe, I actually did that for my server for ufw firewall, but on on desktop... to tell you the truth, I haven't tried it, but I bet it's quite a bit of work. :)
Indeed it is! Although given that the source is already "debianized" for you it's easy to build the .debs directly *most* of the time.

> **Hallvor said:**
> You might pronounce the word "up-to-date software" but it could just as well be spelt "b-u-g-s". A cutting edge system means just that: Bugs.

Debian Lenny is by far the best distro I have tried. Ubuntu Dapper wasn`t that bad either. But stability is number one for me. I don`t mind sticking with older applications as long as they are well tested.
Agreed on both accounts, cutting edge does indeed mean bugs. TBH I've kind of got sick of the more cutting edge distros. I've Debian Squeeze on my laptop and it's just about right for me, mind you I probably wouldn't use Squeeze until coming up to the big feature freeze.
I've a heavily customized version of Lenny on my desktop. Newer kernel, newer version of Alsa, and most of the software I use on a daily basis pulled down from either the testing or unstable repos and built from source.

I agree with you about stability, were I pushed to choose one distro I'd probably go for either Debian stable or an official release of Slackware, nothing touches either when it comes to stability IMO. :)

---

