---
title: "Arch Linux and Ubuntu"
date: 2009-07-26
forum: Testimonials &amp; Experiences
---

### Post by Merc248 on 2009-07-26
So, I've recently decided to switch completely over to Linux after going back and forth between several distros, several versions of Windows, and Mac OS X.  I've initially tried to go with Gentoo Linux (which I've used a ton of times in the past), but after breaking the system and realizing that I needed another couple of hours to recompile *everything* from scratch, I decided to ditch Gentoo with one of my most favorite distros, Arch Linux.  It's extremely similar to Gentoo in terms of how minimal and how simple the system is setup, and I loved it for a while.  I've even installed Arch Linux on a separate partition on my MacBook Pro; I loved how much I could customize my installation compared to Mac OS X.

However, I wanted to run a few applications in wine, which didn't work all that well for me, since Arch Linux x86-64 is mostly a *pure* x86-64 bit system (that is, there are multilibs available, but they aren't installed by default, and they were added somewhat as an afterthought.)  I also had a number of other problems with 64-bit Flash, microstuttering in games, and a few other things.  Don't get me wrong, I love Arch Linux, and I still have it installed on my MacBook Pro, which I often use at my work.

I couldn't deal with not maximizing YouTube videos and having a ton of stuff break in 32-bit wine, so I've decided to go back to Ubuntu after a long hiatus.  And holy crap, I'm impressed by how much Ubuntu has improved from several years ago!  First of all, I'm impressed that Flash actually works in full screen (is it because Firefox + Flash are both 32-bit?), and that 32-bit wine works perfectly in 64-bit Ubuntu.  That, and I appreciate the little bits of patches that were applied on various things for better performance and whatnot.  After being on the rolling release model for a few months with Arch Linux, I'm also appreciating the fact that I can just download a specific version of Ubuntu, and expect it to *not break* after an update.

I'm probably going to stick with Ubuntu for a long while now, though I'm always still itching for heading back into CLI territory with Arch and Gentoo.

(For server applications, I always try to stick with RHEL 5.x / CentOS 5.x.  But I'd love to experiment with a Debian based server sometime...)

---

### Post by Dullstar on 2009-07-27
Does Ubuntu install on MacBooks and live side by side with Mac OS X?

Hope that'd work!

---

### Post by cariboo on 2009-07-27
@Dullstar

Macs are intel powered these days so almost any os will work. For more info on Ubuntu on apple check out the threads [here]("http://ubuntuforums.org/forumdisplay.php?f=328").

---

### Post by Dullstar on 2009-07-27
Please ignore the following:

**[SIZE="7"]W00T![/SIZE]**

Okay, over.

That would make the perfect laptop.  Combine the nice MacBook with Mac OS X, and you have a great computer.  Add Ubuntu to the mix (**don't replace Mac OS X**, just add Ubuntu on as another OS), and then you have an awesome computer!

---

### Post by ngsupb on 2009-07-27
yes, Ubuntu is awesome! It doesn't require Linux knowledge to set and configure it. 

Arch linux is hard to set up, but it works faster.

Have both of them. Testing Arch at the moment :P

---

### Post by ukripper on 2009-07-27
> **Merc248 said:**
> 
(For server applications, I always try to stick with RHEL 5.x / CentOS 5.x.  But I'd love to experiment with a Debian based server sometime...)

Debian and ubuntu based servers both are good . Ubuntu LTS server comes with 5 year updates-support.

---

### Post by SuperSonic4 on 2009-07-27
Go for both :D - each has their uses although I've not had any problems using *flashplugin* in Arch x86_64 but fair enough.

I prefer to keep my arch and try to iron out any problems :p

---

### Post by Merc248 on 2009-07-27
> **ukripper said:**
> Debian and ubuntu based servers both are good . Ubuntu LTS server comes with 5 year updates-support.

Aye.  If I could, I'd actually switch over to a Debian based server in a heartbeat; it's an absolute dream to configure compared to RHEL servers.  However, the university I work for has an RHEL satellite server configured PLUS free RHEL support, and so I have to stick with RHEL.  Plus, the applications I'm installing on an RHEL box I'm using is mostly only supported on RHEL (I'm configuring a box as a master node for a Beowulf cluster, which will be used for Bioinformatics stuff.)

Oh yeah, as for installing Linux and Mac OS X side by side: I had a number of troubles with installing Arch side by side with Mac OS X, mostly with getting the damn installation to boot up.  I haven't quite looked into how Ubuntu partitions the hard drive (I forgot if it uses LVM or not), so Ubuntu might work flawlessly with a Mac OS X system with no other operating systems installed.

QUICK SIDENOTE: I think a lot of it had to do with EFI + MBR resyncing and the number of partitions that MBR allows; I had two partitions for EFI boot partition + Mac OS X, and initially another three for /boot + root + swap for Arch Linux.  MBR only allows for four primary partitions while EFI, I believe, allows for a lot more than four primary partitions.  This caused a lot of problems, namely with the boot loader (rEFIt) hanging on the Linux Penguin logo.  Workaround: combine /boot + root together on a single partition.  Probably an even better solution is to simply create an LVM partition, with everything (except swap) in a single logical volume.

In any case, I'd keep Mac OS X on the hard drive anyway, mostly for Firmware updates and the like.

---

### Post by Dullstar on 2009-07-29
I'm going to have to ask.  Why remove Mac OS X from the hard drive in the first place?!

---

### Post by Merc248 on 2009-07-29
If you really hate Mac OS X, for instance. :)

I'm of the opinion that Mac OS X is a desktop UNIX done right.  It's just that I'd rather have options when it comes to the GUI and whatnot, and Linux distros give me that option.  Plus, Mac OS X was getting a little long in the tooth for me TBH, I had it installed on my PC for a bit at the same time, and ended up nuking that installation in favor for Linux.

---

