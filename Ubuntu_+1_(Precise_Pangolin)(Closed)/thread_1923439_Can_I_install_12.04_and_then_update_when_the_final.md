---
title: "Can I install 12.04 and then update when the final comes out?"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ernestj on 2012-02-10
I tried the daily 12.04, WOW!! what a difference, it is great!! I want to upgrade to 12.04 alpha 2, can I do this now and then when the final comes out, the updates over time will equal the final release?

Thanks,
Ernie

---

### Post by nothingspecial on 2012-02-10
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

Yes you will update until you have the final release.

---

### Post by r9tysix on 2012-02-10
sorry i post this in wrong thread

---

### Post by savanna on 2012-02-10
Yes, and when the next release upgrade comes out, you'll be able to upgrade to the next version! Either using the gui tool or "apt-get dist-upgrade" at the command line.

---

### Post by ernestj on 2012-02-10
Thank you. I tried to upgrade 11.04 to 11.10 and it was a problem. I had to do a clean install of 11.10 to fix a whole mess of problems. But, I guess if I have the basics workings of 12.04, kernel and all, then there will only have to be updates to get the the final release.

---

### Post by jerrylamos on 2012-02-10
I've found a fresh install takes less hard disk space, or to say it another way, update after update after update hard disk usage goes up and up despite my efforts at autoremove, deleting old linux images & headers, etc.  If you don't mind a few hundred megabytes of left over junk then just stick with updates.

Since this is a development forum, I try installs from time to time because I get more reportable bugs that way.....

Jerry

---

### Post by brpylko on 2012-02-10
> **savanna said:**
> Yes, and when the next release upgrade comes out, you'll be able to upgrade to the next version! Either using the gui tool or "apt-get dist-upgrade" at the command line.

I wouldn't recommend upgrading through the command line. My friend tried to and screwed over his system and spent 2 or 3 days rolling it back before he then upgraded using a live CD.

So my $0.02 would be to use a 12.04 live CD to perform the upgrade.

---

### Post by jerrylamos on 2012-02-11
Can't use a "live CD" when as usual development images exceed CD capacity.  Maybe after release they might have it down to 700 MB, maybe not.

Solution see thread: "Alpha 2 ISO file too big" post #10 where I boot and install live directly from the .iso on the hard drive.  Saves time, don't have to write USB's or CD's or DVD's, and is faster.  And don't care how big the .iso is (well, if it gets into too many gigabytes).

Also, if running any "unstable development" ubuntu expect crashes and re-installs somewhere during A1, A2, B, even RC.  Don't want crashes?  Don't run "unstable development releases".

Me?  I learn a lot of linux from bugs and crashes....on test pc's or at least ones I have backed up.  I even had to reload Windoze....7 all four DVD's once on an Acer Aspire 5253 notebook when ocelot unstable totally borked the boot record while installing onto a USB hard drive.  I've learned a bunch since, like how to recover borked boot records.  Most of the time.  Oh, I don't run USB hard drives on that notebook but I do on this Acer Aspire 1 netbook.  It's happy, I'm happy.

Jerry

---

### Post by ranch hand on 2012-02-11
> **brpylko said:**
> I wouldn't recommend upgrading through the command line. My friend tried to and screwed over his system and spent 2 or 3 days rolling it back before he then upgraded using a live CD.

So my $0.02 would be to use a 12.04 live CD to perform the upgrade.
I upgraded for 4 dev cycles from version to version with no trouble.

If you start at the beginning of the dev cycle there is no way to upgrade other than the terminal.  You have to have an OS before you can make an image of it.   You have to have people using the OS so that someone knows when to test that first (A1) image.

I have never done a normal upgrade in any other way than using apt.  Works fine.  You do have to know exactly what you are doing.  The OS to be upgraded needs to be in the correct condition to upgrade as does the sources.list for that OS.

There is more to a version upgrade than just a dist-upgrade.  The next time you do an upgrade with UM, plan on being really bored and what the output for the whole thing.  You will see a long part of it is after all the upgrades are installed.  This is called "Clean Up".

This can be done in terminal too.

Upgrading with the Live CD is a great way to upgrade and even better if you are installed on 2 partitions, / (root) and /home.  I think it is one of the greatest advances in the installer ever.

---

### Post by Gregory Lee on 2012-02-11
> **nothingspecial said:**
> *Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

Yes you will update until you have the final release.
I've just installed 12.04 using the live/install CD, so does this mean, specifically, that if I run "apt-get update" from time to time, eventually I will wind up with a system equivalent to the release version of 12.04?

Or, will I have to upgrade, at some point, to get to a real 12.04.  (I would think not, because I already have a 12.04 version, but sometimes things don't work in the most obvious way.)

---

### Post by paul_in_london on 2012-02-11
> **Gregory Lee said:**
> I've just installed 12.04 using the live/install CD, so does this mean, specifically, that if I run "apt-get update" from time to time, eventually I will wind up with a system equivalent to the release version of 12.04?

Or, will I have to upgrade, at some point, to get to a real 12.04.  (I would think not, because I already have a 12.04 version, but sometimes things don't work in the most obvious way.)

Just keep updating/upgrading and you'll end up with the final release.

If you're using apt-get, run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If **apt-get dist-upgrade** wants to remove stuff and you're not sure, run:

```
sudo apt-get upgrade
```

instead.

I prefer **aptitude**. The equivalent commands are:

```
sudo aptitude update
``` and

```
sudo aptitude full-upgrade
``` or ```
sudo aptitude safe-upgrade
```

until any dependency issues are resolved.

---

### Post by Gregory Lee on 2012-02-11
> **paul_in_london said:**
> Just keep updating/upgrading and you'll end up with the final release.

If you're using apt-get, run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```If **apt-get dist-upgrade** wants to remove stuff and you're not sure, run:

```
sudo apt-get upgrade
```instead.


Thanks for the information.  I still am a little puzzled why I have to "upgrade" from my current 12.04 system.  Oh, well.

I did (as root)
```

apt-get update
apt-get dist-upgrade

```and got the message that 5 packages would be removed, including software-center and ubuntu-desktop, which didn't sound like a good thing, so I said 'n' to the dist-upgrade, and ran
```
apt-get upgrade
```instead.  I rebooted -- it still seems to be in working order.
I'll try the same sequence again, soon.

---

### Post by cariboo on 2012-02-11
Packages are being updated quite often right now, so you should be updating at least once a day if not more often.

---

### Post by ranch hand on 2012-02-11
You may also want to reinstall once the final release is really stable.  If you have had to do a lot of hacking to keep it running to that point it is the easiest way to clean it up.

If you are installed on 2 partitions this is easy to do and you do not loose any data in the /home partition (back up still a good idea) as long as you instruct the installer not to partition /home.

This is a dev release.  It probably will break.  Using it as your production OS is not a real good idea at this point.  It can be done but is best done after you have a couple of dev cycles under your belt.

---

### Post by paul_in_london on 2012-02-12
> **Gregory Lee said:**
> Thanks for the information.  I still am a little puzzled why I have to "upgrade" from my current 12.04 system.  Oh, well.

I did (as root)
```

apt-get update
apt-get dist-upgrade

```and got the message that 5 packages would be removed, including software-center and ubuntu-desktop, which didn't sound like a good thing, so I said 'n' to the dist-upgrade, and ran
```
apt-get upgrade
```instead.  I rebooted -- it still seems to be in working order.
I'll try the same sequence again, soon.

The "update" part basically downloads the latest package information from the repositories and the "upgrade" part downloads and installs any newer versions of your installed packages that may be available.

---

### Post by Gregory Lee on 2012-02-12
> **ranch hand said:**
> If you are installed on 2 partitions this is easy to do ,,,
I have 4 partitions, now, but when I first installed, the facility for choosing your own partitioning didn't seem to be working right.  I originally got just one large partition plus a small partition for swap.  So yesterday I booted up the live CD again and used GParted from there to shrink the one partition and add two others.

However, I hope to avoid reinstalling.

---

### Post by yacine on 2012-02-12
I have been using Ubuntu for quite some time... The new Alpha2 12.04 is the most stable I have ever installed! I am just amazed at how it works flowlessly! Looking forward to upgrading to the officially released version!
Thanks for the Ubuntu team and eveyone involved for this qulity distro!

---

### Post by jasonrisenburg on 2012-02-12
What I do is when alpha 2 comes out I upgrade, report as much as I can and it comes out pretty good. When the launch happens, I do a fresh ( I keep everything backed) install and play again.

---

### Post by Gregory Lee on 2012-02-12
After running "aptitude update" and "aptitude safe-upgrade" a number of times over the last day, I finally got from the update manager just now (noon on Sunday) the message "The software on this computer is up to date."  No more threats to remove programs, for now anyway.

---

### Post by paul_in_london on 2012-02-12
> **Gregory Lee said:**
> After running "aptitude update" and "aptitude safe-upgrade" a number of times over the last day, I finally got from the update manager just now (noon on Sunday) the message "The software on this computer is up to date."  No more threats to remove programs, for now anyway.

I don't bother with update manager at all. aptitude works just fine. If you do want to use a GUI, I'd suggest synaptic rather than update manager.

You might find it helpful to read this sticky:

[ubuntuforums.org/showthread.php?t=1859240](ubuntuforums.org/showthread.php?t=1859240)

---

### Post by Gregory Lee on 2012-02-12
> **paul_in_london said:**
> I don't bother with update manager at all. aptitude works just fine. If you do want to use a GUI, I'd suggest synaptic rather than update manager.

You might find it helpful to read this sticky:

[ubuntuforums.org/showthread.php?t=1859240]("http://ubuntuforums.org/showthread.php?t=1859240")
I did read the sticky, and I'm only using the terminal version of aptitude (though I used apt-get, at first).  I ran the update manager not to do any updates, but just to check whether I was up to date.  Before, it said I wasn't; now, it says I am.  I'm pleased with the progress.

---

### Post by paul_in_london on 2012-02-13
> **Gregory Lee said:**
> I did read the sticky, and I'm only using the terminal version of aptitude (though I used apt-get, at first).  I ran the update manager not to do any updates, but just to check whether I was up to date.  Before, it said I wasn't; now, it says I am.  I'm pleased with the progress.

Ok. As I say, you just need to be a bit careful (especially during the dev cycle) if **aptitude full-upgrade** wants to remove packages. When in doubt, use **aptitude safe-upgrade** instead.

---

### Post by philinux on 2012-02-13
> **paul_in_london said:**
> Ok. As I say, you just need to be a bit careful (especially during the dev cycle) if **aptitude full-upgrade** wants to remove packages. When in doubt, use **aptitude safe-upgrade** instead.

We should not really use aptitude in testing. See this thread and in particular the last two posts. [http://ubuntuforums.org/showthread.php?t=1881843]("http://ubuntuforums.org/showthread.php?t=1881843")

---

### Post by paul_in_london on 2012-02-13
> **philinux said:**
> We should not really use aptitude in testing. See this thread and in particular the last two posts. [http://ubuntuforums.org/showthread.php?t=1881843]("http://ubuntuforums.org/showthread.php?t=1881843")

Hmm. Thanks Phil. I didn't realise that **aptitude** is now in **universe** and hence not officially sanctioned. I was under the impression (must have read it somewhere at some point I suppose) that **aptitude** was recommended over **apt-get**. I note the last two posts from that thread you mentioned and take the point that **aptitude** and **apt-get** won't always resolve package dependencies consistently. I don't think it's a too much of a problem in practice as long as people are careful when allowing either tool to remove packages - perhaps, for example (as was suggested there), to compare the proposed actions of both before doing anything reckless. It's probably also worth mentioning that **synaptic** doesn't always offer the same dependency resolution as either **apt-get** or **aptitude**. *Caveat emptor* and all that.

So it seems you've had a change of heart since this post in the same thread?! :lolflag:

[ubuntuforums.org/showpost.php?p=11462410&postcount=15](ubuntuforums.org/showpost.php?p=11462410&postcount=15)

---

### Post by philinux on 2012-02-13
> **paul_in_london said:**
> Hmm. Thanks Phil. I didn't realise that **aptitude** is now in **universe** and hence not officially sanctioned. I was under the impression (must have read it somewhere at some point I suppose) that **aptitude** was recommended over **apt-get**. I note the last two posts from that thread you mentioned and take the point that **aptitude** and **apt-get** won't always resolve package dependencies consistently. I don't think it's a too much of a problem in practice as long as people are careful when allowing either tool to remove packages - perhaps, for example (as was suggested there), to compare the proposed actions of both before doing anything reckless. It's probably also worth mentioning that **synaptic** doesn't always offer the same dependency resolution as either **apt-get** or **aptitude**. *Caveat emptor* and all that.

So it seems you've had a change of heart since this post in the same thread?! :lolflag:

[ubuntuforums.org/showpost.php?p=11462410&postcount=15](ubuntuforums.org/showpost.php?p=11462410&postcount=15)

Oh yes. Live and Learn. Eh :P

---

### Post by paul_in_london on 2012-02-13
> **philinux said:**
> Oh yes. Live and Learn. Eh :P

And then we die and forget it all! :lolflag:

---

### Post by prusswan on 2012-02-13
Update manager actually warns me about partial upgrades, but apt-get tells me what exactly will be removed. 'Tis a hard choice

---

### Post by Gregory Lee on 2012-02-13
I've only used "aptitude update" and "aptitude safe-upgrade", as I said above (after switching from apt-get).  Except that I did run the upgrade manager a few times, just to see whether it would say it would say it would remove programs.  I've just done that all again, and again, the update manager says the software on this computer is up to date and there are no packages to install.  "aptitude safe-upgrade" has not offered to remove anything, but it wouldn't, of course, because of the "safe-" prefix.  And if it did, I wouldn't give it the go ahead to do that.

I did read the thread that mentioned why aptitude was not supplied as a default.  I didn't really see what the problem with it was supposed to be.  Nonetheless, of course I'll switch from aptitude back to apt-get, if you experts think I should.  I only used aptitude because earlier in this thread one of you said he preferred it.

---

### Post by cariboo on 2012-02-13
Aptitude is still officially sanctioned, it just isn't installed by default. My feeling is that if it's in the repositories, it should be used and tested.

---

### Post by Ibidem on 2012-02-13
> **prusswan said:**
> Update manager actually warns me about partial upgrades, but apt-get tells me what exactly will be removed. 'Tis a hard choice Aptitude warns about broken packages, lets you view them, AND lets you try to fix it (so if an upgrade breaks something, you can back out the part that breaks stuff while updating everything else). (If you use the CLI, press "e" when it asks what to do)

---

### Post by ojeezy on 2012-02-15
Just my one cent worth(upgrade to two maybe?): One thing I imagine would be necessary in addition to the dist-upgrade, etc...is that the repos for the final release would need to be in the sources.list as well. I've noticed there are particular sources for testing that I'm sure will be replaced in the final .iso. This might have already been mentioned but, you know, I had to throw my non-red hat into the mix!:P

---

