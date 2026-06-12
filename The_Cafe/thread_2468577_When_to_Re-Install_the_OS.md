---
title: "When to Re-Install the OS?"
date: 2021-11-03
forum: The Cafe
---

### Post by Shibblet on 2021-11-03
Hope I am not digging up a dead discussion here, but I am curious about this.  

Currently, I use Timeshift to make a snapshot of my Kubuntu 21.10 Install.  If anything goes wrong, I can run Timeshift and restore my OS back to my initial setup.

However, Windows users say that you should "re-install" your OS (the new version with all the updates and security fixes) every 6 months.  A clean-install, not a system-restore-point, or drive image.

Does this apply to Ubuntu, or is this just a crazy notion that people think needs to happen, and really doesn't?

---

### Post by ugjka on 2021-11-03
"Just re-install" is advice given by people who have no clue what they are doing

---

### Post by guiverc on 2021-11-03
I re-install when I have to, and not before.

This current system was an *artful* or 17.10 install, and I've had no reason to re-install since then (*even with numerous minor issues*...) and *release-upgrades* every six months (it's *jammy* now as I sit on the *development* cycle).

I'd only re-install IF I have need; which means I'm giving up trying to fix issues; OR I need the box functional after I've stuffed something up, and don't have the time to fix it correctly.

I have other boxes where I don't perform any upgrades, but that's intentional; I upgrade them via re-install (*upgrade via re-install* or *install using existing partition*) as the install itself is a QA *testcase* and I perform the weekly update via a QA-test re-install (and check out none of my user files are touched, the additional *manually installed apps* I added are re-installed by the re-install). But that's a special case; I perform a QA-test install instead of upgrading the box (currently that's a *jammy* and *focal* boxes; *jammy *as it's the current *development* release, and *focal* as it's next out of the '*gates*' (ie. 20.04.4 re-spin).

If I made a *mess* of the package system; that's when I'd likely consider a re-install - but again I'm more likely fix the issue without re-install to teach myself a lesson.

I had a box die a few months back, took out the system drive & put it in a replacement box. The replacement box was perfect, but I've performed this action before (*moved disk from a dead box and into another box*) & had an imperfect result; I re-installed that prior time, as I couldn't find the issue & wanted to move on (*got tired of looking for it*)

---

### Post by Frogs Hair on 2021-11-04
Unless an OS installation  is corrupt and non functional in some way I don't reinstall and that includes testing new versions of Ubuntu. I also upgrade to new stable versions at times. Backup for me entails  cloning my pictures and documents to removable sources and that's all I'm concerned about. If I had a hard-drive full of movies my backup process would be different. As a Windows user I have not heard of the reinstall every 6 months approach . Windows 10 has been getting two build/ feature updates a year and I suppose that is when some choose to reinstall.

---

### Post by grahammechanical on 2021-11-04
> Windows users say that you should "re-install" your OS (the new version with all the updates and security fixes) every 6 months.

I cannot speak for what would be the best practices of a Windows user. I just hope that the development model of Ubuntu is not confusing this matter. We get a new release of Ubuntu every six months. It has all the updates and security fixes as well as an updated firmware (drivers) and Linux kernel.

If we are using a Ubuntu Long Term Support (LTS) release we do get security fixes; updated firmware (drivers); updated Linux kernel and certain default applications also get up graded over a period of time.

If for some reason an OS gets broken or messed up in some way a re-install might be the simple and quick fix. If someone is using an unsupported version of Ubuntu then a fresh install might be better than a series of online upgrades to get to a supported release of Ubuntu. 

There are different opinions on this forum about doing online upgrades to every new release. Or, doing online upgrades from one LTS to another. Or doing a fresh install each time. We recognize the value of different working practices. Any of which might prove useful to other Ubuntu users. Over the years I have certainly been educated by posts on this forum.

Regards

---

### Post by Tadaen_Sylvermane on 2021-11-04
> [COLOR=#000000]Windows users say that you should "re-install" your OS (the new version with all the updates and security fixes) every 6 months. A clean-install, not a system-restore-point, or drive image.[/COLOR][COLOR=#000000]

This is because Windows doesn't clean up after itself. When you load a restore point it isn't exactly as it was when it was created, even though that is what they claim it does. Lots of crap get's left behind. CCleaner is a big hit for Windows people because of how much garbage get's stuck in the registry (even when you follow the uninstallers properly). With Linux however unless you do something really dumb like rwx the entire root directory recursively a reinstall shouldn't be needed. Even then the only reason is because it would take to long to fix (if it's even possible).

To be fair though. If you somehow cause or get an extremely obscure issue that you simply cannot find it is faster to reinstall from clean media and restore data than spend god knows how long chasing something that google doesn't seem to have anything on. This however is rare.[/COLOR]

---

### Post by lammert-nijhof on 2021-11-04
I almost never reinstall a system. I even always upgrade the OS, so recently I upgraded from 21.04 to 21.10 and in April I will upgrade again to 22.04. To keep my system clean and efficient, I use the "Ubuntu Cleaner".  My Host OS runs Ubuntu on OpenZFS and I take weekly snapshots. I had a  hacker trying to get some money in January, but I simply restored an old  snapshot, changed the passwords and lived happily ever after.

I use a lot of VMs and also there I have a number of old installations like Windows XP installed in March 2010 or Ubuntu 16.04 LTS now 16.04 ESM (Extended Security Maintenance) . Both run without re-installation for 11 and 5 years now and I still use XP and 16.04 a couple of times per week. But also for Windows I use a program to keep the system clean; "Advanced System Care". 

I only reinstall, when it is unavoidable and that is mostly caused by bugs, my stupidity or a combination of the two. You can reduce the stupidity reason by using a VM for all your experiments. 

Sometimes HW changes require a re-installation, but not always. I remember in 2019 I moved my disks 'lock stock and barrel' from a 2010 Phenom II X4 B97 to a 2019 Ryzen 3 2200G and the system booted without re-installation. I used that installation for half an year, till I had to reinstall it, because I bought a nvme-SSD.

---

### Post by TheFu on 2021-11-04
Good question.

First, typical Windows users aren't like typical Linux users in many ways.  This means the systems aren't "exercised" the same ways.
I have a Windows install that is over 10 yrs old and working fine, so the need to do a reinstall every 6 months is obviously some need based on use patterns, not the OS.

Every 3-5 yrs, I have moved the Windows install completely to new storage, so the typical "bit rot" that seems to cause issues on Windows is mitigated by this periodic move of all the bits.

Linux kernel updates are really easy and happen about 2x a month for supported released.  This is different than the WinNT kernel in Windows systems which probably gets updated at most, once a year. I honestly don't know how often this happens and would welcome specifics from someone who does.

New Linux and Windows users tend to install all sorts of junk.

I'm different in that regard.  My Windows systems haven't seen any new installs in about 5 yrs and had very few changes the 5 yrs prior to that.  Without all the crap installed on the systems, the cruft that builds up doesn't happen.  I ran 10.04 - 16.04 systems for many years in less than 15GB of storage. Because I know which programs I need to use for the workflows I use and Linux makes removing programs and dependencies easy, unlike Windows, there is less cruft with Linux OSes.

Both systems have issues with personal setting conflicts.  Gnome uses a DB to store setting - eeew.  That's very similar to how Windows uses "the registry." The solution to problems on both these systems is to create a new userid for logins and use that every few years.  This is more of an issue for people not using LTS releases.  If you only use LTS releases, that reduces the problem opportunity greatly.  

If there are issues on Linux, creating a new userid is a common troubleshooting issue. No need to reinstall. I suppose this could work for Windows too, but I don't recall anyone suggesting to create a new user to troubleshoot issues on Windows all that often.

For some issues that have been traced to be OS setting and not tied to an individual userid, I might spend 30 minutes troubleshooting, but since a fresh install on Linux isn't that big of a deal, after 30 minutes and failing to solve an issue, I'll wipe and do a fresh install much quicker than I would ever do on Windows.  Then 15-30 minutes to restore system and personal settings, followed by data, and finally I feed a list of manually installed packages into the package install tools and in 45 minutes, I've gone from an empty system to a system that "feels" like it is mine, with my settings and my data, but completely refreshed.  Because I do versioned backups, I can restore the system as it was 60, 90, 120, 180 days ago or any other day between last night and 180days ago.

On Windows, I'd probably have to spend a few days pointing and clicking to install software and get everything setup with my settings (assuming I don't miss something), all hands-on effort. Perhaps there's an easier way, but my Windows knowledge isn't strong enough to make it easy and getting all the "setup.exe" files for each 3rd party program is a major hassle.  Then there are the OS patches which aren't available anymore for my OS (unsupported), so I think I'd be screwed trying to recreate a Windows system from 60 days ago.  

If I were less skilled at Ubuntu, the same issues would likely hold me back too.  The point-n-click and the fear of reinstallation.

[LIST]
[*]Avoid cruft. Install what you need, nothing more.  If something isn't needed/used anymore, remove it.
[*]Have backups that are proven to be restored. Spend the time BEFORE you need it, now.
[*]Stay on supported releases, and move to a newer, supported, release BEFORE EOL happens.
[*]Always have a "Try Ubuntu" flash drive ready to troubleshoot boot issues and to see if hardware driver issues are tied to the installed OS or Ubuntu in general. Lots of issues can be quickly resolved using this *Try Ubuntu* solution.
[/LIST]

Simple things to avoid traps.

---

### Post by poorguy on 2021-11-05
I believe in the* **if it ain't broke leave it alone*** philosophy. :lol:

---

### Post by bunny9000 on 2021-11-06
I have a family member that's been running Ubuntu for the last 2 years going through upgrades with no noticeable slowdown and for 5 years I had the same OS on a machine and never noticed slow downs.

Windows used to have a bad rap with ntfs file fragmentation on spinning hard drives so the system would slowly slow down over time if no defragmentation was done and mechanical hard drives slow down as they age.

A lot of the problems Windows users have are caused by the users themselves by installing incompatible drivers, badly written software, or modify system files all of which can cause weird side effects that users may blame on the Windows Operating system itself, rather than their own actions.

When would I reinstall Ubuntu? When your hardware is faulty or you're moving to another computer.

---

### Post by kurt18947 on 2021-11-06
My primary install is 20.04 LTS. I'll probably leave it as-is until 24.04 has been out a few months. At that point I'll probably back up all my data and try an in-place upgrade if that's available after skipping an LTS version. Nothing says I can't install other versions or distros in the meantime without touching my primary.

---

### Post by Shibblet on 2021-11-09
> **TheFu said:**
> Good question.

First, typical Windows users aren't like typical Linux users in many ways.  This means the systems aren't "exercised" the same ways.
I have a Windows install that is over 10 yrs old and working fine, so the need to do a reinstall every 6 months is obviously some need based on use patterns, not the OS.

Every 3-5 yrs, I have moved the Windows install completely to new storage, so the typical "bit rot" that seems to cause issues on Windows is mitigated by this periodic move of all the bits.
I have heard that Windows progressively gets slower over time.  I have also been told that it's due to the registry getting larger because when programs are removed from the system, they don't necesarilly get removed from the registry.

> **TheFu said:**
> Linux kernel updates are really easy and happen about 2x a month for supported released.  This is different than the WinNT kernel in Windows systems which probably gets updated at most, once a year. I honestly don't know how often this happens and would welcome specifics from someone who does.

New Linux and Windows users tend to install all sorts of junk.
Not I.  I only install programs from the software center, and then I keep my machine lean and mean.

> **TheFu said:**
> On Windows, I'd probably have to spend a few days pointing and clicking to install software and get everything setup with my settings (assuming I don't miss something), all hands-on effort. Perhaps there's an easier way, but my Windows knowledge isn't strong enough to make it easy and getting all the "setup.exe" files for each 3rd party program is a major hassle.  Then there are the OS patches which aren't available anymore for my OS (unsupported), so I think I'd be screwed trying to recreate a Windows system from 60 days ago. 
I have a Windows 7 VM that was backed up after initial install.  If anything goes wrong, I can restore that VM and all is good.

> **TheFu said:**
> 
[LIST]
[*]Avoid cruft. Install what you need, nothing more.  If something isn't needed/used anymore, remove it.
[*]Have backups that are proven to be restored. Spend the time BEFORE you need it, now.
[*]Stay on supported releases, and move to a newer, supported, release BEFORE EOL happens.
[*]Always have a "Try Ubuntu" flash drive ready to troubleshoot boot issues and to see if hardware driver issues are tied to the installed OS or Ubuntu in general. Lots of issues can be quickly resolved using this *Try Ubuntu* solution.
[/LIST]

These are great suggestions!  Thank you!

So, what everyone seems to be saying, is there is no real reason to "reinstall" a Linux OS unless you break something by tinkering.  Other than that it still continues to work well over time.  Re-installing for performance is really just a Windows problem?

---

### Post by TheFu on 2021-11-09
> **Shibblet said:**
> I have heard that Windows progressively gets slower over time.  I have also been told that it's due to the registry getting larger because when programs are removed from the system, they don't necesarilly get removed from the registry.


Not I.  I only install programs from the software center, and then I keep my machine lean and mean.


I have a Windows 7 VM that was backed up after initial install.  If anything goes wrong, I can restore that VM and all is good.


These are great suggestions!  Thank you!

So, what everyone seems to be saying, is there is no real reason to "reinstall" a Linux OS unless you break something by tinkering.  Other than that it still continues to work well over time.  Re-installing for performance is really just a Windows problem?

As I said, it isn't a Windows problem, it is a Windows-user problem or a computer hardware.  I have 10+ yr old Windows installs that run just the same as they did before --- actually faster because they been migrated to faster hardware. I don't install cruft and leave it there - just like I don't install cruft on Linux and leave it there (too often).

Of course, both OSes can become slower with failing hardware and IME, non-MS OSes tend to recognize failing hardware sooner than Windows does, so issues can happen earlier. OTOH, do you really want to work on your PhD project on hardware that is having data corruption problems for months, but that-other-OS isn't complaining, yet?  I'd want to know ASAP.

As for normal system maintenance for Linux desktops ... seems like someone should have written an article about that.   Oh - they did:
[https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282](https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282)
or the updated version: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) (last updated 2021).

I think there is something important about actually doing backups that exercises spinning storage and is preventative against future issues. It gives the HDD hardware a chance to see when reading is just starting to degrade, so the HDD will either refresh the byte or relocate it somewhere else.  Windows users tend to only backup their data files ... and only by manually copying those to flash storage, typically. They do it more often when important work is happening, but less often or not at all, when they aren't doing anything really important - sometimes for years without any backup.  

Just the fact that we do backups is helpful, I'm convinced.

---

### Post by dirtydog01 on 2021-11-29
Totally agree.

---

### Post by mikewhatever on 2021-11-29
There is no need to reinstall every 6 months. Windows users don't say and don't do that. Given the particular peculiarity of the question, I'd venture a suggestion, you should spend less time on social media platforms.

---

### Post by Tadaen_Sylvermane on 2021-11-30
> **mikewhatever said:**
> There is no need to reinstall every 6 months. Windows users don't say and don't do that. Given the particular peculiarity of the question, I'd venture a suggestion, you should spend less time on social media platforms.

Need is the wrong word. You are correct there is no need. But there are many in the Windows world who value and do nothing but benchmark and overclock stuff. To them fractions of a second count. So if Windows is slowed even slightly by the fragmentation or registry or whatever then off with it's head. These are the same people that will build a whole new machine because 80+fps isn't enough. They need 100+. To each his own...

---

### Post by Shibblet on 2021-11-30
> **Tadaen_Sylvermane said:**
> Need is the wrong word. You are correct there is no need. But there are many in the Windows world who value and do nothing but benchmark and overclock stuff. To them fractions of a second count. So if Windows is slowed even slightly by the fragmentation or registry or whatever then off with it's head. These are the same people that will build a whole new machine because 80+fps isn't enough. They need 100+.
60 FPS is perfect.  Any more you risk tearing, any less you have choppiness.

> **Tadaen_Sylvermane said:**
> To each his own...
NIL!  Gamers!!!  NIL!

J/K ;-)

---

### Post by maketopsite on 2021-12-15
No need for regular reinstall of linux distribution as other said. What you should do is delete cache files, temporary files from time to time. For example web browser's temporary files.

---

### Post by kurt18947 on 2021-12-16
> **Frogs Hair said:**
> Unless an OS installation  is corrupt and non functional in some way I don't reinstall and that includes testing new versions of Ubuntu. I also upgrade to new stable versions at times. Backup for me entails  cloning my pictures and documents to removable sources and that's all I'm concerned about. If I had a hard-drive full of movies my backup process would be different. **As a Windows user I have not heard of the reinstall every 6 months approach .** Windows 10 has been getting two build/ feature updates a year and I suppose that is when some choose to reinstall.

Back in the days of Windows on top of DOS including Win95 & 98 the reinstall every few weeks/months was recommended. If it only crashed once a week you were doing good or weren't using it much. Today I think Windows is pretty stable though I barely use it so can't really say. My primary machines are on 20.04, I don't know if I'll go to 22.04 or wait for 24.04.

---

### Post by ajgreeny on 2021-12-16
I only reinstall, or perhaps I should say install, approximately every two years, soon after the new LTS versions are released but allowing a few weeks for the immediate bugs to be squashed.

I think the last time I had to actually reinstall, ie scrap what I have and just start again with the same version, was the first time that I attempted to install in a new UEFI machine; I didn't read carefully enough at the time and rather than leave it as a BIOS install I simply scrapped the whole thing and started again.

---

### Post by Shibblet on 2021-12-16
> **kurt18947 said:**
> My primary machines are on 20.04, I don't know if I'll go to 22.04 or wait for 24.04.

I really like the changes in the Plasma Desktop, as well as the Open Source AMD Drivers in the 21.10 Release of Kubuntu.  I will happily go 22.04 when it releases.  ;-)

What sparked this question, was that I seemed to be installing an OS every 6 months or so...  20.04, 20.10, 21.04, 21.10... And I hadn't really let my OS stay on my machine for over 6 months.

I saw plenty of articles stating that you should re-install Windows 10 at least once a year.  Primarily when a new system update came out.  People claimed that it ran better with a clean install.  I just wondered if Ubuntu (or it's derivatives) had a similar issue.  But from what everyone is saying, Ubuntu doesn't work that way.

---

### Post by kurt18947 on 2021-12-16
I have an install that I use as a test machine. I use it to try out commands and software that I feel might make a machine unrecoverable or unreliable. It's probably quicker to simply reinstall than to undo the damage. No data to be concerned with so nuke and repave.

---

### Post by DuckHook on 2021-12-19
> **Shibblet said:**
> I saw plenty of articles stating that you should re-install Windows 10 at least once a year.  Primarily when a new system update came out.  People claimed that it ran better with a clean install.  I just wondered if Ubuntu (or it's derivatives) had a similar issue.  But from what everyone is saying, Ubuntu doesn't work that way.
As hard as I try to maintain a squeaky clean system, cruft invariably creeps into it. Things are way better in the last two years since I've started installing new apps into containers, but the vast majority of users don't do that, and it's hard to be so ascetic that one never tries new apps. The leftover config files, changes, orphaned libraries, and now, registry entries/changes will invariably pull a system further and further offside.

I recently experienced a frustrating example of this.

I have three different OS partitions on my main box, two of which are meant to be redundant dependable main usage OSes always running the latest LTS versions. Both partitions have their important data directories linked to the same data files (on yet another partition), so I can access the same browser history, emails, VMs, etc. no matter which partition I'm using. I try to keep both DEs as similar as possible, as simple as possible and as default as possible.

When my old video card gave up the ghost, I installed a new one that was actually too new for Focal. The default AMDGPU driver runs like a pig in a poke on this card and I had to try the proprietary binary. To my consternation, the proprietary driver installs in one OS, but not in the other. For some reason, it chokes with dependency conflicts. Therefore, although I swear the two OSes are as identical as I can make them, I have to run one OS on the inefficient FOSS driver, but get the benefit of performance and full functionality on its twin.

I must have made some change to one OS that I didn't do to the second, but for the life of me, I don't know what I did. But because I have one partition that works well, I haven't bothered to chase down the dependency conflicts on the other.

My point is that even small changes can have big consequences. Just as importantly, such changes can be so subtle that one can't even remember or guess what they are. So, a clean install can indeed give one a clean start. When Jammy is released, I will not be doing a network upgrade on the problem partition. I will instead do a virgin install. The ironic thing is that I won't need the proprietary driver with Jammy. That third partition I mentioned at the start? That is the one I use for experimentation. It has Impish on it and its native FOSS driver runs my new video card tickety&#8209;boo.
> **kurt18947 said:**
> I have an install that I use as a test machine. I use it to try out commands and software that I feel might make a machine unrecoverable or unreliable. It's probably quicker to simply reinstall than to undo the damage. No data to be concerned with so nuke and repave.
Have you considered a container or a VM? Most of us have the urge to test drive stuff, but I've found a largely trouble&#8209;free way to do so is to install the app in a VM or a container. Since these platforms have the ability to make snapshots, there's no need to even re-install. Just roll back to the previous snapshot and its like the damage never happened. I do that with all new apps these days. You might find that it saves you a lot of time.

---

### Post by kurt18947 on 2021-12-23
> **DuckHook said:**
> 
.......................
Have you considered a container or a VM? Most of us have the urge to test drive stuff, but I've found a largely trouble&#8209;free way to do so is to install the app in a VM or a container. Since these platforms have the ability to make snapshots, there's no need to even re-install. Just roll back to the previous snapshot and its like the damage never happened. I do that with all new apps these days. You might find that it saves you a lot of time.

I haven't had the time or inclination to venture into the world of VM or containers. Something for down the road I imagine.

---

