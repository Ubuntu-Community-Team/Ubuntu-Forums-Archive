---
title: "A feisty lament for premature upgrades"
date: 2007-03-19
forum: System76 Support
---

### Post by Kaloma on 2007-03-19
Okay, I should have learned my lesson a long time ago, but I can't help myself sometimes. I decided I really wanted to have Blender 2.43 (for all its exciting new features) and Mail-Notification 4 (to solve the weird CPU-eating bug of v.3).

Then I figured, "oh, what the heck... Feisty beta is about to be released, and I don't see anything that causes concern on the outstanding bugs list" and I decided to upgrade everything.

The final result: I nearly hosed my Serval.  Okay, slight exaggeration, but several things are now broken.

For starters, disk management has gone haywire.  I can no longer boot the Edgy kernels (which I left installed, thinking it gave me added safety), because they can't seem to find the root partition on my SATA disk anymore.  The 'Disks' application I also find that I (that is, my non-root user) can no play audio CD's, the explanation being
> Sound Juicer could not access the CD-ROM device '/dev/scd0'
Reason: Permission denied".
Data discs work fine.  During the upgrades, the *mdadm* package asked which MD arrays are needed for the root filesystem, and I just left the default value of 'all' since I didn't know otherwise.  Could this be the source of the problem?

Besides those hiccups, *network-manager* was no longer playing nice with my wireless network, just endlessly trying to connect.  After down-grading *network-manager* and *network-manager-gnome* back to Edgy, things seem to be working again.

Even more tragically, my beautiful Compiz desktop is no more.  At least on my hardware configuration, Feisty's *desktop-effects* support is pitiful; *compiz* just crashes.  Even after trying to restore all compiz packages back to the version I had before the upgrade (which were not Edgy, but rather the latest from FreeDesktop.org's gandalf repository) I still can't get it back to proper working condition.  Very sad.

There were one or two other minor issues (such as the latest Feisty version of *gnucash* having a broken dependency).

Anyhow, I though I'd inquire about whether anyone else here has some insight into one or more of these problems.  Primarily, I'd like to get audio CDs working again.  Then I'd like to restore my GLX desktop.

I guess I should have restrained myself this time.

Thanks,
Matthew

---

### Post by patrickfromspain on 2007-03-19
My tip: download the latest daily live and do a fresh install, then install beryl.

---

### Post by Kaloma on 2007-03-20
Well, it turns out that I have compiz and most of the plugins working again (I guess the settings just got messed up during the upgrade).  However, window borders are missing and in general compiz seems unstable.

Just out of curiousity, what effects are possible with the latest Beryl on Ubuntu?

With Compiz, I had the following working beautifully:
[LIST]
[*]cube w/skydome
[*]plane
[*]wobbly
[*]opacity (and copacity)
[*]zoom
[*]annotate
[*]water and rain (including wiper effect)
[*]all animations (fire w/smoke, dream, sidekick, beam up, magic lamp, etc.)
[*]states (different properties for different window types/applications)
[*]scale (like expose')
[*]3D windows during cube rotate
[*]animated show desktop
[/LIST]

Is Beryl's feature set basically the same, or comparable? (For the latest Ubuntu build, that is.)

Thanks for the suggestion, I may try it, whether or not I get my Metacity themes working under compiz.

Matthew

P.S. In your opinion, what are the reasons for choosing Beryl over Compiz?

---

### Post by voidmage on 2007-03-20
Beryl's feature set is basically the same, but I run SVN right now and have this great plugin, much better than cube, IMO:
[http://www.youtube.com/watch?v=6TM7N6JKEvw](http://www.youtube.com/watch?v=6TM7N6JKEvw)

---

### Post by Kaloma on 2007-03-20
Well, thanks for giving me just the tiny nudge I needed to finally give Beryl a try.  That wall plugin looks quite slick.

Wow! Unless I missed something, Beryl Manager + Beryl Settings Manager is light-years ahead of what its equivalent for Compiz.  (I previously used the latest Gnome Compiz Manager, which I liked, from the gandalf repository.)

Interestingly, after installing Beryl, I can now get Compiz working without a hitch.  I can't explain that one.

I have to say I much prefer Beryl already.  As mentioned above, the settings manager is truly empowering and easy to use.  Furthermore, the plugins available (at least, comparing the packages I have installed) are more varied and refined than for Compiz.  E.g., I never had control over the thickness of my 3D windows before, and with beveled corners! And, I now have a transparent cube! Fantastic!

Now if I can just get my audio CDs playing again...

Matthew

---

### Post by macogw on 2007-03-22
Check and see if your cd drive is properly called /dev/scd0.  Mine is /dev/hda (cuz it's IDE) and my hard drive is /dev/sda.

---

### Post by Kaloma on 2007-03-22
Good thought!  (I hadn't even look further into this one, yet.)

I have no /dev/sdc at all!  Nor do I have any hd* devices under /dev.  My drive appears to be /dev/cdrom and /dev/cdrw. Like I mentioned above, data CD's no problem, just audio discs (and maybe VCD/DVD, I haven't tried movies yet).  I haven't changed anything manually, just upgraded, so I am surprised about this problem.

I don't know why applications (SoundJuicer, Totem) are looking for /dev/sdc0 when I pop in an audio disc.  Should I have sdc0 under /dev?

Matthew

---

### Post by Nighto on 2007-03-22
you may try to link then, as

```
sudo ln -s /dev/cdrom /dev/scd0
```

not the best solution, but might fix it.

---

### Post by Kaloma on 2007-03-27
Well, I have the CD problem solved, or at least I have a workaround.

First of all, I must have typed sdc0 instead of scd0 when I was investigating, because the node IS present.  It turns out that the problem is the group for /dev/scd0 was changed to floppy with the Feisty upgrade.  Others have already filed a bug against this, but it seems not to be a high priority over there.  Perhaps because there are simple workarounds, such as adding users to group floppy or modifying the udev rules (see [Bug #75753 for more).]("https://launchpad.net/ubuntu/+source/udev/+bug/75753")

Thanks for the help, everyone! Now only the network manager issue remains.  But I can work around that for now too.

Matthew

---

### Post by Kaloma on 2007-03-31
This will be my last post to this thread, but I thought some of you might like to know about the status of the Network Manager issue, since you may want to upgrade to Feisty when officially released and may also have the Intel 3945 wireless card in your machine.

The news is that the latest upgrade of the *libnm* packages (also *network-manager* and *network-manager-gnome*) fixes the issue.  No more mysterious infinite loop while trying to connect to a wireless network.  Needless to say, I am thrilled, and anyone interested in upgrading to Feisty when it is officially released should know that this issue is not a concern any longer (though stranger things than re-introduced bugs have been known to happen before a release ships).

Signing off,
Matthew

---

