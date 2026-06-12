---
title: "How often do you do clean install instead of upgrade?"
date: 2017-04-13
forum: The Cafe
---

### Post by sp40140 on 2017-04-13
I have been installing every update and every upgrade (regular and LTS both) as soon as they are released for about 8-10 years on same machine which I use as desktop/media server/htpc/print server/compiler. Basically it does everything.
I wonder when does it make sense to just wipe everything and do fresh install? 
Does the junk build up? I don't mean the logs. But old obsolete stuff? Does my system keep using older version?

As you can imagine, I have 10 years worth of customizations and software installed on it and it's very hard to get that list somewhere in my system.
So, is the fresh install worth it? Or should I just keep upgrading on the same OS?

How do you guys manage?

Not that it should matter from hardware side, but I am running core2quad, 8 gigs ram and AMD 7770 vid card. HD space is no problem.

---

### Post by RobGoss on 2017-04-13
I would say as long as it's not broke don't fix it. If your system is running as it should why attempt to fix anything or changes OS's, you're one of the lucky ones

I don't change OS's to often unless there's something terribly wrong an I am unable to fix it I'll keep the current distribution for as long as I can. Don't get me wrong, I always have the latest distribution and LTS release but never just wipe a OS just to clean house, grant you there are times I know this must be done to make things run as they should but I always keep things running as they should so I don't have to change

---

### Post by mooreted on 2017-04-13
I used to do that but felt like a bug tester after awhile. I now stick to LTS releases so I might re-install once every 5 years or something. Even when a new LTS comes out I like to wait for it to settle in have all it's quirks fixed. I prefer stable to new.

---

### Post by izznogooood on 2017-04-13
You should really listen to this:
[https://www.youtube.com/watch?v=3zpgQpdy_fI](https://www.youtube.com/watch?v=3zpgQpdy_fI)

Short lesson: If it works, don't fix it!

On my Desktop/Server I've been using 16.04 since alfa... But on my laptops I've been skipping and bopping and hopping all over the Distro's. Until I listened to this. Call it religion, crazy or common sense, he has a good point!

I will however still install PPA's for the software I feel I need ro update, like MESA drivers if you Play or Openshot if you edit video etc. But the base = If it works, dont change it!

---

### Post by sp40140 on 2017-04-13
I am more curious from the performance point of view. Does fresh install perform better over stack of upgrades (about 12-14 ubuntu versions)? If so, by how much? 
As I need to weigh it against personalizing all my stuff again which would take me some time. And some of the packages are not even available any more (like pysdm).
The reason I keep upgrading is mainly for security patching, kernel updates, drivers and multimedia fixes (audio specifically). And I fortunately, upgrades haven't broken things for me. In fact it's other way around. I see improvements. This is my personal experience, others might have experienced differently.

---

### Post by sp40140 on 2017-04-13
@izznogooood. That's a good video for someone who is looking to get into linux.
I am on the other hand, been using Ubuntu that's it. Once in a while I get interested in some other distro which I install in virtual env. But it's Ubuntu for me all the way unless something drastic happens.
This question is more focused on upgrades over fresh install (same OS/ distro).

---

### Post by mooreted on 2017-04-13
Performing and in-place upgrade can leave cruft and outdated settings and files in place. Since I only install LTS I always perform a clean install. I have had problems in the past with in-place upgrades especially when major changes have been made in the next version like Grub2, Upstart, etc.

No one can tell you which is best for you. I can only share how I do it and why. You have to decide what is best for you.

---

### Post by #&amp;thj^% on 2017-04-13
> **mooreted said:**
> Performing and in-place upgrade can leave cruft and outdated settings and files in place. Since I only install LTS I always perform a clean install. I have had problems in the past with in-place upgrades especially when major changes have been made in the next version like Grub2, Upstart, etc.

_**No one can tell you which is best for you. I can only share how I do it and why. You have to decide what is best for you**_.
+1 :)
 I also like my LTS a fresh start (Clean Install)
But as a tester I have one partition that I keep rolling to the next Development cycle....but I also now clean the cruft on occasion to avoid false bugs.
It just boils down to experience that you acquire...and your personal preference.

---

### Post by RobGoss on 2017-04-13
>  I am on the other hand, been using Ubuntu that's it. Once in a while I get interested in some other distro which I install in virtual env. But it's Ubuntu for me all the way unless something drastic happens. 

And that's OK trying other distributions that's how you learn and get to see what's new, but you need at least one stable machine as your primary go to computer which I have and it runs Ubuntu 16.04.2 and runs like a champ

---

### Post by mörgæs on 2017-04-14
You have been lucky so far. Don't take it as a sign that you always will.

I would install 16.04.2 in a dual boot, setting all your software packages up for testing. When everything works then you can move your personal files and let the old install go.

---

### Post by izznogooood on 2017-04-14
> **mörgæs said:**
> You have been lucky so far. Don't take it as a sign that you always will.

I would install 16.04.2 in a dual boot, setting all your software packages up for testing. When everything works then you can move your personal files and let the old install go.

+1

Yoiu could buy a SSD, install fresh. Move your old disk to port 2, and move your home back. This way you keep your settings as you install software, and will certainly get a speed boost.

---

### Post by sp40140 on 2017-04-14
Well, it's not always been smooth. I have had random fires which I have been able to put out without much trouble. Especially Nvidia prop drivers don't play well with brand new version. It takes some time and few updates for Nvidia prop drivers to work properly. But I have been able to handle things.
I already have an SSD. So, I might just do fresh install. I have couple other machines competing for the SSD though.
Just that I am bit concerned about loosing all my 10 years of customizations. It will take me forever.

---

### Post by yetimon_64 on 2017-04-14
I only ever tried using upgrades when upgrading Gutsy to Hardy back in mid 2008. It was a messy affair so have always done fresh installs since. Basically I am a user who always does a fresh install, I suppose out of habit, nowadays.

Being a dual-booter I often have an overlap of systems. When the new system stabilises and I get it set up to the point of comfortable usability I fully transfer my data and settings across and then a bit later on remove the older install. Often an older install will remain for up to several months on the drive until I am fully comfortable with the new install.  Cheers, yeti.

---

### Post by wildmanne39 on 2017-04-14
I all ways do a clean install, I have tried both but upgrades can be disastrous and they take a lot longer then clean installs most of the time, the more major changes in the new release the bigger the risk, and also you have to have pretty much a stock install when you upgrade for example remove all ppa's and third party software.

---

### Post by cariboo on 2017-04-14
I always run the latest testing version, and it depends on if I have any problems, on whether I do a clean install or just upgrade, on this system, Ubuntu, I will do a fresh install, but on my laptop, I'll just do an upgrade to 17.10 AA.

---

### Post by schtufbox on 2017-04-14
I usually go somewhere between the two.  Clean install, but keeping my /home partition.  Usually have to clean up a few settings but doesn't take long :D
I actually just switched from Linux Mint 18.1 to Ubuntu Gnome 17.04 a couple of hours ago doing this.

---

### Post by Seb71 on 2017-04-15
A long time ago I tried an upgrade (between Ubuntu releases) and it failed. A few years after that I tried again with some newer releases and then succeeded. But I settled for clean installs and I only do them when there are major improvements with the new release.

I have a separate /home partition (besides / and a 2GB swap partition), but even from that I only keep my data and Thunderbird e-mail folder. I delete all the rest of the settings and configurations from /home. Then I do a clean install, re-formatting / partition in the process. I am still with Ubuntu (Unity) 14.04 LTS (on two of my PCs). 16.04 LTS was not worth the trouble of a re-install for me. And non-LTS Ubuntu releases have a too short support now to consider them (I only try them live or in Virtual Machines).

---

### Post by sp40140 on 2017-04-15
One thing I should have mentioned is that I am an average/typical home pc user. I just use Ubuntu (instead of windows). I am bit technical but I don't have time and inclination to mess with computer at home. I do enough of that at work. I just want my home computers to work. I see it as a tool. Like a pen. And you don't keep tweaking/personalizing/fixing a pen. You use it when you need to write. That's how I see my home pc. And many of the things I have configured are done by googling and this forum. I don't even remember half. So, if I were to wipe everything, I would have to spend quite a bit of time on it.

---

### Post by RabbitWho on 2017-04-15
I only ever do clean installs, and I do them whenever my LTS is no longer supported, OR if I feel the need to, which is only if the computer isn't working well.

---

### Post by SantaFe on 2017-04-15
I tend to upgrade to every version, LTS or not.  So far I've only had to do one clean install since 6.04. And that was only because I had KDE on my computer & the upgrade to KDE 5 went horribly wrong. ;)

---

### Post by ajgreeny on 2017-04-15
I am another who always clean installs, and like many here I use LTS releases only.
I do not wait until the current installed version loses support but move from one LTS to the next when the first point release arrives and most bugs have been squashed, ie in my current case, Xubuntu 16.04.1 which I moved to from 14.04 in Nov last year.

I have never upgraded from one LTS version to the next LTS so am unable to comment about the problems that others may have seen when doing so.

To make life easier I have a separate /home partition on my main computer and a separate /data partition on an old laptop I use occasionally, so other than the normal backups of personal files that I have created in my day to day use of the system, I do not need to worry about making other backups before clean installing.

---

### Post by mörgæs on 2017-04-15
> **sp40140 said:**
> One thing I should have mentioned is that I am an average/typical home pc user. I just use Ubuntu (instead of windows). I am bit technical but I don't have time and inclination to mess with computer at home. I do enough of that at work. I just want my home computers to work. I see it as a tool. Like a pen. And you don't keep tweaking/personalizing/fixing a pen. You use it when you need to write. That's how I see my home pc. And many of the things I have configured are done by googling and this forum. I don't even remember half. So, if I were to wipe everything, I would have to spend quite a bit of time on it.

Most of us are. 

I still suggest that you begin with a completely clean install, not keeping /home from the old one. While you install your stuff in the new Buntu you copy the relevant commands to a text in Google Docs. Next time you need to do a fresh install you just copy-paste the relevant commands from Google Docs to the terminal. 

This also gives you a convenient document for sharing if you want to teach other people to install and customise.

---

### Post by sp40140 on 2017-04-16
@morgaes. /home personalization is not an issue. Let me elaborate.
I just added SSD and did fresh install. Now I can't get my Brother all-in-one working, even though Brother provides a handy script which is supposed to take care of everything. The scanner doesn't even get detected! I use tonido. And I can't get it to start/launch. These are just two examples. And neither are located in /home. Also still working on configuring samba.
I think in place upgrade would have been much better in my case. 
Anyways, it's done. Time to dig in and sort some mess out!

---

### Post by sp40140 on 2017-04-17
I just upgraded my laptop. No issues at all. Everything working fine. 
I think I will stay away from clean installs in future.

---

### Post by speedwell68 on 2017-04-19
I only use LTS and always wait for at least a month after it's release and do a clean install.  Stability, I has it.

---

### Post by 6975 on 2017-04-19
I never trust upgrade whole system it's a big mess. Always clean install for me.

---

### Post by qyot27 on 2017-04-20
I do a clean install on every 6-month release, and have since I started using Ubuntu.  There was only one time I tried an in-place upgrade, and I can't remember if it was Breezy->Dapper or Dapper->Edgy.  I started using a separate /home around the time Intrepid came out.  And if I need to recall something I installed, I started doing prep work by copying the apt install logs to /home before doing another clean install and pruning them down to just what I know I need so I only have to issue a few commands once the new version is installed.  The new version is more or less at par with the old version the same evening, although my cross-compilation environment can take several days to a couple weeks to settle down because of the way GCC times their stable releases.

---

### Post by monkeybrain20122 on 2017-04-21
Always clean install instead of "upgrade".

---

### Post by LastDino on 2017-04-21
Fresh install, ALWAYS!

Had trouble on my first experience with Linux while upgrading, but I was lucky I was dual booting. Since then always fresh install. 

Also, system stays pretty clean.

---

### Post by shantiq on 2017-05-12
Used Ubuntu since 2009 and for first 3 or 4 years I never had any luck with upgrades always ended up having to go to fresh install in the end with all logistic hassles involved... maybe i did not know to suspend PPAs in software-properties-gtk/other programs or maybe it is simply that these days the distro versions are way slicker and last 2 or 3 versions upgraded as smoothly as a seal dipped in honey ... nothing broke ...   all went very well up to the next number ...   for which I am even more awed by Ubuntu code writers ... SO to answer question in 2017 no need for fresh install altho it will speed things up AT FIRST later on it makes little difference
To clean as you go is always a good plan tho   ubuntu-cleaner   ace software to use and clean the dead wood

```

sudo add-apt-repository ppa:gerardpuig/ppa
sudo apt update
sudo apt install ubuntu-cleaner
```

---

### Post by exhile on 2017-05-12
It looks like a lot of Ubuntu users prefer to do a clean install over an upgrade path whether it is an LTS point release, a new non-LTS version or new LTS version. I would think the upgrade path would be a better choice since I'd hate to download drivers and redo all the settings again in a clean install. However, from what I've read, Ubuntu users have a lot of problems with the software update when upgrading. This thread is very useful since I've only been using Ubuntu for less than a year. Thanks all who have contributed to this thread.

---

### Post by sp40140 on 2017-05-12
I think a lot of habits were developed in the past when upgrade was troublesome. But lately, I have found that the upgrades are very stable ( I never had issues with it). Instead clean installs take lots of time and energy to get back to that comfortable level of customization and all the software you installed overtime.
I will be doing in-place upgrades until it creates problems.

---

### Post by #&amp;thj^% on 2017-05-12
I think for newer users...a clean fresh install enhances the user's experience..
You know the old rule..(Cant put The Good over The Bad)
I have one disk with a Ubuntu Partition that has come from 12.04 to 17.04 with out issues.
Just depends on the user's tech skill's.
Seen a lot post's with the first initial release of 16.04 with some pretty significant problems with upgrading.
Besides the practice of reinstalling a new OS is a good practice in gaining more experience if needed. (Admit it or not)
And with good back-ups a reinstall really dose not take that much time, when you take into account the hours waiting or finding out why your upgrade just failed...LOL
BTW I use both methods for newer release's.
Just my 2 cents worth

---

### Post by Cavsfan on 2017-05-13
First of all I have an old PC with a 500GB drive. I must have Windows for my wife and so I can help friends if they have a problem.
Because it is an old PC (2009) I can only have 4 partitions and the 4th is the extended partition. Then logical partitions come after that.

I upgraded an LTS version once but, other than that I do clean installs.
I like to have an LTS and like ajgreeny, I wait until the 1st point release has come out.
Plus I have to always keep up with the latest release, whether it's a 9 month or an LTS release for the Wiki in my signature.

Once I tried just having an LTS version; ignoring the other releases and grub changed so my Wiki became outdated. That was embarrassing to say the least.

I also became an Arch Linux enthusiast about a year and a half ago and it never needs upgraded or a clean install; it just evolves with the cutting edge apps. 
Arch only has what you choose to install on it, no bloatware, etc. I don't even have a DM I just login through tty and it starts up X and Xfce.
So I have Windows 10, Arch Linux, Xenial Zerus 16.04 LTS and Zesty Zapus 17.04 and can boot into which one I want to play with.

I have a 1MB swap file as one of my extended partitions and yes that's right 1MB just to satisfy that I do have a swap file. I've never seen 1kb used unless something is wrong.
I always select "Something Else" when installing and select the partition I'm installing and BAM. It sees my swap file and just installs.

I also label my partitions with this command e.g. **sudo tune2fs -L "Zesty" /dev/sda6** because it makes it easier.

EDIT: My Grub screen on 17.04 customized from my Wiki: 

[[IMG]http://www.zimagez.com/miniature/20170419165958.jpg[/IMG]]("http://www.zimagez.com/zimage/20170419165958.php")

The Grub background is also my desktop background on 17.04: 

[[IMG]http://www.zimagez.com/miniature/screenshot2017-05-0416-23-22.png[/IMG]]("http://www.zimagez.com/zimage/screenshot2017-05-0416-23-22.php")

---

### Post by gordintoronto on 2017-05-13
I like to look at a variety of new versions. In the 10 years I have been using Linux, I have done one upgrade, and probably close to 50 fresh installs. My current "daily driver" is a fresh install of Xubuntu 17.04. I have about 10 other Linux versions installed on various partitions of various computers.

---

### Post by cc1984 on 2017-05-13
I have always done fresh installs. I keep my home directory on a separate partition and I maintain a script that installs all the software that I normally use. So doing a fresh install is fairly easy. Then I just need to make config changes to my DE and a few other bits here and there. 

I have done this for some time simply because I tend to distro hop a fair amount. At this point though I've settled into 16.04 and stayed with it for awhile now. When the next LTS is released I'll probably wait a bit then attempt an upgrade this time instead of a fresh install.

---

### Post by lammert-nijhof on 2017-05-17
Clean install is only useful for Windows. I upgraded Ubuntu from 11.10, 12.04, 14.04 to 16.04 without problems. The same is almost always true, if I use upgrade for the alpha development versions, which proves that the upgrade process is very robust. Besides it is almost equal to normal updates/linux upgrades within a release.

---

### Post by Wadim_Korneev on 2017-05-23
[COLOR=#292F34][FONT=verdana]I do a clean install with every new version. I've just always never been a fan of upgrades across releases for any OS.[/FONT][/COLOR]

---

### Post by 7dEfOk4AgU on 2017-05-23
Back in the days of 4.10, 5.10 and of course 6.06LTS, also Win XP, 2000, (forget ME and Vista) and even old 7 I would religiously clean install to save on paracetamol. These days however upgrading has matured and I often will just upgrade. If the PC is getting a bit rough and grumpy I will take the opportunity of a new release to do a clean install.

---

