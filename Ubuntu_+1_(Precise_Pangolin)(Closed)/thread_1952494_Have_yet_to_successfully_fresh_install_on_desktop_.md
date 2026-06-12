---
title: "Have yet to successfully fresh install on desktop amd64"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-04-04
So far I have yet to be able to fresh install the desktop amd64 iso.  Partman crashes after the 'Preparing to install Ubuntu' screen every time.

The first time -- with Precise Beta 1 22/03/12 -- I reported this (bug# 962455) the apport retrace failed with outdated debug symbol packages (I reported that as bug# 962479). Seems that no further effort's being made with either report.
The second time -- with Precise Beta 2 26/03/12 -- I reported this again (bug# 965719) in the hopes that the outdated debug symbol packages bug with apport retracing had been fixed :)  That would be a negative.
Hopefully this third time -- with Precise Beta 2 04/04/12 -- bug# 973450 will be the charm.

These crashes are probably related to fakeraid even though I'm not trying to install to the fakeraid array anyway (not that it gets far enough to even ask me).

I did link these to the iso tracker.

---

### Post by NHclimber on 2012-04-04
> **NHclimber said:**
> Hopefully this third time -- with Precise Beta 2 04/04/12 -- bug# 973450 will be the charm.
Nope - apport retracing service still complains about outdated debug symbol packages and bails on the stack backtrace. I think this happens for the same reason that 'partial upgrades' happen -- the archive already has a newer version of the package. There has to be a better way to update the archive -- like some kind of 'shadow' that's swapped en masse.

My favorite 'feature' is that it then marks the bug as invalid - hahaha. That's one way to keep the bug count down...

For quick reference:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450)

---

### Post by bcarlowise on 2012-04-05
I had the same thing happen to me but was able to successfully complete an install when I made sure the option to install 3rd Party software was UN-selected. I typically select that by default during installs but I noticed, starting with Beta 1, that selecting that option would cause the install to fail during disk partitioning. Try doing an install without it selected and see if the install completes.

---

### Post by 2F4U on 2012-04-05
I did a successful install from the amd64 iso with the third party apps selected. It crashed in the manual partitioning screen but allowed me to continue after selecting cancel. There seemed to be no obvious drawback from my crash.

---

### Post by NHclimber on 2012-04-05
Thank you both for the suggestions.  I did try both options with no luck.

This is actually a crash in partman-server and I never see the full-disk/side-by-side/something else screen.

---

### Post by cariboo on 2012-04-05
Have you tried the alternate iso?

---

### Post by NHclimber on 2012-04-05
> **cariboo907 said:**
> Have you tried the alternate iso?

I think you were reading my mind ;)

The longer story is this:
When the first 'fresh install' failed (back on the 22/03/12 Beta 1), it actually produced a bunch of crashing bugs all at once:  one in gnome-settings-daemon, one in partman-server and one in whoopsie.
After spending a while filling out all the Launchpad bugs, I figured maybe the partman-server crashing was related to fakeraid.

So I tried the alternate iso. It hung at the corresponding location -- with no indication of crash. I did not file a bug for that. I have not tried the alternate iso since.

After bcarlowise and 2F4U suggested messes with options, I thought 'maybe I should retry the alternate iso and file that bug if it hangs this time' and then you messaged. Sign from the Goddess Computa, that.

---

### Post by NHclimber on 2012-04-06
The alternate iso 'hangs' at the first screen after selecting 'Install Ubuntu'. By 'hang', I mean won't accept any input -- I think this may be keyboard related. I'm going to mess around with a wired keyboard in a little bit to see if that's true.

More info: at the initial popup keyboard layout, I can select English. Then if I select 'Install Ubuntu', the keyboard selection that comes up is non-responsive. Alternatively, if I first enable 'Expert' mode then select 'Install Ubuntu', the expert installer menu that comes up is non-responsive.

I have to 'hard' power-off.

[edit]

Looks like maybe this was previously known but never found... [http://ubuntuforums.org/showthread.php?t=1754632](http://ubuntuforums.org/showthread.php?t=1754632)

---

### Post by NHclimber on 2012-04-06
<sigh>

The alternate iso does not have the hid-logitech-dj driver so no support for wireless keyboards that use the Logitech unifying receiver.  [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198)

With a wired keyboard, I was able to get to the partitioner (so the chain of partman-server bugs is probably due to some interaction with ubiquity).

Unfortunately, partman really wants to format the swap area on the fakeraid array (why??) and fails. Going to try again without enabling raid and see what happens.

---

### Post by NHclimber on 2012-04-06
Well, I did finally get a fresh install from the alternate iso.

I had to use a wired keyboard.

TBH, I'm not exactly sure what I did right to finally get past the partitioner.  It's pretty scary because it really really really wants to format swap space no matter where that swap space is and there is no way to turn it off.

As I said, my first pass through I enabled the fakeraid. There is a swap partition on the fakeraid. So finally I gave up and said ok to the various partition changes.  This gave me an error and bumped me back to the manual partitioning screen. I promptly aborted the installation.

Second time through, I *did not* enable the fakeraid -- but it came up anyway and the partitioner still wanted to format the swap space. So I went back and enabled the fakeraid, and then said ok to the various partition changes and it worked. What's scary about this is the raid name is totally wrong - it's something like raid#126 not /dev/mapper/isw_cbdbfhdjad_Raid0.

When it wanted to install the bootloader, none is not an option so I backspaced over the suggested location and continued with a blank installation location name.  Not even an error!  Whatever....

Then I boot back to my stable oneiric install and ran 'update-grub2' from there to discover the new install and boot on to it.

As much as I want to mark this thread solved, 'successfully' is not really the adverb that comes to mind ;)

I say we pitch in together and give every ubuntu / grub2 developer *only* a fakeraid or real raid SMP machine with a wireless keyboard and a UPS and get these ridiculous anachronisms addressed.

---

