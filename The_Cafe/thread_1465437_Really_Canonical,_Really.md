---
title: "Really Canonical, Really?"
date: 2010-04-29
forum: The Cafe
---

### Post by Twitch6000 on 2010-04-29
Well I thought I would give canicoal a chance and think they would hold back ubuntu to fix the intel bug they have. Well I gave them to big a chance. They have released ubuntu 10.4 with a huge bug.

The Bug - 

> Intel 8xx X freezes/crashes

The -intel driver fails with X freezes or crashes on certain i8xx hardware. The issue is known upstream but solutions are still under development. For now, to work around the issue, boot with the -vesa video driver. See [http://wiki.ubuntu.c...ucidi8xxFreezes](http://wiki.ubuntu.c...ucidi8xxFreezes) for further details.

Source - [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

Well that is nice to see a workaround,but uhmm all you get is a black screen,no terminal... 

Can anyone explain how a so called professional company would do this?

Edit: And according to  - [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

There is another huge bug ...

> Performance regressions with ext4 under certain workloads

The default file system for installations of Ubuntu 10.04 LTS is ext4, the latest version in the popular series of Linux extended file systems. ext4 includes a number of performance tuning changes relative to previous versions such as ext3, the file system used by default up to Ubuntu 9.04. These generally produce improvements, but some particular workloads are known to be significantly slower when using ext4 than when using ext3. If you have performance-sensitive applications, we recommend that you run benchmarks using multiple file systems in your environment and select the most appropriate.   

In particular, the dpkg package manager is known to run significantly slower on ext4, causing installations using the server or alternate install CD to take on the order of twice as long as before. ext4 does not guarantee atomic renames of new files over existing files in the event of a power failure shortly after the rename, and so dpkg needs to force the contents of the new file out to disk before renaming it in order to avoid leaving corrupt zero-length files after power failures. This operation involves waiting for the disk significantly more than it strictly needs to, and so degrades performance. If fast package management operations are most important to you, then you should use ext3 instead. (570805)   

The simplest way to select a different file system such as ext3 at installation time is to add the partman/default_filesystem=ext3 boot parameter when starting the installer. If you are deploying Ubuntu automatically using Kickstart or preseeding, then you can set a different file system in the partitioning recipe instead

Why must they release their distro with such big bugs. Is it that hard to hold off until they get fixed?

---

### Post by cariboo on 2010-04-29
When you expect to find something wrong you will, This has nothing to do with Ubuntu.

> The -intel driver fails with X freezes or crashes on certain i8xx hardware. **The issue is known upstream but solutions are still under development**. For now, to work around the issue, boot with the -vesa video driver. See [http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) for further details.

I've bolded the pertinent part.

---

### Post by Twitch6000 on 2010-04-29
> **cariboo907 said:**
> When you expect to find something wrong you will, This has nothing to do with Ubuntu.



I've bolded the pertinent part.

Which is why they should have been smart and went hey this is a big bug. Lets hold off the final until it is fixed or else millions of users will have a broken computer.

---

### Post by JDShu on 2010-04-29
First one :D more threads like this to come later

---

### Post by fatality_uk on 2010-04-29
> **cariboo907 said:**
> When you expect to find something wrong you will, This has nothing to do with Ubuntu.



I've bolded the pertinent part.

Here here!

---

### Post by 98cwitr on 2010-04-29
and people ask me why I still run ext3

---

### Post by P4man on 2010-04-29
> **Twitch6000 said:**
> 
Why must they release their distro with such big bugs. Is it that hard to hold off until they get fixed?

No indeed, its not. for YOU.  If you are affected by these known issues, you should hold off. But if that represents like 0.01% of all users, why hold off for everyone? If you are going to wait for any linux distro that works 100% on all PCs, then we will never get to see any new release ever.

---

### Post by Twitch6000 on 2010-04-29
> **P4man said:**
> No indeed, its not. for YOU.  If you are affected by these known issues, you should hold off. But if that represents like 0.01% of all users, why hold off for everyone? If you are going to wait for any linux distro that works 100% on all PCs, then we will never get to see any new release ever.

Hummm the ext4 bug will infect the majority of users.. It is the default filesystem you know...

---

### Post by Chrysantine on 2010-04-29
Ubuntu isn't the only distribution with this issue, SuSE for example suffers from similar problems with the Intel chipset/drivers.

Just sayin'.

---

### Post by NMFTM on 2010-04-29
Ubuntu is a balance between new features and stability. If stability is  extremely important to you than use Debian and wait 2 years between  stable releases. As far as Ext4 goes, it's been the default file system  for 6 months (other distros besides Ubuntu are following suit) and nobody's forcing you to use it. Just use the manual  partitioner during the installation and select Ext3.

---

### Post by P4man on 2010-04-29
> **Twitch6000 said:**
> Hummm the ext4 bug will infect the majority of users.. It is the default filesystem you know...

But not everyone runs the specific workloads that are affected. My filesystem performance using ext4 is outstanding for my workloads, thank your very much.

---

### Post by Twitch6000 on 2010-04-29
> **Chrysantine said:**
> Ubuntu isn't the only distribution with this issue, SuSE for example suffers from similar problems with the Intel chipset/drivers.

Just sayin'.

Sure it does,but atleast their community doesn't say it always works.. 

Not to mention the devs do try to fix bugs before its release. Even if that means holding it off. For instance 11.2 prelease had a bug which made them hold off the final.

---

### Post by swoll1980 on 2010-04-29
Lets hold back 15 million users because 20,000 might have a problem.  Windows 7 doesn't work with my network card. How does a professional  company release a $100 OS that doesn't work with my network card? What  the hell were they thinking?

---

### Post by smellyman on 2010-04-29
The bug is out there for all to read.  If your'e scared or think it may affect you then don't install.

simple really.

---

### Post by snowpine on 2010-04-29
10.04 is "Ubuntu Long Term Support;" it is not "Ubuntu Stable." Canonical has to live with it for the next three years. Sure, they could choose older software that is known to be stable right now, but a couple of years from now, that software will be quite outdated. So, they choose software that is somewhat stable now and will become more stable, but still relevant, as the release matures.

Conservative users who are concerned about stability will wait a year until 8.04 reaches its "end of life," then upgrade to 10.04 once it has had a year of bug fixes and security patches. Users who press "refresh" every 10 seconds to be the first on the block with the new release are enthusiasts, hobbyists, and techies who presumably enjoy the thrill of uncharted waters. ;)

---

### Post by Docaltmed on 2010-04-29
> **snowpine said:**
> Conservative users who are concerned about stability will wait a year until 8.04 reaches its "end of life," then upgrade to 10.04 once it has had a year of bug fixes and security patches. Users who press "refresh" every 10 seconds to be the first on the block with the new release are enthusiasts, hobbyists, and techies who presumably enjoy the thrill of uncharted waters. ;)

Precisely. We began migrating to Ubuntu just after the 8.10 release. I've been keeping up with the releases, and it's fun but it's a lot of work, and I've got other things I'm supposed to be doing. So once all of the company computers are on 10.04, I think we'll just sit there until the next LTS and let you guys work the bugs out. :)

---

### Post by Twitch6000 on 2010-04-29
> **snowpine said:**
> 10.04 is "Ubuntu Long Term Support;" it is not "Ubuntu Stable." Canonical has to live with it for the next three years. Sure, they could choose older software that is known to be stable right now, but a couple of years from now, that software will be quite outdated. So, they choose software that is somewhat stable now and will become more stable, but still relevant, as the release matures.

Conservative users who are concerned about stability will wait a year until 8.04 reaches its "end of life," then upgrade to 10.04 once it has had a year of bug fixes and security patches. Users who press "refresh" every 10 seconds to be the first on the block with the new release are enthusiasts, hobbyists, and techies who presumably enjoy the thrill of uncharted waters. ;)

Odd I hear all the time if I want a stable ubuntu to use the LTS... As it is "stable".

---

### Post by swoll1980 on 2010-04-29
> **Twitch6000 said:**
> Sure it does,but atleast their community doesn't say it always works.. 


How could you possibly testify as to what the entire Suse community says? Do you have some kind of special powers we should know about?

---

### Post by Chrysantine on 2010-04-29
> **swoll1980 said:**
> How could you possibly testify as to what the entire Suse community says? Do you have some kind of special powers we should know about?
Perhaps mind control! 

Seriously though, old Intel chips have been an issue for almost every distribution since i810 was dropped. I doubt it comes to anyone as a big surprise anymore (well, apart from the original thread starter).

---

### Post by arashiko28 on 2010-04-29
My computer is Intel based and I have never seen such a bug, the biggest one was in 9.10 release and was fixed as soon as the next kernel version came out, therefore I chose to help this time instead of giving headache to the community and installed 10.04 since beta versions came available, my 3 partitions runs on ext4 including the 10.04 install and have not noticed any slowing rate or lost in productivity... (Except for the first few days when I kept clicking the wrong thing with the windows buttons). I think that the beta versions are even more stable than ever, it has it's ups and downs, sure, but hey, even shoes sometimes gives us unexpected surprises.

---

### Post by KiwiNZ on 2010-04-29
Lets calm the aggression in this thread.

It is OK for someone to have an opinion that is not 100% pro Ubuntu , and it is OK for someone to voice that opinion . And this is the place to voice that non pro opinion. So calm down .

---

### Post by AlanR8 on 2010-04-29
Here here......day of release and already knockers?

---

### Post by powerslave12r on 2010-04-29
Installed mine within minutes of the availability to find the broadcom support still sucks! I had to connect through ethernet to apt-get b43-fwcutter.

Works like a champ now though. Only other complaint is the XV^ buttons on the left hand of the window title bar, but that's just a setting away.

---

### Post by snowpine on 2010-04-29
> **Twitch6000 said:**
> Odd I hear all the time if I want a stable ubuntu to use the LTS... As it is "stable".

8.04 is the current LTS; think of 10.04 as "LTS in training." :)

(Some would actually consider Debian the "stable Ubuntu" but that's a whole other can of worms now isn't it. ;))

---

### Post by lykwydchykyn on 2010-04-29
> **Twitch6000 said:**
> Odd I hear all the time if I want a stable ubuntu to use the LTS... As it is "stable".

Stable has a few different meanings.  In technical terms it generally means "not subject to major volatile changes".  In common parlance it tends to mean "not having a lot of bugs", but that's not the same thing.

I reported some freeze bugs on an i8xx chip for lucid.  The Ubuntu devs handled it promptly and were very helpful, but it is an upstream issue so they couldn't do much but send it on up.  I think the opendesktop.org devs closed it because whatever debugging info I sent wasn't complete (I would have done whatever they asked to get better info, but they didn't ask).

It's a catch 22 for distros: stick with the old version and you don't fix any bugs, add new features, or add support for new hardware.  Use the new version, and you may regress on older stuff.  Given the choice, which one would you choose?

---

### Post by PC_load_letter on 2010-04-29
> **KiwiNZ said:**
> Lets calm the aggression in this thread.

It is OK for someone to have an opinion that is not 100% pro Ubuntu , and it is OK for someone to voice that opinion . And this is the place to voice that non pro opinion. So calm down .

Totally agree, but no one held a gun to the OP's head to install Ubuntu 10.04 today w/ all the bugs that he thinks they're going to affect his computer. He still has options and workarounds as others have pointed out. His latest response is borderline trolling IMHO.

---

### Post by Chronon on 2010-04-29
> **Twitch6000 said:**
> Odd I hear all the time if I want a stable ubuntu to use the LTS... As it is "stable".

Well, that just seems like a fallacy that should be addressed.  It will become more stable as it is supported for longer and will get more bugfixes during its lifetime than normal releases, but I don't see a reason to view it as more stable at the time of release.

---

### Post by init1 on 2010-04-29
> **P4man said:**
> No indeed, its not. for YOU.  If you are affected by these known issues, you should hold off. But if that represents like 0.01% of all users, why hold off for everyone? If you are going to wait for any linux distro that works 100% on all PCs, then we will never get to see any new release ever.
That's pretty much what Debian does. It takes them years to release a stable version, because they take time to fix as many bugs as possible.

Edit:
Also, I understand the OP's frustration. I've had quite a bit of trouble with regressions in Ubuntu. Some older versions of Ubuntu work on my laptop, others don't. However, I feel that the overall progression of Ubuntu is positive. Certainly, compatibility is better than it used to be. But it's not perfect. Being able to run an older version of Ubuntu on your computer is no indication that a newer version will work, and visa versa.

---

### Post by limey_rick on 2010-04-29
I paid for Windows Vista x64, and could not install it on my PC because it had a bug when installing with > 3GM memory and multiple disks. I had to install with only 1 memory dimm in the slot and one disk, then go back in and add the other disks and memory cards after first boot. If I ever had to re-image, (and I did) I had to go and pull the disks and dimms out and call MS each time to re-activate my license. I installed Ubuntu 9.04 without problems. 

I installed Windows 7 on another x64 desktop and cannot run my memory at the fasted QA'd speed because windows crashes once or twice a day, with the blue screen of death. Ububtu 9.10 and 10.04 installed fine. 

MS release software that is not 100% bug free - their last OS was so bad, they had to re-brand it and sell it [again] - Apple release products with known issues and that can't be activated; why would Canonical be any different? They are a business after all as has been pointed out by the original poster? 

Its never good to moan about something you know was an issue when you started. It is much better to praise the approach to fixing the problems and considering the issues with the latest release and GRUB, I think that illustrates how Canonical usurp in my opinion and well done to them!

---

### Post by Ebere on 2010-04-30
> **Chrysantine said:**
> Ubuntu isn't the only distribution with this issue, SuSE for example suffers from similar problems with the Intel chipset/drivers.

Just sayin'.

DOOD !!!

You STILL only have 2 BEANS !!

You have a tapeworm, or something ?

;o)

---

