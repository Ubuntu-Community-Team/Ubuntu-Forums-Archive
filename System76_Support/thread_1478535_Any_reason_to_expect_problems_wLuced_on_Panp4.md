---
title: "Any reason to expect problems w/Luced on Panp4?"
date: 2010-05-09
forum: System76 Support
---

### Post by ResumeMan on 2010-05-09
So I bought a Pangolin about  a year and a half ago. Haven't upgraded from the pre-installed Ubuntu 8.10. It's starting to act a bit wonky (most notably suspend seems to mostly not work any more). I figured that since the OS is officially not supported I ought to just upgrade to the latest and greatest, and then if something doesn't work I can complain with a clear conscience :).

So would I be able to expect that everything should go smoothly if I serially upgraded using the auto-updater? Or is that asking for trouble and should I just do a fresh install?

And has anyone installed Lucid on a Pangolin of this vintage? Any reason to expect that there could be an issue with any of its hardware once I install and run the S76 driver? I just don't want to walk into any trouble...

My machine's specs are below for reference.

```
Pangolin Performance (PAN-P4)
       Operating System Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
       Display Resolution 15.4" WXGA Super Clear Glossy LCD (1280 x 800)
       Processor Core 2 Duo P8400 2.26 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Hard Drive 320 GB 5400 RPM SATA II
       Optical Drive CD-RW / DVD-RW
       Wireless 802.11 agn
       Bluetooth Bluetooth
```

---

### Post by marshmallow1304 on 2010-05-10
I would be reluctant to upgrade 8.10->9.04->9.10->10.04.  While I've heard of successful similar upgrades, it leaves a lot of room for something to go wrong.  Backing up and doing a fresh install is much more advisable.

---

### Post by thomasaaron on 2010-05-10
+1. Good advice.

---

### Post by silvertuna on 2010-05-10
I have the same vintage system and did a fresh install for Karmic to solve the problems created by merely upgrading.  This time around i will do a fresh install but want to create a separate Home partition to streamline the process.

Will there be any issues doing this on the Pan4? And can someone direct me to the best guide for creating a separate Home partition on the Pan4? 

silvertuna

---

### Post by bill516 on 2010-05-10
I agree that a fresh installation is what you want to do.  Coming from 8.10 you are going to see a different Ubuntu.  Hope you like Popsicle Purple.

You should have no trouble installing with a separate home partition.  Here is one link that explains a way to do it.

[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html")

There is also a nice explanation over on the Psychocats site.  Suffice it to say that when I used it, it worked just fine.  Worth taking a look.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

May I emphasize one thing?  Before you do ANYTHING back up your data files and do not forget your browser bookmarks!

If you make a mistake with your operating system you can always fix that.  No mistake is fatal, really.

But lost data is lost data.  So make a backup and check it to make sure it is both complete and readable.

My PanP4 is just a bit newer than yours, perhaps, but it has no trouble with 10.04 at all.

---

### Post by isantop on 2010-05-10
There are some Panp4's with Nvidia cards and some with intel cards, but either one should run Lucid just fine. I wouldn't worry about it too much.

It wouldn't hurt to pop in a LiveCD to test out your hardware first. Some things may be fine, but if you get any problems here, you'll know without messing up your system.

I would definitely install cleanly from 8.10. 8.04 would be one thing, but even in that case, I'd probably just install. Then again, I don't think I've ever used the upgrade tool.

Like I said, a LiveCD would be a good thing to test on.

---

### Post by betrunkenaffe on 2010-05-11
I have panp4, pretty sure same one as you (I have nVidia gfx), been running Lucid for days now without any major concerns.

In fact, this is the first Ubuntu since 8.10 that everything seems to just work.

Highly recommend fresh install (upgrades fail too often imo) and always keep a /home partition. Backing up as suggested is always advisable.

The only issue I've ran into is a known bug that system76 cannot fix which is that the boot screen splash screen is a terrible resolution when using proprietary drivers.

---

### Post by jml on 2010-05-11
Since you are planning for a clean install, once you download and burn the 10.04 disc, boot it up as a live CD first and make sure that there are no outstanding issues.  That way there will be no post install suprises.

Joe

---

### Post by ResumeMan on 2010-05-11
OK thanks, looks like fresh install it is. I'll try the live cd first too.

> **silvertuna said:**
>  This time around i will do a fresh install but want to create a separate Home partition to streamline the process.

Am I mistaken that this computer already has a separate /home partition? That was my understanding, and also appears to be the case when I run Gparted. That said, partitions ain't my strong suit.

There's a 14 gig partition mounted on /,/dev/.static.dev (or something like that), a swap partition and a 280 gig partition mounted on /home. So I should be able to just tell the installer to install on the first partition, right?

---

### Post by bill516 on 2010-05-12
OK, you are ahead of where I thought you were, since you apparently already have a home partition.  If so good, we'll use it.  But let's check.

Is GParted is showing you something like:

/ on sda1 ? (probably flagged bootable)

/home on sda2 ?

swap on sda3 ?

/ will be something on the order of 10 to 20 Gigabytes?

/home will be the largest of these partitions.  If you have a 320 Gig HD it is a big monster.

swap will be equal to or larger than your installed RAM?

Correct so far?  If not report back.

OK, let's keep this as simple as we can.

You have backed up your data, right?  Do not skip that step!

Now, if you have no other distro on that machine you have choices.

1.  You can just tell the 10.4 installer to use the entire disk and it is going to do just that.  Potential problem:  I do not know if it does a /home partition by default.  So you do need to check and see what it proposes to do.

I think the second choice below is best because you specify what the installer is going to do.

2.  You can select the "advanced" choice when you get to the partitioner.  Then you instruct it to put / on sda1, put /home on sda2 and put swap on sda3.  Select the ext4 file system, which is the default.  There is no problem with it.

At this point the installer will reformat your existing sda1 and sda2 partitions, then install the new Ubuntu 10.4 / on sda1 and /home on sda2.  Since swap on sda3 will remain as swap the installer probably will need to do nothing with it.

Next you have to go out to the System 76 website and follow the instructions there for getting your updated System 76 driver.

After that put your data files back on, put your bookmarks on the new Firefox and away you go!

Just one thing.  When you reload your data files don't put those old 8.10 configuration files back on.  You don't need them and they just clutter the landscape.

I liked 8.10 a lot.  I still like it in fact.  But done is done.  So I have to upgrade one desktop machine here this week. I will be doing a variant of what you are doing.  If 10.04 runs as well as 8.10 we have a winner!

Except for that Grape Popsicle color which Ars Technica calls "aubergine".  I think that is French for eggplant?  We shoud run an eggplant? :confused:

---

### Post by ResumeMan on 2010-05-20
Hi, hadn't checked this thread in awhile.

What I have is close to what you describe.

/dev/sda1 has the mount point /,/dev/.static.dev - 14 GB
/dev/sda2 has the linux-swap filesystem and no mountpoint - 3.5 GB
/dev/sda3 has the mount point /home - 280 GB

So what I'd really prefer to do is to just leave the /home partition alone and just install the OS on the /dev/sda1 partition. Can I do that? And if so can I leave /sda3 as ext3 and format /dev/sda1 as ext4?

I don't have a whole lot of important data on this machine; I keep all my music, docs, etc., on a separate file server machine. But I do have bits and pieces scattered thru the /home directory that I'd rather not chase down and replace. If something went wrong and I had to erase it all, que sera sera...

Anyhow, is that possible? Can I just tell Lucid to install itself on that one partition and leave the /home one alone?

---

### Post by betrunkenaffe on 2010-05-20
That's pretty much what I have.

/dev/sda1 - /dos - ntfs (Windows)
/dev/sda2 - / - ext4
/dev/sda3 - /home - ext3
/dev/sda4 - swap

And I never format sda3, only the others. Also, if you keep your username the same then all your personal settings will still work after the reinstall.

---

### Post by bgreenaway on 2010-05-20
On my PanP4, I had some problems with the resolution of the splash screen, but this was resolved after applying a solution I found in the forums. It appears to be a problem relating to NVidia as I did not experience the same problem on a desktop using an Intel chipset.

Apart from, that I did an install from scratch after backing up my home folder. Everything worked fine.

---

### Post by ResumeMan on 2010-06-15
So just to round out this topic, I did a clean install 3 weeks ago and everything's working perfectly.

---

### Post by isantop on 2010-06-15
Yeah, on a 100% successful clean install, Lucid seems to be working great now on PanP4s. Just make sure you have installed the System76 Driver and that you have all updates installed, and you should be good to go.

About bgreenaway's splash screen resolution problem, it is a known issue, and happens with almost all recent Nvidia and ATI graphics cards with proprietary drivers enabled. We do have the fixes here on the forum, and also in our knowledge base.

Intel Graphics users do not have this issue since Intel drivers are open source. Thus, PanP4i's are exempt. Panp4n's have the problem.

---

