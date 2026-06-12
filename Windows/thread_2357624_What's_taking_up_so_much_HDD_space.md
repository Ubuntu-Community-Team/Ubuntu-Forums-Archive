---
title: "What's taking up so much HDD space?"
date: 2017-04-04
forum: Windows
---

### Post by random turnip on 2017-04-04
I'm about to install Ubuntu on an older machine currently running Vista.  I booted it up to clear some HDD space and there is basically no data left on it and barely any programs, yet it's still using over 100GB!  Surely that can't just be Vista, can it?
I planned on reducing how much space Vista was using as much as possible to give the ubuntu partition as much as possible, but other than uninstalling pretty much everything I don't really know what to do.  Is there a way I can check other than manually looking through all the folders on the C drive.

The other thing was I wanted to make a back-up disc in case something horrible happens, but don't want to back up 100GB of stuff.

I am planning on defragging tonight (started last night but gave up cause it hadn't been done in about 4 years and it was taking a long time) to see if that helps, but I can't see it making much difference.

---

### Post by TheFu on 2017-04-04
If you don't want to lose anything, then you need a backup.

I found a "thin" vista home to require 60G. That's with about 10 specific programs (FF, Teracopy, putty, quicken, ....) and ZERO data stored on the Windows drives. I also clean old windows installs, old patches, temporary files, and RAM caching files that Windows likes to leave around in assorted places.

To be fair, Linux will leave cache files around too, but they are always under the HOME for the userid. Creating a new userid and using it is all that is needed to start fresh on Linux.

You need a backup regardless. It is a $45 issue to buy an external USB3 HDD big enough to backup everything. Any you'll be able to reuse it for backups in the future.

---

### Post by random turnip on 2017-04-04
Ah so maybe 100gb isn't so ridicules.  I do have a 1TB HDD lying around to be fair with enough room on it to back that up i think, so may as well use that.
Will the backup using the default windows tool take up the same 100gb or will it compact it at all?

---

### Post by TheFu on 2017-04-04
How you should backup completely depends on how you plan to restore and the purpose of the backup.  If you want to restore everything back the way it is now, that is a different problem than if you just want data and documents.

If you backup using a specific windows tool, then I'd expect the restore **absolutely must** use that same tool. That requirement is pretty normal in the proprietary world and for some F/LOSS answers too.

If you want/need to restore the files onto a Linux machine, then perhaps using a Linux tool would be smart for the backup?

---

### Post by random turnip on 2017-04-05
Well mostly I'm worried about something going wrong with the linux install, so I want some way to re-install vista if I really need to? Anything I can do for that? Other than that there isn't much worth backing up.

---

### Post by TheFu on 2017-04-05
I suspect the best place to get answers for how to backup and restore a Windows install is NOT on an Ubuntu forum. I'm fairly certain the way I would do it isn't "the best" way for most other people.  I'd use fsarchiver to make cloned partitions.  Every few years, I buy a new HDD for my only Windows booting machine and make a clone from the old disk into the new disk. The old disk is retained, untouched, for about 6 months before being converted into an external USB3 portable storage device.  The laptop came with a 320G HDD. I swapped in a 500G HDD about 3 yrs later, then a 750G HDD about 2 yrs ago. It works for me.

The easiest, 100% certain, answer is to swap out the old HDD for a new one and install Linux onto the new HDD. The 5 min swap is much more efficient than anything else I know. Nothing is lost from the prior install.

---

### Post by random turnip on 2017-04-05
Yeah you're probably right. Seems like it was a bit if an issue in Vista anyway, but there was a service pack with a program included apparently so I'll give that a bash later. 

A new hdd does sound a good idea actually, I was given the laptop for free so spending a little on a ssd seems reasonable. 

Alternatively i might just forget about backing up, there's little to no data on there and I don't intend on using Vista anyway unless Ubuntu doesn't work properly for some reason.

Thanks for the replies.

---

### Post by random turnip on 2017-04-05
Actually you've just reminded me I have an old 500gb laptop hdd lying around so going to try and recycle that first because why not.

That had ubuntu 10.04 on it, if I put it into the newerish laptop should i be able to boot into the existing ubuntu on there?

---

