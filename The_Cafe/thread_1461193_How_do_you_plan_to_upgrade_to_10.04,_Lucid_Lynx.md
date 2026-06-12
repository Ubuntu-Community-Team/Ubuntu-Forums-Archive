---
title: "How do you plan to upgrade to 10.04, Lucid Lynx?"
date: 2010-04-23
forum: The Cafe
---

### Post by lookitseman on 2010-04-23
I'm trying to get an idea of just how many people in the Ubuntu community plan to upgrade to 10.04 via Synaptic.  I've never done it, despite using Ubuntu for a long time.

If you have any standard practices during upgrades to make the upgrades easier, feel free to list them. :)

For those of you who are upgrading via Synaptic, do you have a separate /home/ partition?  Does that make the upgrade any easier/harder?

=======

I'll start...

I have been using Ubuntu since 7.10 (Gutsy), and over time I have gradually shifted into linux.

I used Ubuntu in VirtualBox
...then in Wubi
...then by dual-booting (Windows+linux)
...then by dual-booting linux distros
...and now I own a copy of Windows 7, which I don't plan to install because it isn't worth the trouble of fixing my master boot record again.


I've always taken a few hours every 6 months to do some spring cleaning:
* archive anything important, trash as much of everything else as possible.
* gzip what's left and archive that for a month, just in case.
* Install fresh from live CD

This would be the first time I've tried to upgrade through Synaptic.  I'll still run my normal backups before upgrading, it's just a good practice to keep up.

---

### Post by TriBlox6432 on 2010-04-23
Wanna parcel that copy of Windows 7 to me?  :popcorn:

The laptop I'm selling would be worth a bit more with Win7 :P


Apart from that, I've got the RC which I installed via live USB (clean install)  I always do a clean install, and I do fresh installs several times in the 6 months, because I break stuff really easily.  Lukily, I've learned to back up.  It didn't work too good when I lost 7 years worth of school work.

---

### Post by alphacrucis2 on 2010-04-23
Fresh install as I have decided to use the 64 bit version. As far as I know upgrading from 32 bit to 64 bit could be a bit tricky, as in not supported.

---

### Post by lisati on 2010-04-23
I've currently got a triple boot (Vista, 9.04 & fully update 10.04 beta1). In a week or two, unless a problem shows up, I'll probably transfer the data from the 9.04 partition to the 10.04 partition and play musical partitions.

So far, the only minor annoyances are the moved close/minimize/maximimize buttons (workarounds for those who don't like it are documented elsewhere) and grub2 mis-identifying the Vista partitions (main partition identified as "recovery" and vice versa; also probably easily fixed, when I get round to it)

---

### Post by ed-koala on 2010-04-24
I already installed a fresh copy of 10.04.  I used to upgrade, but trying that from 9.04 to 9.10 resulted in a 3 day nightmare trying to get my system to boot.

I learned plenty from that experience. I just don't want to risk another "learning experience" similar to it. lol

Was probably more a result of how my PC is configured than any Ubuntu issue. I have RAID and I believe the changes in 9.10 concerning that are what zorked my upgrade.

---

### Post by garvinrick4 on 2010-04-24
I have already fresh installed a 10.04 and labeled it under /dev/sda5 /media/maverick
sda6 will stay as Lucid and my /home is still my /home sda7.
  I am ready to go thank you very much.


rick@rick-laptop:~$ sudo blkid
[sudo] password for rick: 
/dev/sda1: LABEL="SYSTEM" UUID="C6EECCF3EECCDCB5" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="66B0BDBFB0BD95D1" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 
/dev/sda5: LABEL="maverick" UUID="b2386000-aba8-49c2-b59b-7c2b87b37316" TYPE="ext4" 
/dev/sda6: LABEL="lucid" UUID="c4c94121-65f4-40a3-8ce3-80c720438f6b" TYPE="ext4" 
/dev/sda7: LABEL="home" UUID="1adc1fb7-dd51-48e9-8fea-77d6c6a75e78" TYPE="ext4"

---

### Post by ctrlmd on 2010-04-24
Karmic Koala and im not going to update until the next release or so 
its hard to download,burn, format and re-install everything every 6 months :(

---

### Post by Elfy on 2010-04-24
> **ctrlmd said:**
> Karmic Koala and im not going to update until the next release or so 
its hard to download,burn, format and re-install everything every 6 months :(

I'm moving all of mine to Lucid and leaving them there till the next LTS - unless they get something else instead of course.

---

### Post by ctrlmd on 2010-04-24
> **forestpiskie said:**
> I'm moving all of mine to Lucid and leaving them there till the next LTS - unless they get something else instead of course.
sound good if you have good dsl connection its easy to download everything  
i forgot about the lts, might download the LTS soon.

---

### Post by Elfy on 2010-04-24
> **ctrlmd said:**
> sound good if you have good dsl connection its easy to download everything  
i forgot about the lts, might download the LTS soon.

My connection is not as good as it was :( Been using apt-cacher-ng so I'm only going to be downloading once anyway. But I figured I would take advantage of the LTS this time around :)

---

### Post by Irihapeti on 2010-04-24
You can upgrade from one version to the next by using the alternate CD. Saves having to worry about dodgy internet connections.

I'll be doing a fresh install of Lucid and running it in parallel with Hardy for a little while. Once I've decided that Lucid is doing the stuff that I want, I'll remove Hardy.

I'll be a bit sad to see Hardy go; it's served me well over the last nearly two years.

---

### Post by TBerk on 2010-04-24
I've seen the 10.04 beta2 CD run on my system (1st version yet that got my RALINK chipset based wifi to work from the livecd btw).

My plan is also of the triple Boot variety as I want to keep a working, mostly debugged/patched/working 9.10 and XP option on the GRUB menu.

I'm in the process of backing up and making space prior to partition shrinkage to make a home for the new version (which looks to need an immediate update upon install, natch)


berk

---

### Post by Crunchy the Headcrab on 2010-04-24
Dual booting Vista and Ubuntu 10.04.  Have Windows 7 in a virtual machine on the Ubuntu partition.

---

### Post by standingwave on 2010-04-24
Something else.... Torrent to ISO to flash to full install. People still burn CDs?

---

### Post by madjr on 2010-04-24
> **standingwave said:**
> Something else.... Torrent to ISO to flash to full install. People still burn CDs?

you mean USB stick?


I've also used unetbootin (look ma, no CD or USB stick ^^)

in windows you can also use a virtual drive to mount it and use the install helper from the cd options (similar to unetbootin)

It does get stuck sometimes trying to unmount the virtual drive, but there's a command to avoid that, i need to look it up again

---

### Post by rudihawk on 2010-04-24
I've been using it since Alpha, so I'll just have to run an update to get the final version.

---

### Post by ..::| Dave89 |::.. on 2010-04-24
I'm upgrading to 64-bit on both desktop and laptop, so I have to do a fresh install.  I'm waiting on the final release on the 29th.

---

### Post by Paqman on 2010-04-24
I've already upgraded one machine and done a fresh install on another. I'll be upgrading the rest some time in the next week. The only time I do fresh installs is for testing (although that is my main machine)

---

### Post by c00lwaterz on 2010-04-24
i Have installed all of my ubuntu under windows using wubi. it is safer and easier for me to install and reinstall

---

### Post by standingwave on 2010-04-24
> **madjr said:**
> you mean USB stick?Yeah, flash drive. No reason to burn a copy.

---

### Post by Penguin Guy on 2010-04-24
I've always upgraded using apt, but I want to move to x86_64, so I have no choice but to do a fresh install. Then I'll have to set everything up all over again.

---

### Post by Khakilang on 2010-04-24
I think I do an auto upgrade unless something happen. I really don't like to reconfigure the whole thing again.

---

### Post by madnessjack on 2010-04-24
Experience tells me to fresh install- kinda like XP every 6 months :P

---

### Post by CharlesA on 2010-04-24
> **Koh Kook Loon said:**
> I think I do an auto upgrade unless something happen. I really don't like to reconfigure the whole thing again.
I'll be doing a clean install "eventually" but since I wrote up a "script" to install all the crap I need, it makes doing reinstalls pretty easy.

I only do clean installs, since after bumping up to 9.10 from 9.04, I had a few problems.

---

### Post by Chilli Bob on 2010-04-24
Will do fresh install if and when the bugs are sorted for my hardware.  Beta 2 was unusable.  Downloading RC now and will test tomorrow.

Feeling a bit hesitant to upgrade as my Jaunty is SOOOOOO perfect.

---

### Post by Detonate on 2010-04-24
I have upgraded to the RC using the Alternate CD, which was not one of the poll options, so I voted for "Something Else".

---

### Post by sanderella on 2010-04-24
> **forestpiskie said:**
> I'm moving all of mine to Lucid and leaving them there till the next LTS - unless they get something else instead of course.

Me too.

---

### Post by Crunchy the Headcrab on 2010-04-24
> **standingwave said:**
> Something else.... Torrent to ISO to flash to full install. People still burn CDs?
People with older motherboards may not be able to boot from USB.

---

### Post by Ebere on 2010-04-24
> **madnessjack said:**
> Experience tells me to fresh install- kinda like XP every 6 months :P

You did that, too ?

I wiped the HD and reinstalled XP on a refular basis. Just because it always worked better after a fresh install. LOL

I got pretty good at wiping, installing, and getting everything set back up again.  Got to where it would take less than an hour, instead of days.

I hope to learn all the ins and outs of setting Kubuntu up. Then eventually wipe everything out, do a fresh install, (gets rid of all the mistakes I have made. LOL), and make an image of the HD.

For now, I am on a fresh install, (wiped the hard drive, first), of 10.04.

I am almost completely to the end of the cap on my internet connection,  so any further updates will have to wait until after the 8th of next month.

 I have downloaded, burned and installed at least half a dozen  different .iso's. And updates, additional apps, etc... (The reason I am almost at my cap, already.)

Trying to figure out which one works best for me. And have so far had the best luck with Kubuntu.

---

### Post by th5th on 2010-04-24
I plan on doing a clean minimal install from a USB stick onto a brand new Samsung NB30 netbook... 

Then I will spend the next month trying to make Openbox work. I got sick of not being able to play with my Windows system, and have fond memories of Ubuntu from Feisty... So I am going for the "build-you-own-system-from-the-bottom-up-NOW-YOU-CAN-ONLY-BLAME-YOURSELF!" approach :P

---

### Post by ladypcer on 2010-04-24
I already did a fresh install to 10.4 beta 2. I backed up all important stuff, music, images, to a separate hard drive and just wiped the main drive. I think a clean install is better.

---

### Post by lookitseman on 2010-04-24
> **madnessjack said:**
> Experience tells me to fresh install- kinda like XP every 6 months :P

Ain't that the truth :D


I had expected a large number of us to say that they upgrade via Synaptic, but I'm glad to see that I'm already in the majority who just starts from scratch every 6 months, even if they don't wipe out their old partition just yet.

I need to investigate unetbootin / boot from flash stick... seems like a cool concept.

Still unsure if the home partition is a good idea or not.  If two versions of Ubuntu are sharing the same home folder, I could definitely see two versions of an application colliding with each other when writing settings to that directory.

I could have sworn launch day was the 24th...oh well, almost there!

---

### Post by -jay- on 2010-04-24
i wont be upgrading since 9.10 & 10.04 refuse to resume from suspend & after several trys trying to figure out why it wont resume i gave up sticking with 9.04

---

### Post by chessnerd on 2010-04-24
On this desktop, I believe it will just do a seamless upgrade from the beta so that's taken care of. However, I might do a reinstall anyway so I can redo the partitioning to allow for a second Linux version (I'm thinking Fedora or OpenSuSE).

On my other desktop I'll be going up from Xubuntu Jaunty to Lubuntu Lucid, so that will need a Live CD install.

On my laptop, I've been wanting to do some spring cleaning as it is and a fresh install is always a good way to do that.

I always do a fresh install. I've tried the upgrades and they work fine, but they do take much longer to finish than a fresh install.

---

### Post by tica vun on 2010-04-24
Upgrade from lucid beta. This is the same install I've been using since 7.10.

---

### Post by yabbadabbadont on 2010-04-24
After another month or two, I'll do a clean install using the alternate installation cd.

---

### Post by barney385 on 2010-04-24
I'm running 8.04LTSx64 right now, and I have my backups in place.

I usually go with the fresh install method, but I'm going with the ol' *sudo apt-get update* this time.

I'm actually pretty excited about it.

:smile:

---

### Post by CharlesA on 2010-04-24
> **yabbadabbadont said:**
> After another month or two, I'll do a clean install using the alternate installation cd.

What's the difference in running the alternate/minimal install cd as opposed to the regular server/desktop cd?

---

### Post by Irihapeti on 2010-04-24
> **CharlesA said:**
> What's the difference in running the alternate/minimal install cd as opposed to the regular server/desktop cd?

The alternate CD gives you options such as command-line install (i.e. Ubuntu with no graphics) that aren't available on the live CD. People who want a lightweight system usually start this way and then add other stuff.

It can also allow you to install if you can't get the live CD to boot for some reason, maybe because you need to add some special configuration file.

No doubt there are other reasons that I don't know about yet. :)

---

### Post by CharlesA on 2010-04-24
Thanks. I wonder if there is a huge difference between it and the regular server install, since server doesn't install a GUI by default.

---

### Post by Spike-X on 2010-04-25
Clean install, possibly to a separate partition so I can dual-boot with Mint, or I may just wipe the whole thing and start from scratch.

Reckon I might give the install-from-USB thing a try, too.

---

### Post by lookitseman on 2010-04-25
> **CharlesA said:**
> Thanks. I wonder if there is a huge difference between it and the regular server install, since server doesn't install a GUI by default.

The difference is similar to the difference between Ubuntu and Kubuntu... it's still ubuntu, but the packages are different.

Ubuntu Server Edition is shifted heavily toward a production web-server environment.

You have a fully operational LAMP stack from the first boot, there's no GUI, things like that...

---

### Post by scriptjamin on 2010-04-25
I will be downloading Lucid 64bit via Transmission, installing and then seeding the iso for a few weeks at a high upload speed for all of the extra fanatics out there!

---

### Post by finnlloyd on 2010-04-25
I always do a clean install.  I have used beta1, beta2, and the rc of 10.04 and I did a clean install each time.

---

### Post by xpod on 2010-04-25
> Re: How do you plan to upgrade to 10.04, Lucid Lynx?

Well i would normally have upgraded at least one of the 2 *buntu drives i`ve always had in my Desktop by now. I say "normally" because i`ve not got round to upgrading early this time, although there is still time. :)
I`ll usually upgrade one drive with a fresh install mabey about a month before full release and start using that as my main drive until after release time when, if all`s been well on drive 1, i`ll upgrade drive 2 with apt.

I use laptops more often than the Desktop just now but it still does the print/nfs server, storage/backup etc for the rest of the house, among other things.

EDIT:
One of my laptops has the lucid release of Lubuntu if that counts. :-)

---

### Post by mamamia88 on 2010-04-25
i've installed pclinuxos gonna use it at least until lucid comes out.  i kind of like it not sure if i'm gonna move over to lucid or what

---

### Post by leopards on 2010-04-25
Since I hit a glitch going from 9.04 to 9.10 trying to do an upgrade after going to grub2 and EXT4! I had to do a clean install for 9.10 after all! Now I have a separate /home partition setup and am on EXT4 with grub2, so a upgrade via synaptic later in the week, or from an alternate install disk via Transmission should do the job, with the Caveat that I have everything backed up on an external drive!:P

---

### Post by wpLOL on 2010-04-25
I'm going to do a fresh install :)

---

### Post by Plumtreed on 2010-04-26
I have a 'working' PC that will be upgraded some time between now and April next year. It is running Hardy 8.04LTS and will be upgraded when it appears to be completely stable.

I have been using Lubuntu since Beta 1 on a laptop with almost daily updates. This is the computer I play with and I think Lubuntu is going to be my main OS on this PC, now running Karmic.

---

