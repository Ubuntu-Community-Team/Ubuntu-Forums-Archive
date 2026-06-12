---
title: "image backup / restore options?"
date: 2006-12-01
forum: Server Platforms
---

### Post by at0mic on 2006-12-01
hi,

whats the best image backup / restore software solution for linux currently? 

I see Norton Ghost 2003 supports linux but is there a free solution?

---

### Post by technodigifreak on 2006-12-01
[http://www.systemimager.org/](http://www.systemimager.org/) Rocks! 

I've also heard really good things about MondoRescue, but have not yet tried it (I will on my next project though).

---

### Post by meyrd on 2006-12-01
I use G4L.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

It works good and it's opensource.

Read up on it to be familiar with how it works before you use it in an environment that is critical though.

I use it with an ftp intranet box that serves up images for a mobile lab.

I boot the laptops to cd using G4L then bring the image down to the drive from the server. Make sure you partition the drive you want to restore with the same number of sectors you backed up or you will have issues.

---

### Post by tturrisi on 2006-12-01
also...partimage:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
and should be in Ubuntu repositories.

---

### Post by breezyfox on 2006-12-02
> **at0mic said:**
> hi,

whats the best image backup / restore software solution for linux currently? 

I see Norton Ghost 2003 supports linux but is there a free solution?

HI

Thers is IFL (image for linux) which works like ghost and is great. The cost is not much as compared to other similar products for windows and there is trial version which is fully functional.
[http://www.terabyteunlimited.com/imagel.html](http://www.terabyteunlimited.com/imagel.html)

bz

---

### Post by chrisfay on 2006-12-02
I use partimage as well. What's the deal with the 2gig limit on image sizes? Has anyone had experience restoring from a partimage backup that was stored as seperate images due to this limitation?

I remember the error message saying something about it being a filesystem cap but is there a way around this?

---

### Post by breezyfox on 2006-12-03
> **chrisfay said:**
> I use partimage as well. What's the deal with the 2gig limit on image sizes? Has anyone had experience restoring from a partimage backup that was stored as seperate images due to this limitation?

I remember the error message saying something about it being a filesystem cap but is there a way around this?

hi
i just use ghost 2003 DOS version for windows and LFI for ubuntu i never faced this limitation. can you explain in bit detail.

thanks
BZ

---

### Post by hernan43 on 2006-12-03
I have good luck in the past with MondoRescue([http://www.mondorescue.org/)](http://www.mondorescue.org/)). It does bootable install images and can accomodate multiple types of media.

---

### Post by technodigifreak on 2006-12-04
> **chrisfay said:**
> I use partimage as well. What's the deal with the 2gig limit on image sizes? Has anyone had experience restoring from a partimage backup that was stored as seperate images due to this limitation?

I remember the error message saying something about it being a filesystem cap but is there a way around this?

The size cap is for saving images to a FAT filesystem which has a file size limit of 2GB per file.  However, an EXT2 file system has a limitation of 2TB per file.  So if you are saving it to a modern linux partition, then you need not worry.  If you are saving it to a FAT formated external drive, then you should stick with the default. - I usually stick with the default just so that I have data portability.

---

### Post by chrisfay on 2006-12-14
> The size cap is for saving images to a FAT filesystem which has a file size limit of 2GB per file.

Does this also apply to NTFS? I am saving the images to a networked NTFS Samba share and am getting the 2gig size limit.

---

### Post by MJN on 2006-12-15
Even hitting this limit shouldn't be causing any problems - Partimage will happilly split the image as requiredl, and safely restore it back again.
 
I split my images into 2GB files as a matter of course, even though they reside on an ext3 filesystem. This then makes it trivially easy to move them around - e.g. I might want to shift the lot onto a FAT32 partition, or perhaps onto DVDs (two files per disc) without having to make any modification to the original files.
 
EDIT: Having just re-read your post, it sounds like you think there is a 2GB size limit on **images** - no, the limit is only on the individual files that make up that image. For example, your might have a 20GB partition which compresses down into a 10GB image. This image then consists of five 2GB files.
 
Mathew

---

### Post by chrisfay on 2006-12-15
> Even hitting this limit shouldn't be causing any problems - Partimage will happilly split the image as requiredl, and safely restore it back again.

True, but only if you specify it prior to starting the imaging. I went three failed rounds before it was even made apparent that the cause was the 2gb file limit. Drove me nuts until I saw a tiny little error within a bunch of text that highlighted it.

Whats the process for restoring from these chopped up 'mini-images'? I looked on partimages website but found nothing regarding restoring from them....could have overlooked it but pretty sure it wasn't there...

Have you had good success with it?

---

### Post by chrisfay on 2006-12-15
> EDIT: Having just re-read your post, it sounds like you think there is a 2GB size limit on images - no, the limit is only on the individual files that make up that image. For example, your might have a 20GB partition which compresses down into a 10GB image. This image then consists of five 2GB files.

That was the problem, my entire image would compress to about 10GB but, with the limit, had to be broken down into 2GB individual images. This is fine, my mane concern is how to restore from multiple images...

---

### Post by MJN on 2006-12-15
Oh, okay - I see where you're coming from. I must've just started using 2GB files in the first place and hence never suffered having not done so.
 
Restoring the chopped-up images is simply a case of specifying the first file in the series when restoring - this file must (i.e. I'm guessing it does as opposed to saying you have to ensure it does) contain pointers to all the others (which will be labelled as a consecutive numered extension .001, .002 etc). Hence, you don't need to do anything yourself in particular - just pick the right (first) file! In fact, it possibly just looks for any other files with the same name, yet numbered extensions, and collates them all together.
 
I've used it without any problems, although I only use it for rebuilding a standard test machine quickly hence I'm probably not pushing it to its limits. I don't actually use it for backups as I need the ability to retrieve individual files from my backups which you can't do with Partimage (unlike, say, Ghost Explorer with Ghost).
 
Furthermore, I sleep better in the knowledge that my backups differ in only the slightest way from my originals - collating them all together in a compressed format is the old 'eggs in one basket' problem - potentially asking for trouble should part of it become corrupt as it will likely render the whole image worthless.
 
Mathew

---

### Post by chrisfay on 2006-12-15
> Restoring the chopped-up images is simply a case of specifying the first file in the series when restoring 

Sounds good. I haven't had to test this yet so hopefully it will be semi-self explanitory.

> I don't actually use it for backups as I need the ability to retrieve individual files from my backups which you can't do with Partimage (unlike, say, Ghost Explorer with Ghost).

I may be paranoid but, on top of running partimage for my images I tar the entire filesystem nightly, saving a weeks worth of these backups as well; excluding certain obvious folders.  This works well for grabbing specific files but has obvious limitations for doing full system restores. Hopefully Partimage will preform well if needed. We'll see...

If not, down goes my hosting service!:p

---

### Post by MJN on 2006-12-15
Full system restores should be fine from tar backups - I've done the same (twice now!) with my rsync backups... however I must admit that the first time it worked I was amazed, and the second time simply relieved... perhaps next time I'll have more confidence!
 
Of course, with a high-level full system restore like this you must have the partition layout and file system laid out before hand e.g. boot with LiveCD, create partitions as they were before (or remember to edit /etc/fstab afterwards if not), 'format' partitions, rsync everything from the backup to the new disk, (re)install Grub to the MBR for good measure, reboot and pray! :)
 
My 'hosting service' is for myself, friends and family (yours too?) but for some reason in times of crisis this feels worse than if it were for paying customers!
 
Mathew

---

### Post by chrisfay on 2006-12-15
> My 'hosting service' is for myself, friends and family (yours too?) but for some reason in times of crisis this feels worse than if it were for paying customers!


I know the feeling, a good portion of my services are definately friends and family, though my freelance web design, consulting and email services have brought in a decent ammount of professional income/use.  I'd say its a 20/80 ratio. Either way, its worth protecting!

---

### Post by MJN on 2006-12-15
You've got the worst of both worlds then! ;)
 
Having had two server restorations in the past few years (first was a machine upgrade, second was a hard disk failure) I've certainly learnt that having the experience of performing a successfull restore is a real help... particularly when the sh1t has hit the fan and the pressure is on.
 
Now that I've done a couple I'm quite comfortable with it. I recently performed a full system upgrade from Breezy to Dapper and, for various reasons, chose a fresh install. This adds another layer of complexity as you tend to have various bits and pieces lying around (e.g. server certificates, custom config scripts for obscure services) that can easily get missed out so the value of practicing a restore process (and documenting it, even if it's just scribbling what you did down) cannot be overstated.
 
Anyway, I digress, I was going to suggest you gave partimage a whirl on another PC (I have an identical machine to my server with which I do my experimentation on) then you can see for yourself how it does/doesn't work so you're not learning this for the first time when it's all crashed down around your ears!
 
Mathew

---

### Post by chrisfay on 2006-12-15
I have really come to enjoy most aspects of the unix/linux world but, I can't deny the ease of Ghosting a win machine. I've yet to come across a universally capable, user friendly, feature rich and reliable backup solution similar to Ghost or Acronis that's free. I'd even consider paying/using the Linux Acronis package if it wasn't an ungodly $700.  

> Anyway, I digress, I was going to suggest you gave partimage a whirl on another PC (I have an identical machine to my server with which I do my experimentation on) then you can see for yourself how it does/doesn't work so you're not learning this for the first time when it's all crashed down around your ears!

That's probably the best advice...


I'll have to give it a try....

---

### Post by Thorun on 2007-06-16
Now i'm in the exactely the same problem... But I just can't seem to get partimage to work..

when it launches i cannot backup to another partition... witch is much needed. I can only backup to /mnt/backup/some-stuff.gz

Is it possibly to backup /mnt/sda3 to a file on the /mnt/sda6 partition?

---

### Post by at0mic on 2007-07-25
Has anyone tried the ghost 4 linux project? looks ideal.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by MJN on 2007-07-25
See post 3! ;)

---

### Post by at0mic on 2007-07-25
hehe. thanks i somehow skipped that one.

---

### Post by MJN on 2007-07-25
Perhaps I could've added something a little more useful than that...

I have actually used G4L sometime back and it did what it said on the tin. It's certainly no 'Ghost' but it seems to work. I'm pretty sure I stopped using because of some issue or other but I can't work out what it was (if anything - perhaps my strategy just changed as now I use rsync for my backups as I like the 'cleanliness' of such an approach, i.e. no reliance on a particular product to restore the backup - just a simple of case of moving files).

I do recall some 'history' between G4Linux and G4Unix but the details have also escaped.

Damn... Screw the server backups, I need to sort my own memory out first! ;)

Mathew

---

