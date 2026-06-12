---
title: "Beware of 22.10 Update right now.."
date: 2022-09-19
forum: Ubuntu Development Version
---

### Post by zebra2 on 2022-09-19
Just got Gnome 4.3 final in updates


Snap is full on.  It deleted most of my apt apps including Brave browser.  Had to install the snap version.of Brave which is now available. It deleted all of the other installed browsers including the Ubuntu Epiphany Browser 

Make sure you have your browser bookmarks etc backed up. 

A reinstall may be necessary.

---

### Post by guiverc on 2022-09-19
I sit on the *development* release and haven't noticed any changes along the lines you mention.  Sure in 2019 I noted *chromium* replaced by *snap* package, more recently the *firefox* replaced by *snap* package, and whilst I couldn't tell you when that happened (*without looking up my apt logs*), I upgrade packages three times per day & do note changes before I install them  (*if they're only noticed on reboot; that's every fortnight for me*).  However both those changes were known/expected.. with me having loads of advance warning (*though my involvement with Ubuntu News, and Lubuntu (let alone other teams) likely mean I hear more than the average end-user*).

Yes, most of the time I'm using Lubuntu (LXQt), though for a change and as I really like Xfce I do use my Xubuntu (XFCE) or to look at changes that I noted install; even do sometimes login in with my Ubuntu Desktop session (GNOME) to see a change someone blogged about, or view the packages I noted that just upgraded.

The Brave browser isn't a Ubuntu package; I don't see it using `apt-cache search brave`, only see packages like 

```
gnome-brave-icon-theme - blue variation of the GNOME-Colors icon theme
```

The decision you're noting is likely made by whomever packages Brave and is not Ubuntu related as I see it, just impacts Ubuntu users who use that packaged browser.

---

### Post by zebra2 on 2022-09-20
```

zebra1@zebra1-Lenovo-320-15IAP:~$ snap list
Name                       Version           Rev    Tracking         Publisher   Notes
bare                       1.0               5      latest/stable    canonical&#10003;  base
**brave                      1.43.93           177    latest/stable    brave**       -
core18                     20220831          2566   latest/stable    canonical&#10003;  base
**core20                     20220826          1623   latest/stable    canonical&#10003;  base**
gnome-3-38-2004            0+git.891e5bc     115    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/&#8230;  canonical&#10003;  -
snap-store                 41.3-63-gbd822db  592    latest/stable/&#8230;  canonical&#10003;  -
snapd                      2.57.1            16778  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1               14     latest/stable/&#8230;  canonical&#10003;

```

I got a bit more functionality by reverting back to previous kernel.
It's what you learn after you know it all that counts.

I live for this. It is why I use the dev ISO's
Snap also installed core 20.

---

### Post by guiverc on 2022-09-20
The core16/18/20/22 packages are base/common runtime packages.

Yes it would be possible to make the *snap* packages enclose everything in them, but that would mean you're using a lot more disk space & possibly using more RAM during operation, so the *snap* equivalent to a *dependency* (using *deb* package speak) is *connections* and *extensions*.

e.g.  Ubuntu 22.04 LTS Desktop comes with the `firefox` snap, so I'll assume that *snap* package is used by default.

You can view *requirements* of any *snap* package with a few commands; using `firefox as example

```
guiverc@d960-ubu2:~$   snap info --verbose firefox |grep base:
base:         core20

guiverc@d960-ubu2:~$   grep default-provider /snap/firefox/current/meta/snap.yaml
    default-provider: gnome-3-38-2004
    default-provider: gtk-common-themes
```

[I]Note:  I've not re-run those commands, as I'm not using a Ubuntu system currently, so I'm pasting commands from a prior answer I've given here - [https://discourse.lubuntu.me/t/how-to-install-firefox-non-snap/3222/8](https://discourse.lubuntu.me/t/how-to-install-firefox-non-snap/3222/8)  so its possible the requirements have changed [slightly] since April 2022 when I gave that answer and thus ran those commands.

[/I]The first command shows the `firefox` snap was built on a Ubuntu 20.04 LTS system, thus it needs the **core20** runtime library to execute. That requirement exists regardless of your OS/release.

As you have core18 & core20 installed; you've installed *snap* packages that were compiled/built on both 18.04 & 20.04 systems, thus your system needs both of those runtime environments.

You'll also note two of your *snap* packages are used by my `firefox` example too... ie. the *sharing* of the resources saves disk space, but can also save RAM (*if you have more than 1 snap using them anyway*)

---

### Post by zebra2 on 2022-09-20
@guiverc

My post was not intended to be a request for information or help in anyway.  It was a cautionary notice for any new and inexperienced users that a 22.10 upgrade could be a problem right now.   So take necessary precautions. 

So far as the browser issue goes, the update deleted my install of firefox and chromium and the default installed Ubuntu Browser and installed the Brave Browser Snap.

I was setting up to reinstall this morning but decided to revert back a kernel and now all of the updates are working just fine including the Brave Snap. In addition to all of this the update deleted the contents of VAR/APT/Archives and reverted my update repositories back to default. 

I am currently well pleased with the new Gnome 43 Desktop.  I actually don't have any experience with the Ubuntu based flavours that you reference in your post so I don't have any opinion there.

---

### Post by VMC on 2022-09-20
> **zebra2 said:**
> Just got Gnome 4.3 final in updates


Snap is full on.  It deleted most of my apt apps including Brave browser.  Had to install the snap version.of Brave which is now available. It deleted all of the other installed browsers including the Ubuntu Epiphany Browser 

Make sure you have your browser bookmarks etc backed up. 

A reinstall may be necessary.

With latest updates, mine still show Gnome Version 43.rc, after 'apt update & apt upgrade'

---

### Post by zebra2 on 2022-09-20
Mine shows "Gnome Version not available" and with INXI it is showing Gnome 43. It has dropped the RC.  Everything that happened with this update indicates a system upgrade.  It deleted every browser on the system including the snaps and provided the code to install the Brave Snap, I suppose since Brave was default on my system.

---

### Post by zebra2 on 2022-09-20
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291052&stc=1[/IMG]

This is the same desktop that was proposed for Gnome when Unity was dropped.  I have it default now. I did revert back to kernel  5.19.0-16-generic.  -17 was buggy.

---

### Post by ian-weisser on 2022-09-20
> **zebra2 said:**
> It was a cautionary notice for any new and inexperienced users that a 22.10 upgrade could be a problem right now

That's a fair and valid point on it's own, regardless of today's papercuts.

New and inexperienced users should not be running pre-release without a good reason. By definition, they lack the skills and experiences to test, troubleshoot, and file bug reports. New and inexperienced users should be using released versions of Ubuntu, so they can obtain the support they need to gain skills and experience.

So kudos for that. I know that everybody already knows this, but it's good to repeat it clearly every once in a while.

---

### Post by #&amp;thj^% on 2022-09-20
> **ian-weisser said:**
> That's a fair and valid point on it's own, regardless of today's papercuts.

New and inexperienced users should not be running pre-release without a good reason. By definition, they lack the skills and experiences to test, troubleshoot, and file bug reports. New and inexperienced users should be using released versions of Ubuntu, so they can obtain the support they need to gain skills and experience.

So kudos for that. I know that everybody already knows this, but it's good to repeat it clearly every once in a while.
We have missed you ian-weisser. ;)
I'll add a quote from a friend..> Bleeding edge, not bleeding flat. Edge denotes falls will occur from time to time. Bring your own parachute.

---

### Post by VMC on 2022-09-20
I removed all occurrences of Snap in the beginning. Firefox is unaffected. I don't have any issue with latest updates.

---

### Post by zebra2 on 2022-09-20
> **1fallen said:**
> We have missed you ian-weisser. ;)


+1
I also like ian-weisser's use of the term "paper cuts".

---

### Post by zebra2 on 2022-09-20
@VMC
Everyone using Ubuntu 22.10 with the Gnome 43 Desktop is going to get what I have now. I just pulled it in sooner.  No problems with the updates, just the kernel as it turns out.  I'm all snap now including the Brave Browser which is in the Ubuntu Software as a Snap.  So far everything is very smooth.

---

### Post by Wise Ferret on 2022-09-20
Yes, for me the new kernel broke steam. It loads a black window now under the menu bar. With the old kernel (5.19.0-16) steam works fine. Maybe this is something about a regression concerning the communication with the nvidia driver.

---

### Post by zebra2 on 2022-09-20
@Wise Ferret
You may want to turn off proposed for a while until this settles down. The original idea for this new Gnome Desktop was to facilitate multitasking  on multiple desktops. It was idea-ted a few years ago.  Expect Snap to become more involved.

---

### Post by mIk3_08 on 2022-09-20
> **1fallen said:**
> We have missed you ian-weisser. ;)
I'll add a quote from a friend..
> **1fallen said:**
> 
Bleeding edge, not bleeding flat. Edge denotes falls will occur from time to time. Bring your own parachute. 			 		
Well, this is true. For safety purposes. Well if you want to survive you must always have a plan B. plan C or for far more plan D. Regards and cheers.

---

### Post by zebra2 on 2022-09-21
If you are concerned about safety then start with using the LTS release.  22.10 hasn't  had a ISO update since 8/29 so what is you recovery plan. The pending ISO are updated daily but they are untested.. The only safety in using a development version is "not caring".  I get along ok not caring but I have a couple of backup systems. I also keep a puppy linux boot on each computer. If all of that isn't enough I don't care.

---

### Post by guiverc on 2022-09-21
> **zebra2 said:**
> @guiverc

My post was not intended to be a request for information or help in anyway.  It was a cautionary notice for any new and inexperienced users that a 22.10 upgrade could be a problem right now.   So take necessary precautions. 

..

I am currently well pleased with the new Gnome 43 Desktop.  I actually don't have any experience with the Ubuntu based flavours that you reference in your post so I don't have any opinion there.

:P on warnings/advice, esp. to inexperienced users...

Ubuntu *development* releases (currently *kinetic*) aren't for newbies or inexperienced users, unless they have other boxes they can use & relyon, unless maybe they are wishing to hurry their *learning* process by fixing problems more regularly..  (*I expect a couple of issues each six month cycle,  few are serious, but some can take awhile to fix.. I've not needed to re-install since I installed in the artful cycle*)

Your advice is useful for me too, as it expresses your view of the experience, as my system is Ubuntu repository software only (*firefox is snap & unchanged on purpose for example*) so I can hopefully see the effects as upgraded packages roll out and hopefully preempt any problems, esp. as we'll have a *push for QA/testing* when *beta* finally rolls out.  I don't color my experience on this my primary box with 3rd party packages if I can avoid it (*mkusb probably my only exception** as I use that most days*).   Most of my play on installs from *daily* ISOs don't get updated much, as they're usually infrequently with much of the focus on the install itself (*unless I see reports from others about issues, or have experienced something on my primary box myself*).

I'm a Council member/Product Manager for one of the *flavors* thus the flavors are something I monitor rather closely.. but we're all part of larger Ubuntu family anyway. A huge amount of issues impact all anyway (*and if one/more flavor/seed isn't impacted -- that's a huge clue for finding the issue & thus fix!!*)

Thank you for your testing !  (*to @zebra2, but all other QA-testers too!*)

---

### Post by mIk3_08 on 2022-09-21
> **zebra2 said:**
> If you are concerned about safety then start with using the LTS release. I already used LTS since I've started using Ubuntu. Now I am in Ubuntu 22.04.1 LTS x86_64 with 5.15.0-47-generic kernel Though not much fan of using it but you don't have any choice you must have to be up-to-date for the sake of security reasons. Regards and cheers.

---

### Post by zebra2 on 2022-09-21
Well! looks like the ISO/Pending is on hold from yesterday and ISO/Current is still on hold since 8/29.  As soon as myself and 22.10 gets in sync with reality I think I will do a reinstall and resume without my cling-on deb packages. This since it appears that everything is showing up in the snap store.

---

### Post by VMC on 2022-09-21
> **zebra2 said:**
> If you are concerned about safety then start with using the LTS release.  22.10 hasn't  had a ISO update since 8/29 so what is you recovery plan. The pending ISO are updated daily but they are untested.. The only safety in using a development version is "not caring".  I get along ok not caring but I have a couple of backup systems. I also keep a puppy linux boot on each computer. If all of that isn't enough I don't care.Yes, indeed. I have no plans or a parachute. I like living dangerously.

---

### Post by zebra2 on 2022-09-21
> **VMC said:**
> Yes, indeed. I have no plans or a parachute. I like living dangerously.

Nice to find some common ground around here.  A few years back there was some testers in this section that was intentionally crashing ISO's just to see if it could be done.  That sounded pretty intriguing to me so after a couple of dozen re-installs I lost my fear of the process and moved on to other things.  I keep my /Home on its own partition so a reinstall only takes about 15 minutes given that I have an updated ISO in the first place. If not, I don't care. 

I may point out however that 22.04 was the most boring development ever released.  Just crused right through it. 22.10 getting interesting

---

### Post by mIk3_08 on 2022-09-21
> **zebra2 said:**
> I may point out however that 22.04 was the most boring development ever released.  Just crused right through it. 22.10 getting interesting Yes, It is true. Very boring indeed but it is more safer. It uses the latest python3 3.10 as their default, kernel 5.15LTS Gnome 42, latest Grub bootloader version 2.06, OpenSSL 3.0, GCC 11 and a lot more.

---

### Post by zebra2 on 2022-09-21
> **mIk3_08 said:**
> Yes, It is true. Very boring indeed but it is more safer. It uses the latest python3 3.10 as their default, kernel 5.15LTS Gnome 42, latest Grub bootloader version 2.06, OpenSSL 3.0, GCC 11 and a lot more.

+1
22.04 is pretty solid. Except it got released with a Snap system still in development stage.  22.10 has a desktop Snap and Deb store and is workig very smooth.  So far everything I have installed is perfect. It won't be the same Snap being used in 22.04 now.

---

### Post by zika on 2022-09-22
Just HU:
```
:~$ sudo apt dist-upgrade 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gnome-shell-extension-ubuntu-dock ubuntu-desktop ubuntu-desktop-minimal
The following packages will be upgraded:
  gnome-shell gnome-shell-common
2 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 1053 kB of archives.
After this operation, 871 kB disk space will be freed.
Do you want to continue? [Y/n] 

:~$ apt policy gnome-shell
gnome-shell:
  Installed: 43~rc-1ubuntu2
  Candidate: 43.0-1ubuntu1
  Version table:
     43.0-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu kinetic-proposed/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu devel-proposed/main amd64 Packages
 *** 43~rc-1ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status
     42.4-0ubuntu0.22.04.1 500 
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
     42.0-2ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages

:~$ apt policy gnome-shell-extension-ubuntu-dock ubuntu-desktop ubuntu-desktop-minimal
gnome-shell-extension-ubuntu-dock:
  Installed: 72ubuntu6
  Candidate: 72ubuntu6
  Version table:
 *** 72ubuntu6 500
        500 http://archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu kinetic/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu devel/main i386 Packages
        100 /var/lib/dpkg/status
     72~ubuntu5.22.04.1 500
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
     72~ubuntu5 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy/main i386 Packages
ubuntu-desktop:
  Installed: 1.494
  Candidate: 1.494
  Version table:
 *** 1.494 500
        500 http://archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status
     1.481 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
ubuntu-desktop-minimal:
  Installed: 1.494
  Candidate: 1.494
  Version table:
 *** 1.494 500
        500 http://archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status
     1.481 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```
Not using any of those packages (i3/sway-guy) so just giving HU to those who do... ;)
Too late I've seen that there is [a]("https://ubuntuforums.org/showthread.php?t=2479311") thread about that... Sorry.

Update&#8321;: 
 ```
...
The following packages will be upgraded:  gnome-shell gnome-shell-common gnome-shell-extension-ubuntu-dock
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


:~$ apt policy gnome-shell gnome-shell-common gnome-shell-extension-ubuntu-dock 
gnome-shell:
  Installed: 43.0-1ubuntu1
  Candidate: 43.0-1ubuntu1
  Version table:
 *** 43.0-1ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic-proposed/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     43~rc-1ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel/main amd64 Packages
     42.4-0ubuntu0.22.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
     42.0-2ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
gnome-shell-common:
  Installed: 43.0-1ubuntu1
  Candidate: 43.0-1ubuntu1
  Version table:
 *** 43.0-1ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic-proposed/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic-proposed/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel-proposed/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     43~rc-1ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel/main i386 Packages
     42.4-0ubuntu0.22.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 Packages
     42.0-2ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 Packages
gnome-shell-extension-ubuntu-dock:
  Installed: 74ubuntu1
  Candidate: 74ubuntu1
  Version table:
 *** 74ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic-proposed/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic-proposed/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel-proposed/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     72ubuntu6 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) kinetic/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) devel/main i386 Packages
     72~ubuntu5.22.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 Packages
     72~ubuntu5 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main i386 Packages
```

---

### Post by jbicha on 2022-09-22
> **zebra2 said:**
> Well! looks like the ISO/Pending is on hold from yesterday and ISO/Current is still on hold since 8/29.  As soon as myself and 22.10 gets in sync with reality I think I will do a reinstall and resume without my cling-on deb packages.

It's almost up-to-date now:

[https://cdimage.ubuntu.com/ubuntu/daily-live/current/](https://cdimage.ubuntu.com/ubuntu/daily-live/current/)

---

### Post by zebra2 on 2022-09-22
Re: pending and current ISO's.

Yes, just noticed that.  I'm going to update to cleanup my system but will still wait until things settle a bit more.  I really like where this is going though and the changes to Snap are decent especially the Snap Store Desktop.

PS I'm still using the 5.19.0-16-generic kernel though. -17 isn't working for me. Another reason I'm waiting to update. But it may be just an in-bedded problem.

---

### Post by zebra2 on 2022-09-28
22.10 ISO's are now available for download for 9/27/2022. The current and pending ISO's are identical. Applications provided as deb are available in the Snap-store.  After install of an application you will have to open the "permissions" link if provided and authorize needed and available permissions. There is a [COLOR=#000000]5.19.0-18-generic kernel in "proposed" but the [/COLOR][COLOR=#000000]5.19.0-17-generic is working ok.  I installed the newer kernel. [/COLOR]

---

