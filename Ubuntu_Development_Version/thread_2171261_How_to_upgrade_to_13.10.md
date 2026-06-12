---
title: "How to upgrade to 13.10"
date: 2013-08-29
forum: Ubuntu Development Version
---

### Post by Mazate on 2013-08-29
Hi there, I'm currently on 13.04 and am interesting in upgrading early to 13.10.  Is there a way to do that without doing a clean install?  If so, how?

Thanks!

---

### Post by craig10x on 2013-08-30
I'm sure the more technically oriented of the group will soon come along with their suggestions, but couldn't he just run the live 13.10 session and select "upgrade" on the installer?...i kind of recall that is an option you get...Of course, it is a good idea to back up your important data on another hard drive....personally, i put my important data (you know, music, video files, documents, etc) on a flash drive before i move to a new version of ubuntu....makes it easy to re-install it and preserves it in case something goes wrong with my new install...

---

### Post by deadflowr on 2013-08-30
I've installed development branches several different ways.
Method1)Change the sources.list, I think this is called the debian way.

Method2)press alt+f2, or open a terminal and run update-manager -d, which should point you toward the development release.

Method3)And I've installed clean and fresh.

The method I've not done, and you could try is simply
```
do-release-upgrade -d
```
in a terminal.

See if any of these work.

Personally, unless you upgrade soon after the development branch rolls out, I think a fresh clean install is best.

---

### Post by grahammechanical on 2013-08-30
I upgraded a Raring install to Saucy Salamander within one week of the release of Raring. That went fine as the code differences were not too great. But a month later and there was a much greater code difference. I would not recommend the changing the sources list method this far into the development cycle. I am not sure about the Upgrade method either as the development cycle is not finished. Even when a new version of Ubuntu is officially released some people hit problems when upgrading. This is why many of us recommend a fresh install.

  A few minutes ago I put in a fresh install of Saucy in another partition because my regular install of Saucy is broken. On the new install I tick for updates to be installed at the same time as Ubuntu was installed and after rebooting I ran Software Updater and that downloaded another 104MB of updates. This shows how much development work is going on. At this point in time anyone upgrading from Raring to Saucy should view it as an experimental installation unless they are prepared for things to break.

To give you another example, on this fresh Ubuntu Saucy I installed unity-system-compositor (that replaces the xserver with xmir). I restarted lightdm and I got a log in screen that will not accept the input of a password. I used Recovery mode>Resume to get to the desktop that I am using now but it is running on the fallback llvmpipe and there is a noticable difference between llvmpipe and Nouveau. It does not run xmir for a start and everything is a little slower.

So, Ubuntu Saucy Salamander is still very much under developement. Feature Freeze was yesterday. So, from now on it is bug fixing time for the developers.

Regards.

---

### Post by kansasnoob on 2013-08-30
If you're hell bent on trying a dev release just open a terminal and run:

```
update-manager -d -c
```

Then when things blow up ask yourself why you didn't just use a VM or multi-boot :(

---

### Post by deadflowr on 2013-08-30
It's been a while since I've run the update-manager -d(-c) method, so today i ran it on raring.
The old update manager, when that command was run, would give you the upgrade notification when the update manger opened.
Now it runs the software updater and you need to install the raring updates, then it gives you the option to upgrade when the updates have completed.

That said, again I'll stress clean install is probably preferably.
And +1 to VM or dual-boot (or even completely different machine that can sit in a quasi useless state from time to time)

---

### Post by su:bhatta on 2013-08-30
> **kansasnoob said:**
> If you're hell bent on trying a dev release just open a terminal and run:

```
update-manager -d -c
```



A week back I did this mistake!  Suggest follow Deadflowr and do a clean install in a separate partition!

---

### Post by PJs Ronin on 2013-08-30
I'm a fan of the upgrade in place mode.   For the 13.04 to 13.10 upgrade, there is an excellent thread [ here]("http://ubuntuforums.org/showthread.php?t=2138987&p=12619169&viewfull=1#post12619169"), but you need to be very mindful of post #7 in that thread.

I start with my production partition and clone it into other partitions I can upgrade and test on.   When I think I like what I see and nothing is ambushing me from the forest in these new partitions, I clone my current to a new partition and do the in-place upgrade.   Wash/rinse the other partitions (retaining the previous production partition) and start again.

I started with 12.04LTS and tried to upgrade to 12.10 but had bunches of problems so went the 12.04 -> 13.04 route... was a breeze.   I've now done the 13.04 -> 13.10 upgrade and it is so stable it looks like it is my new production partition.   The reason I chose this route is because I run a PostgreSQL database and a Win7 Pro VM.   Upgrading with the VM in place is not a huge headache, but I must retain PostgreSQL 9.0 and re-installing this version (is not in repos) and then fine tuning the PostgreSQL settings is more of an artform than a science... and I suck at art.

---

### Post by craig10x on 2013-08-31
Not directly related to this topic but i was just wondering...If i am running, say 13.04 and i upgrade to 13.10 but i have a ppa or two that were installed on 13.04...will the ppas still work ok or do you need to get the newer version of it (for 13.10) or change it on the source list?  What would happen if you did not change it's source list to Saucy? would it still work or break?

By the way...i just backed up all my important data on a flash drive and tomorrow i may try to do an upgrade using the latest daily build iso of 13.10...that seems to be a way that is rarely mentioned/used here so i thought it would be interesting to see how it goes...if things get messy, i will probably do a clean install of 13.10 at this point instead of re-installing my current 13.04...

That would be this method (as shown in this linked article) refers to 12.04 but the upgrade option on the iso appears in every version of ubuntu since 11.10:
[http://linuxmoz.com/upgrade-ubuntu-12-04-cd-dvd/](http://linuxmoz.com/upgrade-ubuntu-12-04-cd-dvd/)

Still no word on a "symlink" for ubuntu development yet, right?  (that was supposed to make it easy to roll from one development version to the next that they discussed at the previous conferences)...

---

### Post by jerrylamos on 2013-08-31
> **Mazate said:**
> Hi there, I'm currently on 13.04 and am interesting in upgrading early to 13.10.  Is there a way to do that without doing a clean install?  If so, how?

Thanks!13.10 is unstable in development.  If you get into unstable before release expect bugs and re-installs.  Sometimes often.  I'm told upgrades are supposed to work - but the forums are littered with people who tried and wound up with a non-running ubuntu.

On unstable testing like 13.10 is now, I have at least a couple partitions - the last good one like 13.04, a test one like 13.10, and maybe even another test 13.10 (I'm dabbling with mir testing.  Mostly bugs.)

---

### Post by craig10x on 2013-09-01
@mazate:  If you want to do the upgrade i would highly recommend selecting the "upgrade" option from the live iso installer...i used it this morning to upgrade from 13.04 to 13.10 and it went remarkably smooth with just a few easily corrected minor glitches which i mentioned in my other post...[http://ubuntuforums.org/showthread.php?t=2171771](http://ubuntuforums.org/showthread.php?t=2171771)
all my data and settings carried over so a big time saver for sure...

---

### Post by h-barkas-c on 2013-09-03
Thank you upgrading to 13.10

---

