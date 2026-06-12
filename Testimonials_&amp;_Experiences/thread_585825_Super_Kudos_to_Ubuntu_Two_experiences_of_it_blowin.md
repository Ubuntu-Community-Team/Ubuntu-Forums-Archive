---
title: "Super Kudos to Ubuntu: Two experiences of it blowing up and ease of recovery"
date: 2007-10-21
forum: Testimonials &amp; Experiences
---

### Post by tragen on 2007-10-21
First off, hats off to the lineage of free software, open source and specifically all those involved in having made Ubuntu what it is today.

I figured I would share my recent experiences with Ubuntu having been blown up (through no fault of Ubuntu) in less than a week that were easily recovered from.

I have used Ubuntu as my workstation for just over a year now and have been quite happy with it. However I have had it blown up twice in one week, once totally my fault and the second through a power outage right in the middle of upgrading to 7.10

The first was last week, tired, I made the mistake of uninstalling python from the synaptic package manager. I didn't realize how integral it was to the gnome desktop and the reason I did it was that I was troubleshooting a democracy player update that had been greyed out in the updates menu for quite a number of weeks (months?).

The democracy player update had wanted a lower version of python, I checked what version was installed..2.5 if I recall correctly...and saw that the 2.4 was flagged as being in. In my tired state I figured...hmm, I will just uninstall 2.5 update the democracy player update and then install the 2.5 back in (not realizing how it would affect the whole desktop. I know, my bad.

Once it started showing the removal of desktop components I realized the gravity of what was being done. Rather than stop it, I was curious as to how far it would go and how bad it would blow things up.

Long story shorter, the gui desktop was horribly broken. Also long story short, the fix wound up being rather easy. I just had to boot to the commandline and run the "sudo apt-get install ubuntu-desktop" command to rebuild the desktop.

Gui desktop was back, all the settings/apps fine (except a desklets app that wasn't back, but big deal).

So had I known about the command from the start, I would have been back up and running in under an hour (as opposed the the 3.5..which in all fairness most of which was downloading the iso and burning a new copy...as the original one I had...I had given to a friend. It was my intention, in windows thinking mode, of installing over the top via use of the install CD, but it wanted to reformat the existing partition rather than just accepting what partition to install into).

So that brings me to this morning and the 2nd blow up.

During the installing phase of the 7.10 upgrade, my house experienced a one second power outage/hiccup that was enough to kill the computer. Grrreat.

Sure enough the computer was powered up to a kernel panic message. "kernel panic: VFS: unable to mount.." as I recall.

Using the aforementioned live/boot CD, I booted up and got on the web to look up some information. 

Long story short again, all I had to do was hit escape at GRUB and pick an older kernel version (recovery mode) to get to the commandline and then ran the "dpkg --configure -a" to reconfigure/update the computer.

It finished up and was booted up as the perfectly fine as the newly upgraded 7.10. All in about 1.5 hours.

Even got to play around with the compiz fusion for the first time (which took some tweaking...installing the compizconfig-settings-manager to get the advanced effects menu options etc...which I am not sure why that isn't installed by default).

Very nice, very slick and super happy and impressed by the "bulletproof-iness" in these extreme examples of having the system blown up.


Hats off to all the devs and folks posting help on the web etc.

Power to the people!

Cheers,
tragen

---

### Post by wPwLUi3N on 2008-04-03
Wow that's one big testimony :).

---

