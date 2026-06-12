---
title: "Why Do a Clean Install?!?!"
date: 2007-06-29
forum: The Cafe
---

### Post by Mike-97470 on 2007-06-29
Some of you may be wondering why you might want to do a Clean Install rather than just letting the Package Manager do an update whenever the Ubuntu distro is revised.

Doing a Clean Install is easy:
1. Just download the new distro's iso and burn it onto a CD.  Of course, check that the CD boots.
2. Copy your Home folder on whatever you use for backups.  Of course, the Home folder includes all of your important personal info.
3. Boot up the CD you burned to the Live CD desktop.
4. When the Live CD Ubuntu desktop appears, just double-click the little disk icon to start the install process--it's really straightforward and even includes disk partitioning.
5. After the install process completes, just copy all of your personal stuff back into the Home folder.

See, isn't that easy?  Now here is why you should do a Clean Install:
1. You get rid of all those old Linux Kernels that are just hibernating or vegetating or whatever somewhere, and you don't even have to go find them, probably in /BOOT.  They'll be gone from GRUB's OS selection menu, too.
2a. When your disks won't mount because their names or types or whatever got changed to UUIDs or sdx's got changed to hdx's:  The Clean Install will figure things out nicely without getting itself horribly confused trying to remember how it used to do it and how that translates into how it now wants to do it.  You'll even be able to use your optical drives.
2b. Another nice thing is that the Swap partition will actually be used, and believe it or not,  that is really a good thing.
3. You'll free up a bunch of disk space by getting rid of all that software you installed and have forgotten about and will never use again.
4. You'll clear out all of the Cookies from your browser (who like Cookies, anyway) and Bookmarks as well (who needs them?  -- search engines rule!) and all of those useless extensions and some that are useful, too.
5. You'll clear out all of that old email that is such a clutter!  And best of all you'll clear out your calender and contact list.  If it's important, you should already know where and when to go, and for true friends it shouldn't be too difficult to memorize their phone numbers and addresses; you should have then written down in a book somewhere anyway!

---

### Post by tgm4883 on 2007-06-29
> **Mike-97470 said:**
> Some of you may be wondering why you might want to do a Clean Install rather than just letting the Package Manager do an update whenever the Ubuntu distro is revised.

Doing a Clean Install is easy:
1. Just download the new distro's iso and burn it onto a CD.  Of course, check that the CD boots.
2. Copy your Home folder on whatever you use for backups.  Of course, the Home folder includes all of your important personal info.
3. Boot up the CD you burned to the Live CD desktop.
4. When the Live CD Ubuntu desktop appears, just double-click the little disk icon to start the install process--it's really straightforward and even includes disk partitioning.
5. After the install process completes, just copy all of your personal stuff back into the Home folder.

See, isn't that easy?  Now here is why you should do a Clean Install:
1. You get rid of all those old Linux Kernels that are just hibernating or vegetating or whatever somewhere, and you don't even have to go find them, probably in /BOOT.  They'll be gone from GRUB's OS selection menu, too.
2a. When your disks won't mount because their names or types or whatever got changed to UUIDs or sdx's got changed to hdx's:  The Clean Install will figure things out nicely without getting itself horribly confused trying to remember how it used to do it and how that translates into how it now wants to do it.  You'll even be able to use your optical drives.
2b. Another nice thing is that the Swap partition will actually be used, and believe it or not,  that is really a good thing.
3. You'll free up a bunch of disk space by getting rid of all that software you installed and have forgotten about and will never use again.
4. You'll clear out all of the Cookies from your browser (who like Cookies, anyway) and Bookmarks as well (who needs them?  -- search engines rule!) and all of those useless extensions and some that are useful, too.
5. You'll clear out all of that old email that is such a clutter!  And best of all you'll clear out your calender and contact list.  If it's important, you should already know where and when to go, and for true friends it shouldn't be too difficult to memorize their phone numbers and addresses; you should have then written down in a book somewhere anyway!

:shock:  Are you joking?  The beginning sounded like it was serious, but once I started reading the second part (about why you should do a clean install) it read more like a joke.  

1.  All those old kernels?  Maybe 1 and it's not really a problem.
2.  Dont know about this
3.  Unused software?  I usually uninstall this when I know its crap so there isn't any software I don't want.  However if I do a clean install I will have to reinstall all my software.
4.  Bookmarks are nice to have, but since I have foxmarks a clean install isn't a problem.  Cookies, I guess clearing private data would get rid of those.
5.  Old email, I delete it when it's not needed anymore.  Calendar and contact list, i hope your kidding.

This reads both as serious and a joke.  You should be more clear as to which it is as new people might actually trust this as valuable information

---

### Post by bodhi.zazen on 2007-06-29
Moved to the cafe for obvious reasons.

---

### Post by Polygon on 2007-06-29
i do a clean install because sometimes the upgrades through update-manager are not perfect and some stuff gets screwed up... like the dapper to edgy upgrade. not pretty; x failed to start, lots of fsck errors, etc etc etc.

---

### Post by %hMa@?b&lt;C on 2007-06-29
I always do a clean install.  I back up anything that I need on my second hard drive.

---

### Post by Incense on 2007-06-30
I just keep a separate  /home partition. No worries about what kind of install I do, all my data is still hanging out on my drive. Plus it will hang on to my desktop settings, so I don't have to spend time reconfiguring everything.

---

### Post by starcraft.man on 2007-06-30
I do one clean install every release. Then I drive image the OS and everything else on it (excluding data) and thats my one save for the whole six months, I mess anything up, poof I restore. I've always done clean installs, I did them when I used Windows, I do them when I use linux. Old habit, also IMO leads to less complications.

---

### Post by Mike-97470 on 2007-06-30
Ok, just to clarify: my original post is not a joke . . . 
And yes I lost email and contacts which are more or less important--calendar info could be important as well.  Evolution keeps this stuff squirreled away in some secret place other than /home.

The point of all this is that all personal info should be in the user's home directory.  I would like to see Firefox and Evolution do that.

The GRUB menu gets really untidy with 8-10 obsolete kernels after a couple of years of upgrades.  And yes, it's possible to clean them out manually.

A Clean Install is what I'll do from now on.  7.04 proved it to me after wasting countless hours reading _numerous forum posts and complaints about disk mount problems, I never did get my CD/DVD drives completely working again. . . So backup the Evolution data and /home and then do a Clean Install!

---

### Post by tbroderick on 2007-06-30
> **Mike-97470 said:**
> 
The point of all this is that all personal info should be in the user's home directory.  I would like to see Firefox and Evolution do that.

Unless you are running those programs as root, they already store their settings in /home. Firefox is ~/,mozilla and Evolution is most likely in ~/.gnome2 or something. I'm not sure as I don't use it.

---

### Post by SoulinEther on 2007-06-30
You missed the step of making a separate home directory... keep 10-20 gigs for your / directory depending on how much you use, or how much mail you plan on receiving with Evolution if what you're saying is right :)

---

### Post by Polygon on 2007-06-30
evolution is very stupid if it keeps all of your mail somewhere other then your home. I mean, thats where it SHOULD go, every other linux program stores personal data there, lol

and yeah firefox stores its stuff in ~/.mozilla/

i keep 10 gb for root and i have never run out yet, i have like half available right now, and i do install a lot of stuff.

---

### Post by tgm4883 on 2007-06-30
> **Mike-97470 said:**
> 
The GRUB menu gets really untidy with 8-10 obsolete kernels after a couple of years of upgrades.  And yes, it's possible to clean them out manually.


Are you saying when you upgrade kernels it always leaves the old kernels there or when you upgrade distros it leaves the old distro kernels there?

BTW, I see your from Oregon, you should check out the LoCo Teams for Oregon and the Pacific NorthWest

[https://wiki.ubuntu.com/PNWTeam](https://wiki.ubuntu.com/PNWTeam)
[https://wiki.ubuntu.com/OregonTeam](https://wiki.ubuntu.com/OregonTeam)

---

### Post by Obor on 2007-06-30
> **tgm4883 said:**
> Are you saying when you upgrade kernels it always leaves the old kernels there or when you upgrade distros it leaves the old distro kernels there?


I don't know about when you upgrade distro to a new version but a normal kernel update doesn't remove the old kernel. You can always do it from synaptic by searching for linux-image (which is what I do as I don't have a lot of spare space on my laptop, kernel takes about 80MB so its not a big deal on desktops i guess)

---

### Post by PatrickMay16 on 2007-06-30
I've had the same system running for almost two years without reinstalling once. I can say that updating is better than clean installing.

---

### Post by Mike-97470 on 2007-06-30
Thanks for all the help and good advice!

To clarify about obsolete kernels:  when a new Ubuntu version is upgraded by the package manager, old kernels remain in /boot.  When a new kernel is installed by the package manager, old kernels remain in /boot.  They all show up in the GRUB menu although there is a parameter somewhere that controls how many--it's set fairly high.

Actually, I'm in Eugene.  Yes, it would be fun to attend some Ubuntu festivities, but I try to have a life--maybe that would be one.

Everyone automatically has a /home with data from one or more user account(s).

(to tbroderick)
Thanks for the right answer!  Actually, I woke up this morning knowing that my /home/mike folder on the backup drive wasn't showing the hidden folders/files and suspected that .evolution would be there--of course it is as well as .mozilla.  (I did find it there a couple of months ago when I was trying (unsuccessfully) to get Unison to sync it with my laptop.)

So what screwed me up?
1. Somewhere along the way many months ago nautilus switched from defaulting to not show hidden files to show hidden files.  Then with the Feisty clean install, it switched back to not display hidden files.  Since I had learned to expect to see all folders/files I just copied documents/music/photos etc back from my /home/mike and didn't see the "secret" hidden stuff.  Does anyone know how to control the Nautilus hidden file default?
2. I can understand why /home has root permissions, but my user folder /home/mike doesn't and yet when I tried to copy it from the (usb) backup drive, I couldn't.  That's why I started copying its subfolders/files. 

That's about it.

---

### Post by M$LOL on 2007-06-30
I can't imagine just deleting all my bookmarks, the amount of stuff I have stored with them is huge. I'd like to see you try to find all the stuff I have stored using a search engine.

---

### Post by tgm4883 on 2007-06-30
> **Obor said:**
> I don't know about when you upgrade distro to a new version but a normal kernel update doesn't remove the old kernel. You can always do it from synaptic by searching for linux-image (which is what I do as I don't have a lot of spare space on my laptop, kernel takes about 80MB so its not a big deal on desktops i guess)

> **Mike-97470 said:**
> To clarify about obsolete kernels:  when a new Ubuntu version is upgraded by the package manager, old kernels remain in /boot.  When a new kernel is installed by the package manager, old kernels remain in /boot.  They all show up in the GRUB menu although there is a parameter somewhere that controls how many--it's set fairly high.


My system must be broken then cause it keeps one old kernel and the new kernel.  It removes all other old kernels.  I'm assuming this is done through the meta package, if you manually install other kernels they will stay until you remove them.

---

