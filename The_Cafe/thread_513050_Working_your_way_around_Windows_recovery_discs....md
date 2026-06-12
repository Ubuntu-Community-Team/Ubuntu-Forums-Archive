---
title: "Working your way around Windows recovery discs..."
date: 2007-07-30
forum: The Cafe
---

### Post by user1397 on 2007-07-30
I am just wondering how it is possible to bypass the recovery cd-making application that comes bundled with my computer.  It apparently only lets you make one copy of the recovery discs.

I made the recovery discs with this app a couple of years ago, but I chose to burn to CDs  instead of DVDs, so I ended up having to burn 6 recovery discs in total.

So basically, I now wish to have one recovery DVD that has the data on all 6 CDs, because I've had to reinstall windows too many times, and it is getting pretty annoying to install from 6 CDs each time.

So is there any way I can somehow copy all the files and folders from all 6 CDs, put them in some folder on my desktop (in windows xp), make an ISO image, and then burn it to a DVD?

---

### Post by smoker on 2007-07-30
would it not be easier to make an image backup of a fresh install with all the updates. it would be a lot quicker to restore an image than do a re-install whenever windows goes fubar.

---

### Post by user1397 on 2007-07-30
> **smoker said:**
> would it not be easier to make an image backup of a fresh install with all the updates. it would be a lot quicker to restore an image than do a re-install whenever windows goes fubar.how could I do that?  are there any free programs that do this? As far as I know, there is acronis true image, and norton ghost, and both cost something.

---

### Post by srt4play on 2007-07-30
I would boot from a livecd and use partimage.

---

### Post by CSMatt on 2007-07-30
Download [MagicISO](http://www.magiciso.com/).  It's proprietary and works with Windows only, but it will combine the ISO files from your 6 CDs into one or two DVDs.  I recommend using a duel-layer DVD if your burner supports them.  If "DVD+R DL," "DVD-R DL," "DVD+RW DL," or "DVD-RW DL" appears anywhere on the face of the drive, you have duel-layer support for that respective disc.  As with their CD  and single-layer DVD burning cousins, duel-layer burners that can burn RW discs will also burn their R counterparts, but remember to use the correct format.

Despite this remedy, I'd still complain to your OEM about their clear lack of caring for their customers.  My SONY VAIO had the same warped idea of including a recovery partition and no recovery discs, preferring instead to place that burden on the user.  How could I possibly have known that I was supposed to burn the discs myself if I hadn't RTFM?  What if my hard drive had failed and I couldn't restore the factory settings because I hadn't known to make recovery discs?  In your case, what if I had made a bad burn of the discs during the one time I was allowed to make them (SONY didn't have that awful restriction for me)?  Thankfully my ASUS laptop included both driver and recovery discs, and also gave me an option to order another recovery disc if I ever needed to.  Remember not to mention that you were running Ubuntu though, or the customer service representative might just involuntary spit out the "We do not recommend running alternative operating systems on our machines" excuse.

As for partimage, I would recommend that only if your partition isn't NTFS.  The partimage page states that NTFS support is still experimental.  Also remember that the partition you are restoring to has to be precisely equal to or greater in size than the partition you imaged.

---

### Post by user1397 on 2007-07-30
> **CSMatt said:**
> Download [MagicISO]("http://www.magiciso.com/").  It's proprietary and works with Windows only, but it will combine the ISO files from your 6 CDs into one or two DVDs.  I recommend using a duel-layer DVD if your burner supports them.  If "DVD+R DL," "DVD-R DL," "DVD+RW DL," or "DVD-RW DL" appears anywhere on the face of the drive, you have duel-layer support for that respective disc.  As with their CD  and single-layer DVD burning cousins, duel-layer burners that can burn RW discs will also burn their R counterparts, but remember to use the correct format.

In all seriousness though, I'd still complain to your OEM about this clear lack of caring for their customers.  My SONY VAIO had the same warped idea of including a recovery partition and no recovery discs, preferring instead to place that burden on the user.  How would I possibly know that I was supposed to burn the discs myself if I hadn't RTFM?  What if my hard drive had failed and I couldn't restore the factory settings because I hadn't known to make recovery discs?  In your case, what if I had made a bad burn of the discs during the one time I was allowed to make them (SONY didn't have that awful restriction for me)?  Thankfully my ASUS laptop included both driver and recovery discs, and also gave me an option to order another recovery disc if I ever needed to.  Remember not to mention that you were running Ubuntu though, or the customer service representative might just involuntary spit out the "We do not recommend running alternative operating systems on our machines" excuse.thanks for your help, though I still don't quite understand howto actually get all 6 CDs onto one DVD (but I guess I'll figure it out :)

Yea my OEM is HP...and yea it's true what you say...what if the first set you made was bad?  what then?

I think HP does have an option available for ordering recovery discs online, but I only found out about it after I was cruising their site for a while.  I wouldn't have found it otherwise.

---

### Post by popch on 2007-07-30
> **ubuntuman001 said:**
> how could I do that?  are there any free programs that do this? .

Yes, there are. One of them is called Linux. AFAIK, Linux has all required functions out of the box: Reading all blocks of a partition, compressing the data, compiling an ISO image, burning.

Perhaps one of the better informed people in this forum can supply the necessary details.

---

### Post by smoker on 2007-07-30
> **ubuntuman001 said:**
> how could I do that?  are there any free programs that do this? As far as I know, there is acronis true image, and norton ghost, and both cost something.

this is free and works great:
[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)

you can make an image while windows is running, but you need a copy on a boot cd to restore an image. the faq should explain.

best of luck

---

### Post by CSMatt on 2007-07-30
> **ubuntuman001 said:**
> thanks for your help, though I still don't quite understand howto actually get all 6 CDs onto one DVD (but I guess I'll figure it out :)

Yea my OEM is HP...and yea it's true what you say...what if the first set you made was bad?  what then?

I think HP does have an option available for ordering recovery discs online, but I only found out about it after I was cruising their site for a while.  I wouldn't have found it otherwise.

[This will tell you how to combine the ISOs](http://www.magiciso.com/FAQ/FAQ0001.htm).  I forgot to mention that you need to install Daemon Tools also.

HP?  Oh man.  You sure got screwed with that deal.  HP's printers are top notch, but their PCs are terrible and always have been.  It's probably even worse now that they are essentially the new Dell.  You're probably better off formatting the drive and buying and installing a separate copy of Windows than going with the factory install.

---

### Post by user1397 on 2007-07-31
> **CSMatt said:**
> [This will tell you how to combine the ISOs]("http://www.magiciso.com/FAQ/FAQ0001.htm").  I forgot to mention that you need to install Daemon Tools also.

HP?  Oh man.  You sure got screwed with that deal.  HP's printers are top notch, but their PCs are terrible and always have been.  It's probably even worse now that they are essentially the new Dell.  You're probably better off formatting the drive and buying and installing a separate copy of Windows than going with the factory install.well I tried MagicISO, but it's just a trial, so it only lets you make an image up to 300MB in size...I guess I'll try the other one mentioned (DriveImage)

---

### Post by CSMatt on 2007-08-01
Sorry about that.  I never got that far considering I was trying to combine by iBook's 3 Mac OS X CDs into one DVD but it apparently can't make HFS+ formatted disk images.  I figured that since your CDs would most likely use the ISO9660 file system with Joliet extensions that it would work for you.

---

