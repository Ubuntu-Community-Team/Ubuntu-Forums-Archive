---
title: "Xubuntu 12.04 installer partitioning problem"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Penguinnerd on 2012-03-17
I was hoping to test Xubuntu 12.04 on an Acer Aspire One D250 netbook.

I've got the Beta-1 image on a USB flash drive. When I start the installer (from either the live mode or straight into the installer) it appears to hang at the same step

All goes well until I get to the partitioning step. I want to install it alongside Ubuntu 10.04. When the partitioning slider thing is supposed to appear, I just get a movable slider on a gray background in the window, with no text or colors where the partitions should be. The "Continue" button is non-clickable, and the "quit" button causes it to hang until I press the power button, at which point it gives me a shutdown prompt.

side note: I am unable to locate the daily images for x86. I can find a page to download the AMD64 ones [here]("http://cdimage.ubuntu.com/xubuntu/daily/current/"), but no x86. Do these images exist?

Any suggestions are welcome.

---

### Post by Peripheral Visionary on 2012-03-17
They were probably just making the new ones when you visited the site. The same site will have the next daily image for download in a couple of hours, I bet. Revisit the site (and reload the page just in case it's loaded from your browser's cache) in a few hours, or first thing tomorrow morning.

Or it could definitely have something to do with **THIS**:

[http://ubuntuforums.org/showthread.php?t=1942306](http://ubuntuforums.org/showthread.php?t=1942306)

If so, it sounds like the next daily build of Xubu 12.04 will be even more awesome than ever!

---

### Post by Penguinnerd on 2012-03-17
Interesting stuff. I plan to try the latest daily image when it becomes available.

In the meantime, any guesses/theories would be great.

---

### Post by Penguinnerd on 2012-03-18
I still can't find the daily x86 images for Xubuntu 12.04. If I could find them, I'd give them a try, and see if it fixes my problem.

I looked at the daily images from the last few days, and there's no x86 images in there either. Just "alternate install AMD64". Nothing else.

---

### Post by philinux on 2012-03-18
> **Penguinnerd said:**
> I still can't find the daily x86 images for Xubuntu 12.04. If I could find them, I'd give them a try, and see if it fixes my problem.

I looked at the daily images from the last few days, and there's no x86 images in there either. Just "alternate install AMD64". Nothing else.

Scroll down the list [http://cdimage.ubuntu.com/xubuntu/releases/12.04/beta-1/](http://cdimage.ubuntu.com/xubuntu/releases/12.04/beta-1/)

---

### Post by Penguinnerd on 2012-03-18
> **philinux said:**
> Scroll down the list [http://cdimage.ubuntu.com/xubuntu/releases/12.04/beta-1/](http://cdimage.ubuntu.com/xubuntu/releases/12.04/beta-1/)

But I already have the Beta image. It doesn't work for me. That's why I want the Daily image. Click the link in my original post. The daily images are supposed to be there, but the x86 one is missing.

---

### Post by Gregory Lee on 2012-03-18
When I installed Alpha2-amd64, I was also unable to get the installer's partitioner to work.  Since I did not need to save anything on the disk, I had the installer use the entire disk and accepted it's default partitioning.  Then after installation, I changed the partitions to what I wanted.

If you want to save a system that's already on the disk, I don't understand why you want to use the installer's partitioner.  If you need to shrink a partition and make a new one, can't you do that using a partitioning program from your 10.04 system?

---

### Post by Penguinnerd on 2012-03-18
> **Gregory Lee said:**
> If you want to save a system that's already on the disk, I don't understand why you want to use the installer's partitioner.  If you need to shrink a partition and make a new one, can't you do that using a partitioning program from your 10.04 system?

Very true. I'm using gparted on 12.04 live usb mode to shrink the original partition, and I'll tell the installer to use the free space. Assuming nothing else goes wrong, it should get me up and running.

But I'm still curious about what's up with the x86 daily images, if anyone knows about that.

---

