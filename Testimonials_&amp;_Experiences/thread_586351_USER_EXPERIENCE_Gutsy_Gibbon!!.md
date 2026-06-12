---
title: "USER EXPERIENCE: Gutsy Gibbon!!"
date: 2007-10-22
forum: Testimonials &amp; Experiences
---

### Post by takuhii on 2007-10-22
So I'm, chuffed to bits when Update Manager offers me an upgrade to Gutsy, oh how my troubles had just begun.

The update went fairly smoothly, the thrid time around, as what was not mentioned was that I had to disable ALL my third-party plugins, and remove anything non-standard (AWN!!).

A few files failed on the third attempt, due to my repositories not being of Gutsy origin (already disabled, Kimosabe!!).

Reboot the PC to find everything working... or so I thought...
I have two NEW repositories called UNSUPPORTED SOFTWARE, all my FEISTY repos are still there, but there are no GUTSY repos. AWN won't fire up and Compiz-Fusion refuses to acknowledge my existance also.

Removed COMPIZ and rebooted, REMOVED AWN and rebooted. Re-installed COMPIZ, REBOOTED, Compiz still refuses to boot, it want LIBWNCK-1.18.so, which is now depracated and replaced by LIBWNCK-1.22.so. No matter what I do Compiz want the latest version of LIBWNCK!!

I have now added the correct Gutsy repos, removed all reference to FEISTY, and Compiz still doesn't want ot play ball.

At this moment in time, backin up the PC and starting again from scratch is out of the question, as all I have is a stack of blank DVDs and NAUTILUS to drag and drop into the CD/DVD Creator window. With a 25GB music collection (ALL Legal I might add!!!) and 40GB of downloads and home-videos to backup, this is going to be a lengthy task...

The short of it is however, that I had to totally start from scratch. COMPIZ refused to re-install correctly (it ran, but I couldn't tweak it) without thinking it was under FEISTY, AWN ran, like a sack of spanners. so I backed up my data (it took FOREVER), downloaded the GUTSY ISO, and started again...

Which was nice.

---

### Post by realvz on 2007-10-22
Well.. i am sorry you faced issues while upgrading...but Hey...
All's well that ends well...

you will enjoy GUTSY and forget about all these issues in a snap..

---

### Post by lonesomecrow on 2007-10-22
I feel sorry for you bro I really do! I read about all these issues when you upgrade to a newer version, and if it wasn't because the servers just were packed and wasn't able to upgrade, then I would be running in a lot more problems, so I just went and did a clean install!!

---

### Post by mxsteini on 2007-10-22
today I installed gutsy on my sparedisk an my laptop.
samsung P35 

The installation was realy good (<30min).
But after rebooting:
The display turn from light to dark an back.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/145131]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/145131")

My sd-card was not automounting from my extenal usb-careader. Same as feisty

Than I tried to install my second monitor.
After 40 minutes trying radeon, ati, opensource, and restricted driver I gave up.:confused:
I didn't got it working. ](*,)

So, I'm happy that I have a sparedisk. I can go back to my working system.

So, do not install 7.10 on your only systemdisk. Test it on a sparedisk.

---

### Post by conehead77 on 2007-10-22
ouch!

Make a separate /home partition where you store all your data. If you need to make a fresh install then, the /home directory wont be touched (but be sure NOT to select "guided-use entire harddisk" on install ;) )

---

### Post by R_U_Q_R_U on 2007-10-22
> **takuhii said:**
> So I'm, chuffed to bits when Update Manager offers me an upgrade to Gutsy, oh how my troubles had just begun...
Removed COMPIZ and rebooted, REMOVED AWN and rebooted. Re-installed COMPIZ, REBOOTED, Compiz still refuses to boot, ...

Just asking...why did you have to re-install COMPIZ? Is it not built into Gutsy? I did a clean install of Gutsy on a Dell D600 and all the Compiz effects worked fine.

---

### Post by petersjm on 2007-10-22
Everything worked fine for me. I have /home on a spare partition. Downloaded the ISO and installed. Only thing that didn't work was usplash, but I fixed that with a minor tweak. Only thing I don't like about a fresh install is having to reinstall all my apps. But other than that, everything went great. Compiz worked out of the box, too.

---

### Post by mxsteini on 2007-10-22
@conehead77
using a separate /home-Partition is recomended for me. This is one of the vantages of un*x-systems. I'm using this 15 years. It is really untouched by the installationporcedur. 

But if you don't use a sparedisk like I wrote above you can't go back to feisty.

BTW:
On  my next installation I wil have a /home and a /data partition.
The /data is for none-backuped-data like ogg and images.

---

### Post by takuhii on 2007-10-24
> **R_U_Q_R_U said:**
> Just asking...why did you have to re-install COMPIZ? Is it not built into Gutsy? I did a clean install of Gutsy on a Dell D600 and all the Compiz effects worked fine.

I "re-installed" Compiz becuase it was working with the old Feisty file, and refusing the load properly, So I removed it and re-installed it (it still insisted on using the Feisty repos for some reason)...

---

### Post by P4man on 2007-10-24
Upgrading to Gutsy is the biggest mistake I made recently. Feisty worked fine for more, upgrading to Gutsy broke my X and failsafe X kept messing up my xorg.conf. finally ended up reinstalling from scratch only to find out Gutsy locks up more frequently than windows 3.11. I'm not even kidding. Hard freezes several times per day, not even Windows ME did that. Boot times went up considerably, internet browsing became intolerably slow.

Many of these issues I have solved now, but my  "ou of the box experience" for Gutsy was really horrible. This hurts double as I convinced many friends to move to Ubuntu.. now I'm begging them not to upgrade yet. In many ways I see Gutsy compares to Feisty (or even Edgy) as Vista to XP.

---

### Post by armandh on 2007-10-24
that is what the spare HDDs are for....testing
anyone who tests on a mission critical machime can match the folks at chernoble for balls



> **mxsteini said:**
> today I installed gutsy on my sparedisk an my laptop.
samsung P35 

The installation was realy good (<30min).
But after rebooting:
The display turn from light to dark an back.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/145131]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/145131")

My sd-card was not automounting from my extenal usb-careader. Same as feisty

Than I tried to install my second monitor.
After 40 minutes trying radeon, ati, opensource, and restricted driver I gave up.:confused:
I didn't got it working. ](*,)

So, I'm happy that I have a sparedisk. I can go back to my working system.

So, do not install 7.10 on your only systemdisk. Test it on a sparedisk.

---

