---
title: "White install screen."
date: 2024-01-01
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2024-01-01
When trying to install 24.04, once it boots up all I get is a white install screen.  no options at all, language, keyboard, or location.  Just white box.

Henry

---

### Post by MAFoElffen on 2024-01-01
> **Hewjr100 said:**
> When trying to install 24.04, once it boots up all I get is a white install screen.  no options at all, language, keyboard, or location.  Just white box.

The daily for Noble Ubuntu has been broken since 2023.12.12 Bug Report: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2043915)
We are hoping that will be going again soon. I made some noise up at the ubuntu-desktop-installer Git-Hub Issues, as a tickler.

If you intermittently check this thread: [https://ubuntuforums.org/showthread.php?t=2492322](https://ubuntuforums.org/showthread.php?t=2492322)
We often stop by that thread to comment on what is currently working or not for all flavors, and to post the bug reports of the problems we find. That way we have a common place to look to see where things are currently, any work-arounds, things that we are testing, etc. That is the sort continuity snap-shot.

This thread here is what hasn't been tested yet: [https://ubuntuforums.org/showthread.php?t=2493514](https://ubuntuforums.org/showthread.php?t=2493514)

---

### Post by Hewjr100 on 2024-01-01
Ok got it

---

### Post by corradoventu on 2024-01-03
The last 'good' ISO is from December 11th so why isn't the 'current' on the [https://cdimages.ubuntu.com/daily-live/](https://cdimages.ubuntu.com/daily-live/) page?

---

### Post by VMC on 2024-01-03
> **Hewjr100 said:**
> When trying to install 24.04, once it boots up all I get is a white install screen.  no options at all, language, keyboard, or location.  Just white box.

Henry
Thank you for reporting the "white screen install". 
I have a new PC and thought maybe that's the issue.

---

### Post by MAFoElffen on 2024-01-03
> **corradoventu said:**
> The last 'good' ISO is from December 11th so why isn't the 'current' on the [https://cdimages.ubuntu.com/daily-live/](https://cdimages.ubuntu.com/daily-live/) page?
corradoventu and I have been following this issue at: [https://github.com/canonical/ubuntu-desktop-installer/issues/2407](https://github.com/canonical/ubuntu-desktop-installer/issues/2407)

...and trying to keep focus on it, and at the bug report, which, I'm sorry, but I don't understand how they (the team at the GitHub) could _not_ have known about the Bug Report... 

I see that in the past 3 days, there has been some kind of activity, but what I see (mostly) is just lots of people complaining louder every day.

+1 with corradoventu. That is the fix = keep the last working ISO available until a newer working "good one" is spun. But that is not how they have that setup for. So changes would have to be made to implement that to be able to happen.

Currently, they spin up a "daily". They have 4 directories: current, pending, the current date, one day previous. They would have to create another directory there for the "last-good" iso. I don't know if they would buy into that, but seems to make sense for me, right?

---

### Post by VMC on 2024-01-03
I've seen this behavior before. I'm guessing different teams work on projects. The updates keeps rolling in while the section in question is left to their support staff or whoever is assigned what bug reports come in. It's weird to see a bug that brings installation full stop, and still updates keeping going on. 

I was trying to search for the last known good Noble. I use to have a couple of places.

---

### Post by MAFoElffen on 2024-01-03
> **VMC said:**
> I was trying to search for the last known good Noble. I use to have a couple of places.
As mentioned, I think the last good was 2023.12.11 or 2023.12.12.

We are really due for it to be fixed. I've never seen "Ubuntu" Dailys broken for so long before in Dev. Or at least I don't remember it being broken this long before.

---

### Post by lammert-nijhof on 2024-01-06
I has the same issue since the begin of Ubuntu 24.04.  I tried to install a VM in Virtualbox, I tried till Christmas or so and then I did give up.  I solved my problem by cloning a Ubuntu 23.10 install and upgrade it to Ubuntu 24.04 by: 
"do-release-upgrade -d" and that is why I finally have an Ubuntu 24.04 installation.  Note that the 4 Ubuntu flavors I installed in a VM, still used the old installer and that one worked. 

I think, I outsmarted the Ubuntu maintainers by taking a detour :)

---

### Post by VMC on 2024-01-07
> **lammert-nijhof said:**
> I has the same issue since the begin of Ubuntu 24.04.  I tried to install a VM in Virtualbox, I tried till Christmas or so and then I did give up.  I solved my problem by cloning a Ubuntu 23.10 install and upgrade it to Ubuntu 24.04 by: 
"do-release-upgrade -d" and that is why I finally have an Ubuntu 24.04 installation.  Note that the 4 Ubuntu flavors I installed in a VM, still used the old installer and that one worked. 

I think, I outsmarted the Ubuntu maintainers by taking a detour :)

Clever way do do it. I might try that if it isn't fixed soon.

---

### Post by wribeiro on 2024-01-07
It is worrying to have an LTS version, just 3 months before the official launch, with the installer broken for so long.
Users have been unable to install and test the system for almost 1 month.

---

### Post by corradoventu on 2024-01-07
Link to ISO dated 23-12-10 I used to install 
[https://drive.google.com/file/d/1RTe6MxrbNYs49Y7lvaC5Ezg10vfaPJU8/view?usp=sharing](https://drive.google.com/file/d/1RTe6MxrbNYs49Y7lvaC5Ezg10vfaPJU8/view?usp=sharing)

---

### Post by VMC on 2024-01-07
> **corradoventu said:**
> Link to ISO dated 23-12-10 I used to install 
[https://drive.google.com/file/d/1RTe6MxrbNYs49Y7lvaC5Ezg10vfaPJU8/view?usp=sharing](https://drive.google.com/file/d/1RTe6MxrbNYs49Y7lvaC5Ezg10vfaPJU8/view?usp=sharing)

Thanks! That did the trick. I'm undated on 24.04

---

### Post by biccyboy on 2024-01-10
This forum is probably one of the only places where I can actually have a bit of **faith** and **trust** in the validity of the contents to a Google Drive download that could be [I][U][B]anything!

[/B][/U][/I]Since its my only way of getting onto the noble build right now I'll give it a go too, so thank you for backing up your last known working .iso file. Putting all general internet security and safety aside, I'd like to become apart of the experimental updates community and try to provide some bleeding edge bug reports and become useful for the first time in a long while.

I've gotten quite a lot into Debian Linux distro's recently and the idea of helping out with new software sounds like a cool idea that I'd like to take part in. I've got some knowledge of programming and scripting so maybe you'll catch me on Github too.

Suppose this is more of an introductory post than a thanks, just excited to finally be apart of **something, *anything, really at this point! ***Even though the whole thing is based on an unsecured unscanned google drive file but I hope for the best! As you may tell I may come across desperate to just even take part in the community, let alone make an actual contribution but it feels like I've finally got something to do and work towards which is much needed for me.

---

### Post by corradoventu on 2024-01-11
NOT SOLVED!!! bug [https://github.com/canonical/ubuntu-desktop-installer/issues/2407](https://github.com/canonical/ubuntu-desktop-installer/issues/2407) is still open!!!

---

### Post by jbicha on 2024-01-11
A lot of work was done today to try to understand and fix the issue. It's now fixed with the mesa packages in noble-proposed. (After installing them, you'll need to log out and log back in.) However, it may be a few days for the new mesa packages to get out of -proposed so that the installer ISOs work without manual changes.

---

### Post by VMC on 2024-01-11
Yes, this is **NOT** solved. Downloaded today's pending "**11 January 2024 04&#8758;36&#8758;56 PM**". The "white" issue is still there.

---

### Post by paulobizarrocorreia-o on 2024-01-14
[COLOR=#202124][FONT=arial]Hello 

Everything is still the same today's download [/FONT][/COLOR][COLOR=#000000]white install screen[/COLOR][COLOR=#202124][FONT=arial]

[/FONT][/COLOR]Big hug from Portugal

---

### Post by jbicha on 2024-01-14
We are waiting for [mesa]("https://ubuntu-archive-team.ubuntu.com/proposed-migration/update_excuses.html#mesa") to migrate out of noble-proposed

---

### Post by corradoventu on 2024-01-14
BUT a snap package should be self-contained and run independently from the system. or not?

---

### Post by jbicha on 2024-01-14
Yes, but the Ubuntu desktop installer is currently a *classic* snap so it is not isolated as much from the rest of the system.

---

### Post by MAFoElffen on 2024-01-14
jbicha ---

Does that mean because, without a respin on the ISO, the setting for the snap "channel" is set, and "refresh" is still turned off?

Or... That with normal Snap app, all the dependencies are contained within the Snap, but since the problem is with Mesa, that is outside of those included dependencies, so a refresh of the Snap wouldn't necessarily pull those changes in? (So the change of that will be in the respin.)

---

### Post by jbicha on 2024-01-14
Yes, the fix is not in the Snap itself but in a dependency outside the Snap: mesa. The ISO is not set to build from -proposed so we need to wait for mesa to migrate out of -proposed. It is just waiting on amd64 autopkgtests (over 600 autopkgtests currently in line ahead of the mesa autopkgtests). I am hoping the mesa autopkgtests could pass tomorrow (Monday).

After that, the ISO needs to be rebuilt (it is scheduled for once per day. Someone with access could trigger a rebuild faster, but I do not have that access.). The rebuilt ISO goes first to daily-live/pending/ and after it passes automated tests, it gets promoted to daily-live/current/ . (This was a special bug because the automated install never stopped working and we do not yet have a system to test whether the installer is visible.)

Tomorrow is a US holiday so some people won't be working, but I think there is a good chance we could at least get a pending ISO by Tuesday.

---

### Post by corradoventu on 2024-01-16
SUCCESSFUL INSTALL from ISO Ubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20240116)
installed system works despite the install ends with bug 2049491 or 2049495 (I tried 2 times)

[https://bugs.launchpad.net/subiquity/+bug/2049491](https://bugs.launchpad.net/subiquity/+bug/2049491)

Edit: and /var/log/installer is almost empty
corrado@corrado-n4-nn-0116:~$ ls /var/log/installer
casper-md5check.json  media-info
corrado@corrado-n4-nn-0116:~$

Problem was due to local Italian mirror being updated, repeating install later install runs without problems on 2 different PCs.

---

### Post by grahammechanical on 2024-01-17
My ISO (updated 17/10/2024) now gives a white Preparing Ubuntu screen. And after selecting the language I can select Install or Try. If I click Try Ubuntu the screen disappears. So far, so good. If I click the Install Ubuntu Icon the white Preparing Ubuntu screen appears and the spinner goes round and around and does not progress to the next stage of the install process. So far, not so good.

For anyone's information

Regards

---

