---
title: "md5sum error installing flashplugin from official repo"
date: 2007-07-14
forum: Repositories &amp; Backports
---

### Post by kpkeerthi on 2007-07-14
Just noticed some problem viewing flash. Tried to reinstall but it won't. md5 checksum doesn't appear match. Looks like the repo needs to be fixed.
```

XXXXXXXXX:~$ sudo aptitude reinstall flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  flashplugin-nonfree 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 15.5kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com feisty-proposed/multiverse flashplugin-nonfree 9.0.48.0.0ubuntu1~7.04.0 [15.5kB]
Fetched 15.5kB in 0s (21.6kB/s)       
Preconfiguring packages ...
(Reading database ... 143246 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.0ubuntu1~7.04.0 (using .../flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.0_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.48.0.0ubuntu1~7.04.0) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
**md5sum mismatch install_flash_player_9_linux.tar.gz**
The Flash plugin is NOT installed.

```

---

### Post by yabbadabbadont on 2007-07-14
Try this instead: ```
sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by jsteidl on 2007-07-14
Still the same here :-/
```

 2200K .......... .......... .......... .......... .......... 88%  371.07 KB/s
 2250K .......... .......... .......... .......... .......... 90%    1.59 MB/s
 2300K .......... .......... .......... .......... .......... 92%  260.67 KB/s
 2350K .......... .......... .......... .......... .......... 94%  328.71 KB/s
 2400K .......... .......... .......... .......... .......... 96%    1.53 MB/s
 2450K .......... .......... .......... .......... .......... 98%  232.95 KB/s
 2500K .......... .......... .......... .......... .......   100%  218.83 KB/s

00:34:34 (300.66 KB/s) - »./install_flash_player_9_linux.tar.gz« gespeichert [2608602/2608602]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

jsteidl@diego:~$ 

```

it is a new feisty-install, installing from original repos. any thoughts? :)

---

### Post by yabbadabbadont on 2007-07-14
See [here](http://ubuntuforums.org/showpost.php?p=3013930&postcount=3) for a work around.

---

### Post by kpkeerthi on 2007-07-15
Purged and installed it again. Worked fine now. Thanks.

---

### Post by midtown on 2007-07-16
The purge and reinstall didn't fix anything for me, but following the workaround did, thanks! Before doing this, Firefox would crash every time I went to a page with a flash element. No messages or anything, it would just close instantly. Is there no better way for this to be handled?

But, more importantly, why the heck is there an md5sum mismatch on a new Feisty install from an official repository?

---

### Post by JSpaceCadet on 2007-07-16
Hello all,
Midtown has an excellent point.  Why is there a problem (regardless of what it is) in the production repository?  I thought that anything that went in there had been through some sort of QA (though I'm not sure who would do that).
Regardless, if the new version is intended to go into the current repository, can it just be reprocessed and added again?

I have been scripting an Edubuntu install that deals with installing much the commonly used things (FlashPlayer, RealPlayer, QuickTime, various sound functions, servers) of what the distribution either doesn't include or doesn't have enabled.  Because there are so many things like this, where you have to manually go get something, and that will change in a few days so you can do it automated, the scripting is next to useless, though it will be a great primer on how to do a lot of these things.  When I consider that I'm wanting to put 10 to 20 boxes a week out the door to go to special-needs kids, I need the automation or I have to spend much of my time to silly manual-installation things.  Automation is the way.
There is a lot to be said for consistency.  The problem is that things can run consistently smooth, or consistently very rough.  I'm for pushing toward consistently smooth.  If there is something *I* can do to help, someone please let me know.  It is in all our best interests if we want to see this process and product succeed.

Joe

---

### Post by tripleee on 2007-07-17
Long story short: Adobe updated the tar.gz file and the installer script now refuses to install it, thinking it got corrupted or something.  Perhaps it's overtly cautious, but it works as designed.

A fix is pending, and should (YMMV) be out in a few days.  In other words, try again next week. *(Actually, see my followup below.)*

See also [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125131](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125131)

> **JSpaceCadet said:**
> Why is there a problem (regardless of what it is) in the production repository?

You are referring to a package in the "multiverse" repository, sir, not the "production repository".

As the name indicates, the Flash player is "nonfree", and thus doesn't get into the main Ubuntu repository.  In fact, because of Adobe's license, the way it works is it downloads Adobe's installer and tries to run that sort of inside Apt.  This is a fragile approach, but the license dictates these things.  Unlike lots of other software, you cannot in fact build, install, and test your own static version like with basically all Ubuntu packages (and later ship an upgrade when a new version of the player ships -- a consequence of this architecture is that what Apt looks at is just the version of this Apt installer thingy, not what actual Flash player version you have).

The person who scripted this decided to take the cautious path, and refuse to install if the Adobe installer he had confirmed to be working could not be downloaded.  Agreed, there's a lot to say about an installer script which doesn't give you an option to try your luck with a newer version but (to a point) certainly it's more foolproof this way.  That's the flip side of a rigorous QA process, not -- like you seem to be inferring -- the result of a lack of process.

---

### Post by tripleee on 2007-07-17
> **tripleee said:**
> A fix is pending, and should (YMMV) be out in a few days.

Actually, I don't know what the timetable is from moving things from "feisty-proposed" to "feisty-updates".  Maybe it could take a lot longer than that.  However, if you don't mind being a tiny wee bit closer to the bleeding edge of Feisty (not a thrilling concept; the real bleeding edge is Gutsy anyway) then you can get it today, just by enabling the "feisty-proposed" updates in your Apt settings.  (System > Administration > Software Sources > Updates tab)

Contrary to what I sort of expected, I didn't even need to do the purge and then reinstall dance.

> **JSpaceCadet said:**
> If there is something *I* can do to help, someone please let me know.  It is in all our best interests if we want to see this process and product succeed.

What comes to mind is: investigate why you don't currently prefer a properly free Flash player, and what you could do to help solve those issues (or switch today, if you don't find any issues).  Getting the non-Adobe player into shape, to the point where most people prefer it to the Adobe one, is the only real solution; then it could be included in Ubuntu proper, with a proper QA process etc (and/or perhaps help persuade Adobe to change their license).

I can't personally comment on whether Gnash or Swfdec should be the focus of open-source Flash development.  Any hints from anyone here?

---

### Post by midtown on 2007-07-17
> **tripleee said:**
> What comes to mind is: investigate why you don't currently prefer a properly free Flash player, and what you could do to help solve those issues (or switch today, if you don't find any issues).  Getting the non-Adobe player into shape, to the point where most people prefer it to the Adobe one, is the only real solution; then it could be included in Ubuntu proper, with a proper QA process etc (and/or perhaps help persuade Adobe to change their license).

I can't personally comment on whether Gnash or Swfdec should be the focus of open-source Flash development.  Any hints from anyone here?

Personally I tried Gnash first, but it didn't seem to work well enough to be functional for the sites I needed.

Should Gnash be a somewhat usable implementation of flash and if so, is there a place to report specific sites that are broken with it? Sorry if this is off topic.

Thanks for everyone's hard work!

---

### Post by tripleee on 2007-07-18
> **midtown said:**
> Should Gnash be a somewhat usable implementation of flash and if so, is there a place to report specific sites that are broken with it? Sorry if this is off topic.

For Ubuntu, report any bugs at [https://bugs.launchpad.net/ubuntu/+source/gnash/](https://bugs.launchpad.net/ubuntu/+source/gnash/)

The upstream site is [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/) and it still says "alpha" but there's also a list of things which are supposed to be working.  (There's always a slight delay between the upstream "latest" version and what's packaged in Ubuntu; if you run Feisty, expect to be a version or two behind the upstream, for an actively developed project.)  The bug tracker at [https://savannah.gnu.org/bugs/?group=gnash](https://savannah.gnu.org/bugs/?group=gnash) certainly seems to have a good number of bugs related to badly working sites.  Perhaps I'd only report to the Ubuntu maintainer as a first step, though, and then follow up to the upstream if the Ubuntu maintainer doesn't seem responsive.

---

### Post by r.stiltskin on 2007-08-29
I'm having the same problem in Edgy: 
/flashplugin-nonfree_9.0.31.0.1ubuntu1~edgy1_i386.deb
fails with an md5sum error.

Is there a fix available for Edgy, or is the best solution to download the installer directly from Adobe & run it in a terminal?

---

