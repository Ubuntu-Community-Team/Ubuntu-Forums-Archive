---
title: "vbox- vista guest, and lightroom"
date: 2009-08-03
forum: Virtualisation
---

### Post by blur xc on 2009-08-03
Ok- I've got my pc all set up, ubuntu and vista in a dual boot- and inside of ubuntu I also have vbox running vista.  

My purpose is this- to use lightroom.  First off, Lightroom still doesn't work right in Wine.  2nd, lightroom is a memory intensive app- so I feel like I would be crippling myself if I left myself to run lightroom in vbox only.  Heck, the whole reason I built this computer was to improve my lightroom performance (which is awesome, btw).  So- to limit the amount of rebooting back and forth between vista to use lightroom and ubuntu for everything else (mostly just email, shopping, etc..), I thought I could get lightroom running in vbox for quick- jump in, do some simple editing, etc., and be done.  For heavy workloads (processing lots of raw files, etc., I'd reboot into vista.  

In order to access the same catalog file in both installs of lightroom, I have the catalog file on my external drive with all my photos.  Which, btw, is a recommended method of storing your catalog anyway.  It also stands to reason there's a performance benefit of having your paging file and lightroom catalog (it's a few gigs in size by itself) on separate drives.  The lightroom in native vista works flawlessly, awesome compared to my old pc, which was way under-awesome.  It'd take minutes sometimes just to load one picture.  The processor would hit wicked temps, 70C+ exporting a batch of photos at times.

So- here's my problem.  In vbox I set up my external drive as a shared folder with full access.  When I try to open the catalog file, it tells me that lightroom cannot use the file in that location because it can't write there.  This was the regular problem with lightroom in wine as well.  I navigated to that folder from inside vista in vbox, and I could create files and folders w/o any trouble, so then why does lightroom think it can't write there?  Is there some permission setting I can change to fix this?  I read that there's some experimental support for directly accessing drives, but I'm not willing to risk wiping my hdd to test it.

Sorry for the lengthy post-

thanks in advance,
BM

---

### Post by blur xc on 2009-08-05
Ok- I don't yet know how to fix this, but I found out the why-

Apparently, Lightroom doesn't support catalogs stored on network drives.  This seems to be a problem w/ companies that want to work off of one master catalog...

So, as I understand it, a shared folder appears to the guest os as a network folder, correct?  So, there's the problem.  Is there a reasonable work-a-round to get past this?

thanks,
BM

---

