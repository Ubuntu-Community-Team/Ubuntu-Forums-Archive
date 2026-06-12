---
title: "Still gnome 3.12?"
date: 2014-11-06
forum: Ubuntu Development Version
---

### Post by Chanath on 2014-11-06
I find the gnome shell is 3.12.2 in vervet. when would gnome 3.14 be in the repos? Or should I install 3.14 from a ppa? Have anyone done this?

---

### Post by grahammechanical on 2014-11-06
> [COLOR=#000000]when would gnome 3.14 be in the repos? [/COLOR][COLOR=#000000]

That is a decision for the Ubuntu Gnome developers. Seeing as Gnome shell 3.14 was released about one month before Ubuntu Gnome 14.10 was released, I would say that the development of Gnome 3 shell and Ubuntu Gnome are out of phase. We may get Gnome shell 3.14 in Ubuntu Gnome by the release of Ubuntu Gnome 15.04. 


> Or should I install 3.14 from a ppa?[/COLOR]

What PPA is this? We can install the Gnome 3 PPA. If we also install the Gnome 3 staging PPA then we should understand that we are partaking in an experiment. It is the staging PPA that Gnome shell 3.14 stuff will go first. Then it will go into the Gnome 3 PPA and after that into the next Ubuntu Gnome release. This was the method used by the Ubuntu Gnome developers with Gnome shell 3.12 when it was released.

Regards.

---

### Post by Chanath on 2014-11-06
> **grahammechanical said:**
> [COLOR=#000000]

[/COLOR]What PPA is this? We can install the Gnome 3 PPA. If we also install the Gnome 3 staging PPA then we should understand that we are partaking in an experiment. It is the staging PPA that Gnome shell 3.14 stuff will go first. Then it will go into the Gnome 3 PPA and after that into the next Ubuntu Gnome release. This was the method used by the Ubuntu Gnome developers with Gnome shell 3.12 when it was released.

Regards.

Well, ok.
Using 15.04 Ubuntu is also an experiment...
I have installed it an using it. It is still too early to see 3.14 in the repos, and I won't install 3.14 from ppa for sometime, as I want to see how 15.04 works with dist-upgrades, hmmm daily upgrades. 
Have a good day, Graham [IMG]http://ubuntuforums.org/images/smilies/smile.png[/IMG]

---

### Post by mc4man on 2014-11-06
> **Chanath said:**
> I find the gnome shell is 3.12.2 in vervet. when would gnome 3.14 be in the repos? Or should I install 3.14 from a ppa? Have anyone done this?

gnome-shell  went to 3.12 in 14.10 last June
 [https://launchpad.net/ubuntu/+source/gnome-shell/3.12.2-1ubuntu1](https://launchpad.net/ubuntu/+source/gnome-shell/3.12.2-1ubuntu1)
So wouldn't be surprised if 15.04 followed the same timing give or take a bit.

---

### Post by harry332 on 2014-11-07
Well actually a number of packages belonging to Gnome-shell have already been upgraded in Vivid official repos to 3.14.0 or even to 3.14.1.
See for example gnome-session, gnome-desktop3, gsettings-desktop-schemas, gobject-introspection, at-spi2-atk, at-spi2-core ...

What is still left: for example gnome-shell, mutter, clutter, gtk+3, gdm, gnome-settings-daemon, and so on.

However, all these are stable released versions of the new Gnome-shell.
And they are all available from Gnome3-Staging PPA alone, no need to use any other PPA.
For example in Gnome3 PPA, one can only find Gnome 3.12 packages, also in vivid branch.

I use the Gnome3 Staging PPA all the time. It is in a very good state now, working very well.
Still, note that I do not have Unity installed, only Gnome-Shell 3.14.
More and more packages are being updated from there to Vivid official repos almost every day, the latest being libpeas 1.12.1-2.

See here for yourself, and look at the number of packages marked (newer version available). Those are already in Vivid official repos:

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid)

---

### Post by Chanath on 2014-11-07
> **harry332 said:**
> Well actually a number of packages belonging to Gnome-shell have already been upgraded in Vivid official repos to 3.14.0 or even to 3.14.1.
See for example gnome-session, gnome-desktop3, gsettings-desktop-schemas, gobject-introspection, at-spi2-atk, at-spi2-core ...

What is still left: for example gnome-shell, mutter, clutter, gtk+3, gdm, gnome-settings-daemon, and so on.

However, all these are stable released versions of the new Gnome-shell.
And they are all available from Gnome3-Staging PPA alone, no need to use any other PPA.
For example in Gnome3 PPA, one can only find Gnome 3.12 packages, also in vivid branch.

I use the Gnome3 Staging PPA all the time. It is in a very good state now, working very well.
Still, note that I do not have Unity installed, only Gnome-Shell 3.14.
More and more packages are being updated from there to Vivid official repos almost every day, the latest being libpeas 1.12.1-2.

See here for yourself, and look at the number of packages marked (newer version available). Those are already in Vivid official repos:

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=vivid)

When I said ppa, I meant Gnome3 Staging ppa. As there are lot of 3.14 stuff in Ubuntu-Gnome, I'd wait some more time, without installing Gnome3 Staging, that is, let Vervet come through its stages the natural way. Well, Unity is not installed in Ubuntu-Gnome, though some residue of Unity is still there, for example gir1.2-unity-5.0, libunity-control-center1, libunity-protocol-private0, libunity-scopes-json-def-desktop, libunity9. I suppose we can uninstall them safely. Only wory is why didn't the Ubuntu-Gnome developers didn't delete them. Are these residues or the deleting of these apps might break the system?

---

### Post by harry332 on 2014-11-07
Sure, everyone installs as he or she wishes.
I just wrote that gnome 3.14 is not a development DE anymore, it really is a stable, released DE.

As to libunity9 and its dependencies (libunity-protocol-private0, libunity-scopes-json-def-desktop), note that nautilus depends on them (in Ubuntu). And as we know, nautilus is part of Gnome DE.

---

### Post by Chanath on 2014-11-07
> **harry332 said:**
> 

As to libunity9 and its dependencies (libunity-protocol-private0, libunity-scopes-json-def-desktop), note that nautilus depends on them (in Ubuntu). And as we know, nautilus is part of Gnome DE.

Nautilus is a part of Gnome, but not a part of Unity, though Unity needs Gnome and Nautilus, so, if the devs had forgotten to delete these, and it is Ubuntu-Gnome, these unity stuff could be uninstalled. This is having the Ubuntu base, but not Unity at all. Would you agree, Harry? I am going to uninstall them, let's see if Ubuntu-Gnome would break.:p

EDIT:

Oh yes, if I try to uninstall libunity-protocol-private0, it would **also **uninstall Brasero, Empathy, Nautilus, Shotwell and** most importantly** Ubuntu-Gnome-Desktop. Hmmm...even though Gnome by itself is a DE, Ubuntu had sort of interconnected it with Unity, so if all unity libraries are deleted, the Gnome desktop won't work. This won't happen in Debian and Gnome. Let's see if that is the problem with Xubuntu too.

EDIT2:

Xubuntu also has libunity9, libunity-protocol-private0 and libunity-scopes-json-def-desktop, but if you try to uninstall them the **only **app that would get harmed, meaning uninstalled along with it is Xchat. The XFCE DE would stay back.

---

### Post by mc4man on 2014-11-07
> **Chanath said:**
> . Only wory is why didn't the Ubuntu-Gnome developers didn't delete them. Are these residues or the deleting of these apps might break the system?
Last I checked Ubuntu Gnome uses Ubuntu packages which have been in some cases patched for Ubuntu & include a dep on libunity* (build dep of libunity-dev
As far as the gnome3 ppa's, don't see where it says exclusively for Gnome's shells

you are certainly free to build any source without libunity-dev

---

### Post by harry332 on 2014-11-08
> **Chanath said:**
> Nautilus is a part of Gnome, but not a part of Unity, though Unity needs Gnome and Nautilus, so, if the devs had forgotten to delete these, and it is Ubuntu-Gnome, these unity stuff could be uninstalled. This is having the Ubuntu base, but not Unity at all. Would you agree, Harry? I am going to uninstall them, let's see if Ubuntu-Gnome would break.:p

EDIT:

Oh yes, if I try to uninstall libunity-protocol-private0, it would **also **uninstall Brasero, Empathy, Nautilus, Shotwell and** most importantly** Ubuntu-Gnome-Desktop. Hmmm...even though Gnome by itself is a DE, Ubuntu had sort of interconnected it with Unity, so if all unity libraries are deleted, the Gnome desktop won't work. This won't happen in Debian and Gnome. Let's see if that is the problem with Xubuntu too.

EDIT2:

Xubuntu also has libunity9, libunity-protocol-private0 and libunity-scopes-json-def-desktop, but if you try to uninstall them the **only **app that would get harmed, meaning uninstalled along with it is Xchat. The XFCE DE would stay back.

No you would not break the Gnome Shell DE. The package ubuntu-gnome-desktop is only a meta-package. That means if you install this meta-package, it will pull in core Ubuntu Gnome packages.
However, you can remove anytime the ubuntu-gnome-desktop and nothing is broken by doing so.
Debian and Ubuntu is using meta-packages in order make the complete installation a lot more easier.
In fact, I have installed only those Gnome applications that I need, and for this reason I never keep meta-packages.
But of course by removing libunity9, you will break Nautilus, Brasero, Empathy and Shotwell.

---

### Post by vasa1 on 2014-11-08
> **harry332 said:**
> ...
But of course by removing libunity9, you will break Nautilus, Brasero, Empathy and Shotwell.
**apt-cache rdepends libunity9** has a slightly longer list.

---

### Post by Chanath on 2014-11-08
> **harry332 said:**
> No you would not break the Gnome Shell DE. The package ubuntu-gnome-desktop is only a meta-package. That means if you install this meta-package, it will pull in core Ubuntu Gnome packages.
However, you can remove anytime the ubuntu-gnome-desktop and nothing is broken by doing so.
Debian and Ubuntu is using meta-packages in order make the complete installation a lot more easier.
In fact, I have installed only those Gnome applications that I need, and for this reason I never keep meta-packages.
But of course by removing libunity9, you will break Nautilus, Brasero, Empathy and Shotwell.

I don't really need Brasero, but breaking Nautilus or Shotwell would be a problem. By the way, I checked Debian repos, meaning installed Gnome 3.14.1 from Debian repos to a Debian install I have in another partition. (I have Opensuse 13.2, so I could how Gnome shell works.) Usually we said that Debian is late and that Ubuntu is quicker in having newer apps in the repos, but it looks like Debian is quicker this time. I have a feeling that jumping to Unity, when Gnome3 first came in, must've done some damage to the way how apps would be created in Ubuntu. The quite buggy Compiz, which is behind Unity must also make some trouble. Unity is only needed for vanilla Ubuntu, so the rest of the derivatives should do without Unity at all.

---

### Post by harry332 on 2014-11-08
Well we are talking about Gnome DE here, not Unity DE.
So perhaps usb-creator-gtk can be added to the list, not much else.
But because Nautilus depends on libunity9, there is no point thinking to purge it.

---

### Post by Chanath on 2014-11-08
> **harry332 said:**
> Well we are talking about Gnome DE here, not Unity DE.
So perhaps usb-creator-gtk can be added to the list, not much else.
But because Nautilus depends on libunity9, there is no point thinking to purge it.

As we are talking about the Gnome DE, the Ubuntu-Gnome is exactly clean and quite a bit behind the Debian Gnome, maybe it would be better to use Debian, rather than Ubuntu, if we are thinking of using Gnome DE, Harry?

---

