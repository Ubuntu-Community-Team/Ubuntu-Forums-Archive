---
title: "Cleanly updating the OS and all applications"
date: 2009-05-21
forum: System76 Support
---

### Post by tvrusso on 2009-05-21
Back in 2007 I bought my daughter a new panv3 (I think) to use for all her schoolwork and the various socializing she does on the net.  I think it shipped with Ubuntu 7.04 and we quickly upgraded it to 7.10.  It did *not* arrive with /home on a separate partition --- everything is in a single partition.

Since she was using it for school and I had some problems when I updated my laptop to 8.04, we decided to leave it at 7.10 for a while.  "For a while" means until now.  She's heading off to college in the fall, and I think this summer's the right time to get it cleaned up and upgraded, while she's still here with me to get it stable.  We fully intend to use 8.04 LTS rather than have her be chasing system updates for the next couple of years --- my philosophy is that if a machine is actually in heavy use for an important purpose, one shouldn't mess around with it unnecessarily.  Biennial full-system upgrades may be cool on bleeding-edge systems, but not for production machines, and certainly not for the machine my kid's going to be using at school (a nine-hour drive from home and her support staff).

Contrary to the advice I see here most of the time, I have never, ever had to do a "wipe the disk and reinstall" of Ubuntu on any of my machines.  I've incrementally updated machines all the way back from 5.04 up to 8.04 without any problem (my own laptop only from 6.10 to 8.04, but you get the point).  I could even do that on her machine, except that the panv3 actually has a processor that can run Ubuntu 64-bit, and we are still running a 32-bit version of 7.10 on it.  There is no 32-bit to 64-bit upgrade path other than reinstall.

She's been using the machine heavily for a couple of years now, and of course there's tons of data and a boatload of installed apps.  I can always just have her burn CDs of her important data and then start from scratch, but I was kinda hoping to do it more cleverly than that.  But I'm not really clear on how I can best do so.  Asking for some advice.

I was kinda hoping to do this:


[LIST=1]
[*]copy the contents of /home onto some off-line storage (I have a 1TB external drive I could use for that)
[*]Somehow get a  list of installed applications so that I can simply "apt-get install" them *en masse* after the reinstallation of the OS.  Obviously, I'd save this list off-line, too.
[*]Do a full install of 64-bit 8.04, partitioning the drive with a 15GB / partition and the rest as /home
[*] copy back the /home data I'd stored off-line
[*] reinstall System76 driver and any existing restricted drivers 
[*] use the list prepared above as a script to reinstall the installed applications --- there are many, and I'd hate to have to reconstruct that manually.
[/LIST]

Since the thought of wiping a drive to do a system upgrade is so scary to me I want to maximize the safety factor before starting.  So I'm soliciting advice on:

[LIST=1]
[*]most effective/safe backup method to assure that /home is archived properly (I'd use dump and restore if /home were its own partition, but it's not)
[*]best way of recording the list of installed applications so they can be re-installed with apt-get most easily
[/LIST]

Also, does it really buy me (her, actually) anything of value to move to 64-bit OS rather than 32-bit on the panv3?  If not, I'll just do the in-place upgrade from 7.10 to 8.04 32-bit, because I am very comfortable with that process and it has always worked Just Fine for me on several other old 32-bit machines.

---

### Post by riseringseeker on 2009-05-21
> **tvrusso said:**
> 

[LIST=1]
[*]best way of recording the list of installed applications so they can be re-installed with apt-get most easily
[/LIST]


```
dpkg --get-selections | grep -v deinstall > installed-packages
```
Will get you a list of *ALL* currently installed programs, will get back to you on the rest.

---

### Post by tvrusso on 2009-05-21
> **riseringseeker said:**
> ```
dpkg --get-selections | grep -v deinstall > installed-packages
```
Will get you a list of *ALL* currently installed programs, will get back to you on the rest.


Very nice.  That's the sort of thing I was looking for.  I can then pick through this output to remove stuff like kernel packages and other stuff that shouldn't be reinstalled after the upgrade, but this is very nice as a starting point.

---

### Post by octathlon on 2009-05-21
This page has nice instructions on how to reinstall all packages after a fresh OS install.  I haven't tried it though!
[http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html](http://www.ubuntugeek.com/howto-reinstall-all-of-currently-installed-packages-in-fresh-ubuntu-install.html)

I also have a panv3 that came with Feisty in a single LVM partition, which I didn't like. If it had been a regular partition I would have resized it to make the separate /home but instead I just waited until I was ready to install Hardy.  I'm probably going to stay with Hardy until the next LTS version comes out.

I used sbackup (Simple Backup) to back up my files before the new install and saved it to 2 different locations just in case.  The nice thing about Hardy is that everything works without needing to run the System76 driver.

---

### Post by theozzlives on 2009-05-21
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5")
They showed you how to make the list, this will show you how to restore. Now to backup, it can be modified to just /home:
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by riseringseeker on 2009-05-22
> **tvrusso said:**
> Very nice.  That's the sort of thing I was looking for.  I can then pick through this output to remove stuff like kernel packages and other stuff that shouldn't be reinstalled after the upgrade, but this is very nice as a starting point.

You might try rsync as a backup as well, I use it quite a bit.  To backup the home directory here is the code (though I am sure someone will comment on the parameters that I use, which is fine)

```
rsync -avvun /home /media/disk
```

This assumes that you have a USB drive plugged in and it is located at /media/disk.  The above code will make a "dry run" without actually copying any data.  To make it run for real, remove the "n" from "-avvun".

To restore, it basically just the reverse, but add a trailing slash in the source.  

[quote=man rsync] A trailing slash on the source changes this behavior to avoid  creating an  additional  directory level at the destination.  You can think of a trailing / on a source as meaning “copy the contents of this directory” as  opposed  to  “copy  the  directory  by name”, but in both cases the attributes of the containing directory are transferred to the containing  directory on the destination.  In other words, each of the following commands copies the files in the same way, including their setting of the attributes of /dest/foo:
[/quote]

---

### Post by jdb on 2009-05-22
> **riseringseeker said:**
> You might try rsync as a backup as well, I use it quite a bit.  To backup the home directory here is the code (though I am sure someone will comment on the parameters that I use, which is fine)

```
rsync -avvun /home /media/disk
```

This assumes that you have a USB drive plugged in and it is located at /media/disk.  The above code will make a "dry run" without actually copying any data.  To make it run for real, remove the "n" from "-avvun".

To restore, it basically just the reverse, but add a trailing slash in the source.

What's really nice about rsync is after the initial backup, only things that have changed are transferred.
If you use it often it is really fast.

jdb

---

### Post by riseringseeker on 2009-05-25
> **tvrusso said:**
> 
I was kinda hoping to do this:


[*]copy the contents of /home onto some off-line storage (I have a 1TB external drive I could use for that)

There are a number of ways to do so, as I've said, rsync would be my tool of choice, but use what works for you and what you are comfortable with.  You may want to check into debmirror...

If there is enough room left on the drive, you do not have to put it on an external (but it can't hurt).  You could just use gparted to create a new partition and copy the file to there.

> [*]Somehow get a  list of installed applications so that I can simply "apt-get install" them *en masse* after the reinstallation of the OS.  Obviously, I'd save this list off-line, too.

Covered in a previous post.  BTW, the command I gave will list [b]all[/b[ of the installed apps, including the ones installed by default but making a script from the entire list should not cause a problem, as it should skip the ones already installed saying they are already up to date.

> [*]Do a full install of 64-bit 8.04, partitioning the drive with a 15GB / partition and the rest as /home

Should be no problem.

> [*] copy back the /home data I'd stored off-line

Be careful with what items you attempt to restore, some of the settings do not import well from 32 to 64 bit.  All of the files (music, videos, documents) of course is no problem.

> [*] reinstall System76 driver and any existing restricted drivers 

Quite easy using [_[COLOR="Blue"]these[/COLOR]_]("http://knowledge76.com/index.php/Restoring_Your_System") instructions

> [*] use the list prepared above as a script to reinstall the installed applications --- there are many, and I'd hate to have to reconstruct that manually.

Again, should be able to use the entire list - which will save a bunch of sorting.  If it's installed by default, it won't reinstall it, it should just say "already latest version" or words to that effect.


> Since the thought of wiping a drive to do a system upgrade is so scary to me I want to maximize the safety factor before starting.

It's not as scary as it seems, and something I and many other users do here every 6-12 months.

> Also, does it really buy me (her, actually) anything of value to move to 64-bit OS rather than 32-bit on the panv3?  If not, I'll just do the in-place upgrade from 7.10 to 8.04 32-bit, because I am very comfortable with that process and it has always worked Just Fine for me on several other old 32-bit machines.

I'll let others answer this.  There is no downside at least, how much of a gain you get....?  Tom, care to chime in?

---

### Post by thomasaaron on 2009-05-26
> Also, does it really buy me (her, actually) anything of value to move to 64-bit OS rather than 32-bit on the panv3? If not, I'll just do the in-place upgrade from 7.10 to 8.04 32-bit, because I am very comfortable with that process and it has always worked Just Fine for me on several other old 32-bit machines.

The biggest reason to switch to 64-bit on the PanV3 is that there is a bug with the cpu fan-speed in 32-bit. This *only* occurs after resuming from suspend or hibernate and causes the computer to over heat. The bug is not present in 64-bit.

Other than that, 32-bit is great on the PanV3, though 64-bit may have a slight speed advantage, since the PanV3 has a 64-bit architecture.

---

### Post by tvrusso on 2009-05-26
Thank you for all the great replies.  I'm sorry I have only just gotten back on to the forums after the holidays and hadn't thanked you all yet.

There's a lot of good stuff here, and I think I'll be in good shape to get the upgrade done.

thomasaaron: after getting the panv3 we had serious trouble with suspend/resume and I'd worked with you to try to get it working.  We never did get it -- the thing would just hang with "Linu" in the top left corner.  After that, my daughter just never suspended the machine --- either left it running on AC or shut it down when not in use.  Next time she's here with it we'll check out whether it's working after all the upgrades that have been applied to it.  I don't think it worked last time we tried it, but that was a long time ago.

---

### Post by drewbenn on 2009-05-27
> **tvrusso said:**
> after getting the panv3 we had serious trouble with suspend/resume and I'd worked with you to try to get it working.  We never did get it -- the thing would just hang with "Linu" in the top left corner.  After that, my daughter just never suspended the machine --- either left it running on AC or shut it down when not in use.  Next time she's here with it we'll check out whether it's working after all the upgrades that have been applied to it.  I don't think it worked last time we tried it, but that was a long time ago.

My panv3 never suspended well when I got it (the behavior you mentioned seems familiar) so I never bothered using it.  Since installing 64-bit 9.04 I've started using it and it's been working great.

Unrelated: other people have mentioned getting a list of installed packages and then installing them on the new system; some of them may be 32-bit-specific (e.g. have a '-32' in their name); there's a chance you could run into issues (missing functionality is probably the worst) if you blindly install from that list.

Finally, don't forget to export your bookmarks (if you keep them in your web browser instead of online)!  That's the one thing I always forget to save (also the list of my open tabs).  I think there are two formats you can use for exporting bookmarks; one of them I always have problems with.

---

