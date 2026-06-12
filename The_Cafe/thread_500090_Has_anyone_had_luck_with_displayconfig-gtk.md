---
title: "Has anyone had luck with displayconfig-gtk?"
date: 2007-07-13
forum: The Cafe
---

### Post by aysiu on 2007-07-13
Yesterday, I noticed that [displayconfig-gtk](http://packages.ubuntu.com/feisty/admin/displayconfig-gtk) is in the Universe repositories.

I love the interface, but I couldn't get it to work (I was trying to mirror or extend my laptop onto an external monitor).

Has anyone had any luck using this, or is still alpha... or pre-alpha?

---

### Post by aysiu on 2007-07-16
Bump.

---

### Post by yatt on 2007-07-17
It was able to switch me successfully to the fglrx driver, but it did not recognize the driver I had been using: avivo. Not surprising since avivo has probably had all its releases come after this app was packaged. I'd like to see if it could setup dual display, but I only have one monitor at the moment. I tried rotating my display, and it just messed things up. I should have tried it with the fglrx driver, but never thought to.

---

### Post by DoctorMO on 2007-07-17
It seem to work even though I was using kde, perhaps we'll see a displayconfig-qt? although I gotta say we need to sort out this qt and gtk mess, I quite understand pre-compiled applications needing either one or the other but come on does a python based glade thing really need gtk specificity? it'd be nice if there was a nice python lib which all these tools could use which chooses the best lib for the job (i.e the one that's installed); maybe I'll do it myself with dohickey to get it kde only ready *shrug*

but that doesn't mean the name is any good to have gtk in the name *huh*

---

### Post by phrostbyte on 2007-07-17
> **DoctorMO said:**
> It seem to work even though I was using kde, perhaps we'll see a displayconfig-qt? although I gotta say we need to sort out this qt and gtk mess, I quite understand pre-compiled applications needing either one or the other but come on does a python based glade thing really need gtk specificity? it'd be nice if there was a nice python lib which all these tools could use which chooses the best lib for the job (i.e the one that's installed); maybe I'll do it myself with dohickey to get it kde only ready *shrug*

but that doesn't mean the name is any good to have gtk in the name *huh*

Python needs a GTK+/Qt abstraction badly.

---

### Post by 23meg on 2007-07-17
[QUOTE=DoctorMO]although I gotta say we need to sort out this qt and gtk mess, I quite understand pre-compiled applications needing either one or the other but come on does a python based glade thing really need gtk specificity?[/QUOTE]

displayconfig-gtk is a GTK frontend to the displayconfig tool in KDE's Guidance, which existed long before it.

For those not in the know, [work is underway]("https://blueprints.launchpad.net/ubuntu/+spec/displayconfig-gtk") to integrate displayconfig-gtk as the default tool to configure displays in Gutsy.

---

### Post by aysiu on 2007-07-18
Sounds good, 23meg.

It also sounds as if I'm the only person for whom it is definitely *not* working.

---

### Post by prizrak on 2007-07-18
Wonder how it would work with nVidia driver as that one has a pretty nice config tool included with it. Don't feel like killing my setup with trying right now ;)

---

### Post by Extreme Coder on 2007-07-18
Maybe displayconfig should only be started when an opensource driver is detected? Like the Intel IGPs,ATI R200 and below, and others.
Because nVidia and ATi have their own configuration tools. so the availability of displayconfig would only cause confusion.

---

### Post by prizrak on 2007-07-19
> **Extreme Coder said:**
> Maybe displayconfig should only be started when an opensource driver is detected? Like the Intel IGPs,ATI R200 and below, and others.
Because nVidia and ATi have their own configuration tools. so the availability of displayconfig would only cause confusion.

Another good thing would be for the package to create a shortcut to the nVidia/AMD config tools since you need to know the command to run them. Well nVidia you do not sure about AMD since I never get those cards, not even when I was on Windows.

---

### Post by yatt on 2007-07-19
> **prizrak said:**
> Another good thing would be for the package to create a shortcut to the nVidia/AMD config tools since you need to know the command to run them. Well nVidia you do not sure about AMD since I never get those cards, not even when I was on Windows.
ATI now has the Catalyst Control Center to do things via GUI, but it can all still be done via the command line.

---

### Post by Suzan on 2007-07-19
As far as I know displayconfig-gtk needs RandR 1.2 which is includes in XOrg7.3.

XOrg7.3 will be shipped with Gutsy.

---

### Post by prizrak on 2007-07-19
> **yatt said:**
> ATI now has the Catalyst Control Center to do things via GUI, but it can all still be done via the command line.

I think you misunderstood what I meant. While you get a nice GUI from nVidia to screw with your settings you need to invoke it from the CLI. Not extremely difficult if you know how to do tab completion or alt+f2 but would be nice to have a shortcut to it in Control Center.

---

### Post by 50words on 2007-08-14
> **aysiu said:**
> Sounds good, 23meg.

It also sounds as if I'm the only person for whom it is definitely *not* working.

It isn't working for me, either, and I desperately want it to. This is one of the last things on my "to do before switching Windows to virtualization" checklist. Once I've got easy dual monitor support, I can deal with the rest.

---

### Post by igknighted on 2007-08-14
> **prizrak said:**
> I think you misunderstood what I meant. While you get a nice GUI from nVidia to screw with your settings you need to invoke it from the CLI. Not extremely difficult if you know how to do tab completion or alt+f2 but would be nice to have a shortcut to it in Control Center.

Isn't it in Applications -> System Tools?  Thats where Fedora put Nvidia-Settings for me, can't say for Ubuntu where it might be though.

> It isn't working for me, either, and I desperately want it to. This is one of the last things on my "to do before switching Windows to virtualization" checklist. Once I've got easy dual monitor support, I can deal with the rest.

Nvidia-Settings does dual monitors well if you have an Nvidia card.  For ATI or Intel, I'm not sure what the best way is.  I've never been 100% satisfied tho with any dual monitor config tool with the lone exception of Suse's sax2 tool.  Easiest.  Setup.  Ever.  Windows included.

---

### Post by 50words on 2007-08-14
I have an ATI card. displayconfig will reset the settings on my main (laptop) monitor (although it has some serious issues doing this), but does not want to work for my second monitor.

---

### Post by tehkain on 2007-08-18
So I assume displayconfig-gtk will not be included in gutsy now(it is in at the moment but I guess it will be removed from default) since we will not see Xorg7.3 in gutsy.

---

