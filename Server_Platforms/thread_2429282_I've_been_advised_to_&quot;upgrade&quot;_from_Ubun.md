---
title: "I've been advised to &quot;upgrade&quot; from Ubuntu 18.10 to 18.04.3 LTS"
date: 2019-10-16
forum: Server Platforms
---

### Post by rogerk03 on 2019-10-16
Hi,

A bit of newbie to Ubuntu, but not to Linux itself.  I'm a programmer not a system admin.

I run a server on a VPS which works great, it runs Ubuntu 18.10 which I have been advised is now obsolete, no updates available.  I've been told to upgrade it and move to an LTS version, makes sense.

My questions are:  The upgrade process is easy (sudo apt dist-upgrade, I think), but the latest LTS version seems to be lower than what I'm running, is this right?  and is this 'downgrade' advisable?

What are people's advise to getting back on the latest LTS stream?

I'm running Ubuntu 18.10
Latest LTS is 18.04.3 LTS

I should add the server has a fair amount of stuff on it now, runs some live commercial websites and commercial applications for friends, some domain names and servers for various things, so I'm looking for the least risky approaches..

Thanks for any help you can give me or guidance in the right direction.

---

### Post by guiverc on 2019-10-16
Yes Ubuntu 18.10 (or the 2018-October release) is EOL, it's upgrade path is to the next release, Ubuntu 19.04 (from 2019-April, ie. *yy.mm* release format) which is the only tested & supported release path. LTS releases can upgrade to the next release (ie. 18.04 to 18.10) OR to the next LTS release (ie. 18.04 to 20.04).  Backward 'upgrades' are not supported or tested for.

If you want to go backwards, I'd backup your system, then install 18.04 LTS over it using "something else" and ensuring you don't format your system. This method allows going backwards, or skipping releases going forwards; be sure to have 'no format' used, and it'll take note of your added packages, erase system directories, install system, add-back added packages (where available for your new release) without touching your user files (providing you don't select format!!).  However...

If you move backwards though, whilst it'll work (system-wise); some programs may have problems with the later data files, eg. I've had problems before with evolution (mail program/MUA) where it couldn't cope with "newer" features I'd started using, and thus those messages where I'd 'filtered' using newer features were ignored (by the older program as if those mail messages were invisible to it)... This is not a re-install problem, but an issue with the older program not knowing how to 'interpret' the detail/data added to my data files by the later program; this is why backwards upgrades are not supported (*it's your job now to see what programs were updated in 18.10 that you use, and if that could cause problems for you with a downgrade*).

Your other option is to move forward as expected; to 19.04, then sometime soon 19.10 before eventually reaching 20.04 LTS (the next long-term-support release six-nine months in the future).  Two paths are offered, LTS which has longer life and 2+ year upgrades, or 6-9 month regular upgrades; by using 18.10 you've selected 6-9 month upgrades.

---

### Post by Holger_Gehrke on 2019-10-16
No, you can't downgrade without doing a new installation. Might still be the better alternative, an LTS gets 5 years of support (or three for flavours besides mainline and server) while non-LTS releases only get nine months. The 'version number' is actually a release date, LTS-releases are done in April of even years (So the next LTS after 18.04 will be 20.04). The command to do a release upgrade is not 'sudo apt dist-upgrade' (which is just a more intense version of 'upgrade'; upgrade won't install new packages as dependencies, dist-upgrade will) but 'sudo do-release-upgrade'. 18.10 has been out of support for about three month, so you might have to follow [this procedure for an EOL-upgrade]("https://help.ubuntu.com/community/EOLUpgrades"). The next release is 19.04 which has about three month of support left. 19.10 should arrive before the end of the month, so if you go with 19.04 you'll have to do another upgrade within the next few months.

Personally I would **never** go with a non-LTS release for a server that's live on the internet. I'd go from one LTS to the next and not do the upgrade until the first wave of problems in the new release has been cleared up, so I'd do the upgrade about half a year after the release.

Holger

---

### Post by CatKiller on 2019-10-16
> **rogerk03 said:**
> I'm looking for the least risky approaches.

For the future, that is to stay on a Long Term Support release until you've decided that it's time to upgrade to the next Long Term Support release.

Since each LTS is every two years and each LTS has five years of support, you have plenty of time to evaluate each release before you upgrade: you can test the next *two* LTS releases for a year before you run out of support. You can get support for even longer after that if you pay for it. 

The interim releases are where they try out all the crazy new stuff that might work, or might not. As you've found, using an interim release also puts you on the upgrade treadmill.

In your case, doing a fresh install and restoring your data from your backups is the method that provides you with the least disruption. Doing an upgrade from one interim release to another might *still* mean you need to do a fresh install and restore from backups, if it all goes pear-shaped, and you'll need to do it all again in six months' time.

---

### Post by TheFu on 2019-10-16
18.04 is the current LTS.  Even years, April is when LTS releases happen.  All other releases are non-LTS and have 6-9 months of patching.  19.04 support ends in 2 months, so if you move 18.10 (support ended last July) to 19.04, you'll need to move to 19.10 when it is released any day now.  I don't keep up with non-LTS stuff. Not worth my time.

Servers should 99.9999% run LTS releases with extremely few exceptions.

Being a developer doesn't relieve you from being a good admin. If you'd known the release cycles for Ubuntu, all of this could have been avoided:
[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)
[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)
Don't just read the top page, but read the entire articles.

Ubuntu Server LTS releases have 5 yrs of free support and 10 yrs if you pay.

As for getting onto a supported release, there are 2 options.  Both are equally bad, IMHO.
a) move to 19.04, then 19.10, then 20.04 when that eventually gets released.
b) perform a smart backup of the packages, data and settings, then perform a fresh install of 18.04, restore the data, settings, then install the packages. The order is important.  If the binary data is compatible, this should work, but going backwards is never supported. It could be bad or fine. No way to know without trying.

*apt-get dist-upgrade* doesn't move releases.  It moves only the 3rd level.  So, 18.04.1 --> 18.04.2  --> 18.04.3 That's what dist-upgrade does.  This is different from Debian.

On ubuntu, the way to move from 18.10 --> 19.04 is to fully patch the system, reboot (if needed), then run **do-release-upgrade** Before doing anything like this, please, please, please make a know-you-can-restore backup.  Sometimes release upgrades fail for out-of-support versions, like 18.10. Failures are more likely for systems that use packages outside the core Ubuntu repositories.

Backup, backup, backup.

---

### Post by slickymaster on 2019-10-16
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2019-10-17
Not much to add other than I also agree that production servers should be using the LTS versions only.

If I were you, I would start migrating the sites to an 18.04 LTS server.  That obviously means doing one at a time and make sure everything works like it should before flipping the switch on each site to the new location.

LHammonds

---

### Post by rogerk03 on 2019-10-17
OK, thanks for all the input.  Food for thought, I'll try this option: "[COLOR=#000000]a) move to 19.04, then 19.10, then 20.04 (LTS) when that eventually gets released.[/COLOR]" and see how it goes.

Seems I'm not the only one who made this mistake: [https://askubuntu.com/questions/1125375/ubuntu-non-lts-to-lts-in-the-future](https://askubuntu.com/questions/1125375/ubuntu-non-lts-to-lts-in-the-future)

I'll do more research, but is there any special requirements when upgrade to an LTS release from a non-LTS that come to mind?

In the above question someone pointed out changing [COLOR=#242729][FONT=Arial]_etc/update-manager/release-upgrades_ to _Prompt=lts_ [/FONT][/COLOR] for future upgrades

Thanks for your input, really valuable.

---

### Post by CatKiller on 2019-10-18
> **rogerk03 said:**
> I'll do more research, but is there any special requirements when upgrade to an LTS release from a non-LTS that come to mind?

No, it's just the same as any other upgrade. It's just that the release itself gets longer support and they're more conservative about what changes they put in it. Plus they test LTS-to-LTS upgrades as well as the consecutive release upgrades.

Check the release notes before you upgrade from one version to the next; there are sometimes important notes there. For example, one release of Kubuntu couldn't do the upgrade - I think it was from 14.04 to 16.04, or it might have been the one earlier - which is useful to know *before* you try it, but not terribly helpful after.

---

### Post by LHammonds on 2019-10-18
> **rogerk03 said:**
> I'll do more research, but is there any special requirements when upgrade to an LTS release from a non-LTS that come to mind?
I don't know how other admins upgrade their systems but for me, I NEVER do an in-place upgrade.  The in-place upgrades are for upgrading the OS and ensuring the OS will have minimal upgrade issues...that means nothing regarding the additional apps you install and your configurations.

The only sure-fire way I have found to make sure I never see downtime from an upgrade is to build a new OS, install the apps, copy over the data and ensure it runs...then when ready, swap the IPs to make it the new production sever.  This is not a "zing" against Linux because there are usually just too many customized variables in play.  This also lets me document how to install the new OS, applications and data for each version of the OS that comes out.  And having that documentation for each version is VERY helpful when it comes time to upgrade in the future.  You can check the links in my sig and look at the tutorial forum I have to see that I have documented each version of the servers and applications since 12.04.  So when I need to migrate to 20.04, I have a hefty amount of documentation to pull from to ensure a smooth (and consistent) transition to the next version.

Good luck on whatever path you choose,
LHammonds

---

