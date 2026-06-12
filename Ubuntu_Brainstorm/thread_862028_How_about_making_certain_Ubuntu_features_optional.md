---
title: "How about making certain Ubuntu features optional?"
date: 2008-07-17
forum: Ubuntu Brainstorm
---

### Post by F-3582 on 2008-07-17
Hi, I just thought about this:

Ubuntu normally ships with a lot of features enabled by default. In order to eliminate features you personally don't need, you might have to remove the corresponding package in order to prevent conflict (e.g. installing OSS instead of ALSA - see that other thread). Unfortunately this involves deinstalling the ubuntu-desktop package as well.

So how about a dialog (during installation and in the control center) that lets you automagically enable or disable certain features without "compromising" your system? A uniform wizard to choose from certain different options (open-source driver vs. closed-source ones, ALSA vs. OSS, WiCD vs. NetworkManager, Compiz vs. Metisse vs. no compositing at all, many many others). It would provide an easy way for interested/clueless users to tinker around safely without spamming the discussion forums for help (before and after).

What I would like to have is a tool like Jockey that provides me with this choice. It should also guide me through the necessary configuration steps, because the normal end user won't want to open the terminal in order to make changes to /etc/foo/bar.conf

It could consist of different parts like:

- System (for adjusting APIs, backends etc.)
- Drivers (replacement for Jockey)
- Software (for choosing between "contradicting" pieces of software like Gnome or KDE ;))
- Extensions (for adding capabilities like MySQL server, full SAMBA etc.)

How about this?

---

### Post by rahulthewall3000 on 2008-07-17
> **F-3582 said:**
> Hi, I just thought about this:

Ubuntu normally ships with a lot of features enabled by default. In order to eliminate features you personally don't need, you might have to remove the corresponding package in order to prevent conflict (e.g. installing OSS instead of ALSA - see that other thread). Unfortunately this involves deinstalling the ubuntu-desktop package as well.

So how about a dialog (during installation and in the control center) that lets you automagically enable or disable certain features without "compromising" your system? A uniform wizard to choose from certain different options (open-source driver vs. closed-source ones, ALSA vs. OSS, WiCD vs. NetworkManager, Compiz vs. Metisse vs. no compositing at all, many many others). It would provide an easy way for interested/clueless users to tinker around safely without spamming the discussion forums for help (before and after).

What I would like to have is a tool like Jockey that provides me with this choice. It should also guide me through the necessary configuration steps, because the normal end user won't want to open the terminal in order to make changes to /etc/foo/bar.conf

It could consist of different parts like:

- System (for adjusting APIs, backends etc.)
- Drivers (replacement for Jockey)
- Software (for choosing between "contradicting" pieces of software like Gnome or KDE ;))
- Extensions (for adding capabilities like MySQL server, full SAMBA etc.)

How about this?

This is indeed a long debated issue. However, providing too many options during the install process would only end up confusing a newbie. The whole idea of the Ubuntu Install Procedure is to make it as easy as possible so that the average windows user can install it without a problem. Most novices trying Ubuntu would have no idea as to how to decide between WICD/NetworkManager, Gnome/KDE and would be lost at these options. 
However, experienced users want this functionality and removal of pre-bundled software results in the removal of the package (k/x/u)buntu package which is a problem.
What I think of as a viable option is to allow the advanced users to remove the programs that they do not want without the removal of ubuntu-desktop. In gentoo, for example, one has the option to edit the meta-ebuilds and store local versions of it. If something similar can be done with the meta package ubuntu-desktop as well, it would solve a lot of problem.
So, if I do not want to install Pulseaudio I should have the option to move it from Depends to Recommends/Optional in the meta package.
As for the advanced CD install, that is only possible with a DVD, for only then would you the space to provide all the extra packages. And as far as I know, that is not high on the Ubuntu Developers agenda right now.

---

### Post by F-3582 on 2008-07-17
> **rahulthewall3000 said:**
> This is indeed a long debated issue. However, providing too many options during the install process would only end up confusing a newbie. The whole idea of the Ubuntu Install Procedure is to make it as easy as possible so that the average windows user can install it without a problem. Most novices trying Ubuntu would have no idea as to how to decide between WICD/NetworkManager, Gnome/KDE and would be lost at these options. 
However, experienced users want this functionality and removal of pre-bundled software results in the removal of the package (k/x/u)buntu package which is a problem.
What I think of as a viable option is to allow the advanced users to remove the programs that they do not want without the removal of ubuntu-desktop. In gentoo, for example, one has the option to edit the meta-ebuilds and store local versions of it. If something similar can be done with the meta package ubuntu-desktop as well, it would solve a lot of problem.
So, if I do not want to install Pulseaudio I should have the option to move it from Depends to Recommends/Optional in the meta package.
As for the advanced CD install, that is only possible with a DVD, for only then would you the space to provide all the extra packages. And as far as I know, that is not high on the Ubuntu Developers agenda right now.

Well, you could always give the user a choice between "Standard" and "Custom" installation. Advanced users will use the advanced course, of course.

---

### Post by rahulthewall3000 on 2008-07-17
> **F-3582 said:**
> Well, you could always give the user a choice between "Standard" and "Custom" installation. Advanced users will use the advanced course, of course.

Of course, but as I said to package that on a CD might not be easy. It would need more space and I do not know whether this is viable at the moment or not.

---

### Post by F-3582 on 2008-07-17
> **rahulthewall3000 said:**
> Of course, but as I said to package that on a CD might not be easy. It would need more space and I do not know whether this is viable at the moment or not.
Sure, you are right, but... there's enough space for the standard installation. Which already contains a few controversial packages. Which could be disabled during that process. Also, there could be the choice of either downloading the additional stuff from the internets or booting from the DVD version in the first place.

---

### Post by rahulthewall3000 on 2008-07-17
> **F-3582 said:**
> Sure, you are right, but... there's enough space for the standard installation. Which already contains a few controversial packages. Which could be disabled during that process. Also, there could be the choice of either downloading the additional stuff from the internets or booting from the DVD version in the first place.
That makes sense to me, though I would still like the functionality to define my own version ubuntu-desktop. :P

---

### Post by smartboyathome on 2008-07-17
> **F-3582 said:**
> Well, you could always give the user a choice between "Standard" and "Custom" installation. Advanced users will use the advanced course, of course.

Already been asked for several times, and it probably won't be implimented this time either because more code will create more bugs.

> **F-3582 said:**
> Sure, you are right, but... there's enough space for the standard installation. Which already contains a few controversial packages. Which could be disabled during that process. Also, there could be the choice of either downloading the additional stuff from the internets or booting from the DVD version in the first place.

The install process would make this hard. The problem with it is that the CD just installs an image of the live environment with a fancy script, making this very complicated to setup.

---

### Post by F-3582 on 2008-07-17
Okay, this sounded somehow convincing. But how about creating a fancy piece of software to configure that stuff "post partem"?

---

### Post by smartboyathome on 2008-07-17
> **F-3582 said:**
> Okay, this sounded somehow convincing. But how about creating a fancy piece of software to configure that stuff "post partem"?

That can be a third party effort, imo. There are much more pressing issues Ubuntu needs to solve, like the wireless drivers. :(

---

### Post by galileon on 2008-07-18
> **smartboyathome said:**
> Already been asked for several times, and it probably won't be implimented this time either because more code will create more bugs.


whereas moving to pulseaudio was such a success

---

### Post by smartboyathome on 2008-07-18
> **galileon said:**
> whereas moving to pulseaudio was such a success

I don't think the Ubiquity team had much of a say in the PulseAudio move. They are two separate teams.

---

### Post by galileon on 2008-07-18
> **smartboyathome said:**
> I don't think the Ubiquity team had much of a say in the PulseAudio move. They are two separate teams.

i was comparing the philosophies of "new software = new bugs so we don't do it" and "oh, hey, everybody is going pulseaudio, so let's include half of it so nothing works and let the user figure it out"

fyi, i managed to get to work admirably well on my desktop, but i had to spend hours scavenging for info on the net and figure out which half-dozen or so packages were missing and installed them in synaptic.

given that sound worked perfectly well with gutsy, why didn't the philosophy "if it aint broke dont fix it" prevail in there, but does here?

---

### Post by smartboyathome on 2008-07-18
> **galileon said:**
> i was comparing the philosophies of "new software = new bugs so we don't do it" and "oh, hey, everybody is going pulseaudio, so let's include half of it so nothing works and let the user figure it out"

fyi, i managed to get to work admirably well on my desktop, but i had to spend hours scavenging for info on the net and figure out which half-dozen or so packages were missing and installed them in synaptic.

given that sound worked perfectly well with gutsy, why didn't the philosophy "if it aint broke dont fix it" prevail in there, but does here?

I didn't say new software = new bugs, I said the more code a piece of software has, the more likely it is to have bugs. Ubiquity is one of the most important things in ubuntu (since without it, ubuntu can't be installed), so they try to keep it as minimal as possible.

---

