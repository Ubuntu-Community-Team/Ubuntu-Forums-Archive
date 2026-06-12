---
title: "How do you upgrade to a new release?"
date: 2011-04-29
forum: The Cafe
---

### Post by aphatak on 2011-04-29
A lot of people appear to be having trouble with upgrade to 11.04.  I have noticed a couple of things that make an OS upgrade less painful than usual.  What *I* always do is -
[LIST=1]
[*]Create a new partition (well, not exactly; I always keep an unformatted 20GB partition on the disk)

[*]Do a fresh install of the 'upgrade' on this new partition.  When you are asked, refuse to have GRUB installed.  Keep the old crawler alive yet.

[*]Boot into the pre-upgrade version (hereinafter referred to as old trusty).  Put old trusty through its paces, and make sure that has not been clobbered.  Finally, run 'sudo update-grub'.

[*]Restart.  At the GRUB menu, when you see a selection of operating systems to boot, make sure the auto OS-load is not operating (something as simple as clicking the down-arrow key will do).  Then say your prayer (preferably the Programmer's Prayer).  Boot into the new version.

[*]If you reach the log-in screen, let your breath out.

[*]Put the new OS through its paces.  If you notice any bugs, stop immediately, and back slowly away from the keyboard - make no sudden movements, and avoid making loud noises.  If you do not notice any bug, and this is the first time you are in the new version, see your psychiatrist immedediately, and get treated to be connected back to reality.  If, after the first week, you find no bug (or more realistically, have all work-arounds in place), go to step 10.

[*]Lick you wounds, restart and go back to old trusty.

[*]Get into Ubuntu Forum, and look for a solution.  If you don't find a solution, go back to work.  Repeat this step until you find a bug-fix you understand, and feel confident with.

[*]Restart, and log into the new version.  Put the bug-fix in.  Then go back to step 6 for more beating.

[*]Log into the new version, and re-install GRUB.  Make sure the new version is the default, that old trusty is still reachable - just in case, and that all the GRUB files are present in your new version's /boot and /etc directories.

[*]Use your new version from this point on - but don't kill the old one for at least four weeks.

[*]When you feel comfortable that the new version is not going to eat your data, back up old trusty's partition, erase old trusty and do 'sudo update-grub' again.  A good indication that the time to do this is right is when the hair you tore out during steps 6 to 9 has grown back.
[/LIST]

Sound paranoid?  Perhaps there is some truth in that.  But as far as I am concerned, don't trust Version 1.0 of anything, and never trust anything with a microchip in it.  And I have survived so far!

Oh, did you say you don't know what the Programmer's Prayer is?  Well, it's the one that goes "O Omniscient OS who art in core, give us this day our daily share of bugs ...".  I'm sure you remember it, don't you?

---

### Post by jerenept on 2011-04-29
1) Install Ubuntu 10.04.
2) Upgrade to Maverick Alpha
3) Upgrade to Natty Alpha
4)????
5) Boast on UbuntuForums about having Natty before everyone else.

^^This is what I do.

---

### Post by juancarlospaco on 2011-04-29
sudo do-release-upgrade --sandbox  #Test upgrade with a sandbox aufs overlay

---

### Post by Primefalcon on 2011-04-29
I installed 10.04 on this system and did and update-manager -d for both 10.10(upgraded during the last alpha) and 11.04(updated day before release)

---

### Post by danbuter on 2011-04-29
Since I don't use Linux on my main computer, I just wipe the drive and install the new release. Never had any issues.

---

### Post by el_koraco on 2011-04-29
> **danbuter said:**
> Since I don't use Linux on my main computer, I just wipe the drive and install the new release. Never had any issues.

+1
I use it on the main system, but have everything backed up and ready to transfer in 20 minutes.

---

### Post by cariboo on 2011-04-29
I always have two installs on my main system, I usually do fresh installs during the testing sessions, but as the release gets closer, I just keep updating until I have the final release. Having two installs, it's just a matter of copying the files I want to keep from one home directory to the other. I also do rsync backups daily, just in case.

---

### Post by wolfen69 on 2011-04-29
> **aphatak said:**
> A lot of people appear to be having trouble with upgrade to 11.04.  I have noticed a couple of things that make an OS upgrade less painful than usual.  What *I* always do is -
[LIST=1]
[*]Create a new partition (well, not exactly; I always keep an unformatted 20GB partition on the disk)

[*]Do a fresh install of the 'upgrade' on this new partition.  When you are asked, refuse to have GRUB installed.  Keep the old crawler alive yet.

[*]Boot into the pre-upgrade version (hereinafter referred to as old trusty).  Put old trusty through its paces, and make sure that has not been clobbered.  Finally, run 'sudo update-grub'.

[*]Restart.  At the GRUB menu, when you see a selection of operating systems to boot, make sure the auto OS-load is not operating (something as simple as clicking the down-arrow key will do).  Then say your prayer (preferably the Programmer's Prayer).  Boot into the new version.

[*]If you reach the log-in screen, let your breath out.

[*]Put the new OS through its paces.  If you notice any bugs, stop immediately, and back slowly away from the keyboard - make no sudden movements, and avoid making loud noises.  If you do not notice any bug, and this is the first time you are in the new version, see your psychiatrist immedediately, and get treated to be connected back to reality.  If, after the first week, you find no bug (or more realistically, have all work-arounds in place), go to step 10.

[*]Lick you wounds, restart and go back to old trusty.

[*]Get into Ubuntu Forum, and look for a solution.  If you don't find a solution, go back to work.  Repeat this step until you find a bug-fix you understand, and feel confident with.

[*]Restart, and log into the new version.  Put the bug-fix in.  Then go back to step 6 for more beating.

[*]Log into the new version, and re-install GRUB.  Make sure the new version is the default, that old trusty is still reachable - just in case, and that all the GRUB files are present in your new version's /boot and /etc directories.

[*]Use your new version from this point on - but don't kill the old one for at least four weeks.

[*]When you feel comfortable that the new version is not going to eat your data, back up old trusty's partition, erase old trusty and do 'sudo update-grub' again.  A good indication that the time to do this is right is when the hair you tore out during steps 6 to 9 has grown back.
[/LIST]

Sound paranoid?  Perhaps there is some truth in that.  But as far as I am concerned, don't trust Version 1.0 of anything, and never trust anything with a microchip in it.  And I have survived so far!

Oh, did you say you don't know what the Programmer's Prayer is?  Well, it's the one that goes "O Omniscient OS who art in core, give us this day our daily share of bugs ...".  I'm sure you remember it, don't you?

Too much information to begin with. As long as you have your most important stuff backed up twice on seperate drives, you can have fun and install the latest and greatest on a whim. That's why I'm computer knowledgeable, because I keep all important stuff "untouchable", and have a drive for testing, a drive for my current stable linux install, and a drive for games in windows. Why is that so hard to do? 

Seems like alot of regular users who only have 1 hard drive and 1 computer complain. If I don't like something, meh, I just use something else, knowing my beloved media, photos, etc. are locked away and safe. It then gives me the opportunity to explore.

Btw, why is everyone looking for the perfect OS when it doesn't exist? Just keep your important data safe and have fun. Geez, it's only an operating system, not life and death.

---

### Post by Spice Weasel on 2011-04-30
Use a separate /home partition, clean it up before updating then just do a fresh install on / leaving /home intact. 

I have never have good experiences with distribution updaters of any kind.

---

