---
title: "Will ubuntu focus on ease-of-use?"
date: 2004-10-15
forum: The Cafe
---

### Post by dmanderzen on 2004-10-15
The Linux industry-community has a tendency to get focused on computers for computers'  sake, and often loses site of the fact that for a lot of us the computer is a tool to make the rest of our life easier.  I remember when I first installed Linux 4 years ago installing a Quicken- like application turned into a nightmare of packages, libraries, and dependencies. I spent hours so I could save a few minutes a week .After 4 years, software installation is finally beginning to make some sense.   My latest pet peeve is the difficulty of importing certain addressbooks to certain applications (Evolution, T-bird, KMail, OO, etc.). There are a few exceptions, but about the best you can hope for is to search deep in your file system to look for the table to export.  At worst, and commonly, it won't work at all.  This isn't complicated functionality, and it seems ridiculous that  we're still dealing with it.
One of the many great features of BeOS (RIP) was a "People" file, a common file that would be used by all of your applications with addressbooks.   I'm not sure if the same thing could be applied in a Linux distribution, but compared to our current state, there's gotta be a better way.  The enthusiasm of the Ubuntu community is encouraging and infectious, I think it would be great if some of  it could be channeled to solving some of the basic weaknesses of current LInux.

---

### Post by Infatuated_iPod on 2004-10-20
I agree, i dont want linux distro's to hold my hand during every step like windows does, but if  things could be a little less complicated. It would be alot easier for all of us. Especially people new to linux like myself.

---

### Post by daniels on 2004-10-22
We are absolutely focussing on ease of use.  You'll notice that we don't ship a stock GNOME 2.8; we have made many of our own custom tweaks as we feel that'll give an easier-to-use desktop for the greatest common factor.  The installer is designed to be as easy to use as possible, and we've been running through installs and uses endlessly, seeking not only bugs but anything that's not intuitive and easy to use.

We've got a desktop development team as well, and we're all totally committed to ease of use.  After all, if it's not accessible, who's going to use it?

---

### Post by renato on 2004-10-22
Install is easy, but please when partitioning remove the "wipe whole disc" which is the default setting. That may be very scary:-)

---

### Post by daniels on 2004-10-22
It is, however, the best for the default case.  People who don't know what a swap partition is, let alone how large they should make it, and whether they want ext3, JFS, XFS, or what.  As someone who's used to doing his own intricate partition setups, I initially baulked at it, then I imagined handing my mum an Ubuntu CD.

---

### Post by elwis on 2004-10-22
Alright, alright! I'm an old SuSE user.. but if you have the time, take a look at the now GPL'ed Yast2.
If you will ever build a "control panel", that's were to start. Yast2 is still the very best configuration tool I've seen in the Linux world. You could actually, as a windoze-newbie, configure most of the things with simple mouseclicks.
(be it Deskltop settings or Samba/NFS client/server )

Yep, i know, I like it, it's a nice way to get going quickly before you learn to master the "noble art of hacking conf files"

---

### Post by cseg on 2004-10-22
[quote=renato]please when partitioning remove the "wipe whole disc" which is the default setting. That may be very scary:-)[/quote]So I'll keep harping on this:  I would love to see a Usibility Forum here where topics like this can be discussed more thoroughly.

Speaking of installation, the cursor really needs to advance automatically when going through the partition steps.  

That is, when you first select a partition to edit, the cursor is on a field something like "not used".  That's fine.  Then you press return and it gives you a list of (what was it? maybe) filing sytem types.  Of course, the one that is selected by default should be the natural choice.  At any rate, you select one, then press return.  

HERE is where the cursor should have advanced to the next option.  Instead, you have to cursor down yourself.  Again, you press return to enter the window for the next option list.  You make your selection (hopefully the default selection is sensible or preferred choice), then press return.

HERE again is where the cursor should have been advanced for you to the next field.

With properly selected (conservative) defaults and properly advancing cursor, the partitioning process can be reduced to something like:  RETURN-RETURN-RETURN-RETURN-RETURN-RETURN-RETURN-RETURN

Instead, you have to move the cursor around, each time you move it, your anxiety goes UP a little because your not 100% sure if that's the right place to go and you certainly don't want to trash your hard disk.

By always placing the cursor on a reasonable/conservative/noobie default, the user can just /confirm/ the selection by pressing RETURN and anxiety goes DOWN because you're feeling like you're doing the right thing and the wizard is guiding you through safely.

That's the only part of the installation process that I felt could be more streamlined.  The partitioning section is also jarring because every OTHER part of the installation IS just: RETURN-RETURN-RETURN-RETURN-RETURN-RETURN-RETURN-RETURN

But when you get to the partitioning section, you're thrown into a UI which is not familiar, with choices that you may not 100% understand, and you're required to explore around to see if options are what you think they are.

With proper noobie defaults and cursor positioning, a noobie should be able to RETURN-RETURN-RETURN through the partitioning section and produce a resonably partitioned system.  

Of course, that last screen which asks you if you really want to write these changes to disk is absolutely needed as a final failsafe agains trashing you system.  I would only add a list of the things you are about to change.  For example, if your system already has three partitions, but you are only changing one, then changes you are about to apply to that one partition should be listed so you can confirm them before you select YES.

If you have a more complex system or you have more experience, you can obviously deviate from the RETURN-RETURN-RETURN happy path.  This is no different from what you can do now.

The problem is that right now there are too many choices and there really is no "happy path" through the partitioning section and there should be.

And by the way, have I mentioned that I'd love to see a Usibility Forum here where topics like this can be discussed in more depth?

---

### Post by Sorin Paliga on 2004-10-22
Hello,

As a constant MAC OS user, I installed the ppc version on my iMac G3. works OK, installation without any problem (together wth MAC OS X on another partition, and Ext2 mounting the Ubuntu parition in the Finder). As posted under the ppc section, not solved the easy use of one-button mouse, so common with macs. Beside that, well, MAC OS X desktop has a lot to offer. I am mainly interested in foreign language teaching and linguistics. Adding keyboard layouts still is NOT a trivial thing (in MAC OS there is a long and developing passion for such keylayouts, many of them are better made than the default ones; I am one of those fans).
Gucharmap is installed by default, yet there is no Keyboard Viewer (formerly labelled Key Caps).
As far as ease of use is really in view, MAC OS experience would be good, for sure. Frankly, to date no Linux distro may possibly challenge MAC OS X, so if a ppc version is there, well this a challenge in itself! Otherwise, to be frank again, congratulations: Ubuntu ppc is INDEED a very good Linux distro; and the first one which installs and runs without any problem on my iMac (tested Debian proper; Mandrake 9 and Yellow Dog 3; is there any not tested?).

---

### Post by tanari on 2004-10-24
I like ubuntu, it is Ease of use, but some things must be better: now it is not ease to install media codecs and i can't compile many programms (have many errors).

Thank you for Ubuntu, it is very good distro. From all distros I like only 2 ubuntu and yoper :).

---

