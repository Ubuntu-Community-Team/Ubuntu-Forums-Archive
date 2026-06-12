---
title: "Installing Gnome 2.32.1 on Ubuntu 12.04"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wpshooter on 2012-04-20
Is there a way to install Gnome on Ubuntu 12.04 "Precise" and have it look exactly like the layout under Ubuntu 11.04, i.e. with the Administrative & Preference listings under System on the top panel ???

I installed Gnome from Synaptic on a 12.04 installation of Ubuntu and the layout was close BUT not exactly the same as on 11.04.

Thanks.

---

### Post by cariboo on 2012-04-20
Gnome 2 is no longer supported, and may break your installation. Gnome-classic (gnome-session-fallback) is the replacement for the two panel interface of Gnome 2. I imagine if you want it to look exactly like it did back in 10.04 you could install [Mate]("https://launchpad.net/~amanas/+archive/mate-desktop")

---

### Post by kurt18947 on 2012-04-20
There are at least two Gnome 2 feel-likes that are supported.  Mate, which Cariboo907 mentioned and Cinnamon.  You could download LinuxMint 12 which comes with both Mate and Cinnamon as part of the download.  I don't find Cinnamon bad at all.  It's also possible to make Gnome-shell with some extensions and Xfce-desktop work very much like Gnome 2 though neither one has 'System' per-se.  It was a conscious design decision by Gnome 3 & Unity designers to restrict user access to administrative and hardware functions.  I sort of understand why they did it but it's still a PITA for those who know what they're doing and don't want to jump through hoops.

---

### Post by kaldor on 2012-04-20
Is it really neccessary to install outdated software on a new OS? 10.04 is still supported if you want to use GNOME 2.x.

I'm sure you'll have no problems if you either use GNOME 3's panel setup or Unity. It's not different enough to really matter (for me).

---

### Post by wpshooter on 2012-04-20
> **kaldor said:**
> Is it really neccessary to install outdated software on a new OS? 10.04 is still supported if you want to use GNOME 2.x.

I'm sure you'll have no problems if you either use GNOME 3's panel setup or Unity. It's not different enough to really matter (for me).

To me there is nothing outdated about Gnome 2.

It works and (to me, at least) makes much more sense to have SYSTEM administrative & preferences separate from other menu items than it does to have them lumped in all together with stuff that is not related to system type functions.

I feel like Ubuntu is trying to fix stuff that is not broken and greatly ignoring things that really need fixing in their OS that have been broken for ages and yet they get zero efforts to be fix !!!

Thanks.

---

### Post by jbicha on 2012-04-20
Most of the System Administration & Preferences are in System Settings (aka gnome-control-center, which while it existed for years in GNOME 2 wasn't near as nice as it is in GNOME 3). Which kind of proves your point about keeping system configuration separate from apps, but does it better than GNOME 2.

Anyway, complaining here isn't going to do any good. And installing real GNOME 2 is impossible to do safely on Ubuntu 12.04. GNOME Classic isn't too bad and can get better if more interested developers work on it. gnome-panel 3.4 is better than 3.2 which is better than 3.0 and gnome-panel 3.0 fixed several bugs that are still in gnome-panel 2.32.

If the worst thing you can find about GNOME 2 is that System isn't where you're used to, then I think you'll be fine.

---

### Post by Merk42 on 2012-04-20
> **wpshooter said:**
> I feel like Ubuntu is trying to fix stuff that is not broken and greatly ignoring things that really need fixing in their OS that have been broken for ages and yet they get zero efforts to be fix !!!

Thanks.

Actually the decision to move system related functions was done by GNOME (the people who made the UI you like so much) not Canonical/Ubuntu.

Thanks.

---

### Post by wnelson on 2012-04-21
I recenty installed Mate and it brought back some really good memories.

Follow the directions and it works really well with 12.04.

[http://mate-desktop.org/install/#ubuntu](http://mate-desktop.org/install/#ubuntu)

Walt

---

### Post by KBD47 on 2012-04-21
I installed MATE onto Ubuntu 12.04 and it was very very buggy, I don't blame MATE as I've used it elsewhere and it worked fine. Just a bad combo. My suggestion would be to either install Gnome-Panel to Ubuntu, or MATE onto Xubuntu, or wait until next month when MATE comes by default with Mint 13.

---

### Post by wpshooter on 2012-04-21
> **KBD47 said:**
> I installed MATE onto Ubuntu 12.04 and it was very very buggy, I don't blame MATE as I've used it elsewhere and it worked fine. Just a bad combo. My suggestion would be to either install Gnome-Panel to Ubuntu, or MATE onto Xubuntu, or wait until next month when MATE comes by default with Mint 13.

Is there an official release date for Mint 13 ?

Thanks.

---

### Post by mcellius on 2012-04-21
> To me there is nothing outdated about Gnome 2.

It works and (to me, at least) makes much more sense to have SYSTEM  administrative & preferences separate from other menu items than it  does to have them lumped in all together with stuff that is not related  to system type functions.

The interface isn't outdated, of course.  However, Gnome developers made the decision not to keep Gnome 2 up with existing and advancing technologies.  In a technological sense, it _is_ outdated.

That's why several alternatives have been developed.  Off the top of my head there are three: MATE, Cinnamon, and the Gnome classic included with Ubuntu 12.04.  These are not Gnome 2 underneath because if they were they wouldn't run on distros that are keeping current with technological advances, but they all make very good efforts at providing the Gnome 2 desktop experience.

Try them all. Odds are you'll find one you really like.

---

### Post by KBD47 on 2012-04-21
> **wpshooter said:**
> Is there an official release date for Mint 13 ?

Thanks.

I don't think there is an exact day, but it will be released next month.

---

### Post by kansasnoob on 2012-04-22
I'm working on a Precise classic (no effects) guide here:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

It's still missing a couple of features I used in Oneiric:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

But that's just a matter of waiting for the Precise versions of a couple of PPA's :)

It's very snappy on my old VIA C7 w/1GB of RAM, and largely indistinguishable from Gnome 2 other than a slightly rearranged menu. And it'll be supported for 5 years :guitar:

---

### Post by keithpeter on 2012-04-22
> **wpshooter said:**
> To me there is nothing outdated about Gnome 2.

Just an alternatve suggestion: See the first link in my signature. CentOS 6.x has support until 2020. There are 'point updates' every 6 to 12 months, like 10.04 had, and updated applications are distributed with those point updates. You then have a 'coherent' distribution with a defined security policy.

Personally I shall follow the Unity/Gnome 3 developments with interest, and I shall work through Kansasnoob's tour de force howto for the experience.

GNU/Linux gives us the *choice*. Apologies if this is off topic, and I'll go away now :twisted:

Cheers

---

