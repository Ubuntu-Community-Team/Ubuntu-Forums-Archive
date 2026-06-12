---
title: "I multiboot Win XP, Linuxes. I want to have a common data storage partition. How to ?"
date: 2007-02-21
forum: Windows
---

### Post by brjoon1021 on 2007-02-21
My end goal is simply to have a common "My Computer" disk or partition that can be read and written to by My many Linuxes and by Win XP. Should I make it FAT32 ? Both can access this filesystem but I have read that it fragments badly (mostly Linux people shooting it down). It will be a 38GB partition if I only make one.

Should I make it ext2 and use one of those windows drivers? I will not be able to take a read and write performance hit though because I will be editing videos with both Adobe software on the windows side and (I don't know what the good video editing software in Linux is yet).

Should I make it NTFS and install that Linux software NTFS-3G ([http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)) that allows Linux to read and write to NTFS partitions? Again, I am wondering if there will be a read and write performance hit that will make for stuttering audio/video playback and bad video editing.

On this common partition I will have MP3 and Oggs for listening, Office and OpenOffice documents, Jpegs and I will be editing videos from my mini DV camcorder.

I suppose that I could make two or even three partitions but I hate to have duplicate files.

I am pretty confused on how to go about this...

Thanks,

B

---

### Post by rsambuca on 2007-02-21
I have used both FAT32, as well as the [[COLOR="Red"]fs-driver for Windows[/COLOR]]("http://www.fs-driver.org/") which worked really well for me.  I have not used the ntfs-3g driver yet as it is still an RC version, although it sounds pretty bug free now.  My wife uses stuff on Windows so I didn't want to risk using the ntfs-3g driver and screwing with her work stuff.  I have never had a problem using the fs-driver for Windows, as well as the FAT32 partition.

---

### Post by erlyrisa on 2007-02-21
Fat32 is the way to go - it's good'ol technology that you can trust between oses including Mac.

Fragmentation ain't that much of a problem - my shared fat32 partition has never been 'defraged' - though I don't delete much. If your the type that is deleting and creating new files all the time (especially big ones like DVD images) then maybe looking into NTFS or EXT2 should help in not having to deal with defraging.

-Note I wreckon defrag has to be one of the biggest cons in computing history. The average person will never have to defrag thier fat32 drive. The slighly added speed advantage that you get once defraged is soon nullified once you starting moving data around again on your drive. The slight amount of extra work a hard drive has todo for tha average fragmented drive vs. the amount of work the drive does to actually defrag the drive, just needlessly works your drive and wears it out prematurely. Defrag maybe great for a Law firm with multiple strewn files on thier PC's - but really they should be keeping thier files on a Unix server anyway - so as for normal PC usuers it's piontless - and for offices it's piontless because they shouldn't be keeping thier files locally.
The only usefull application I have seen for defrag is in Schoraly institions. Where your users account can be accessed from any Windows PC by accessing the server and downloading the user profile to the client. In this cas 1 PC will become 'cluttered' with mutiple user acounts residing on the drive (and sometimes studuents install their own little programs locally) in this case rudimenterary account deletion and defraging probably helps. (but then again I don't ever remmember seing a fat32 windows version running in an institution - so again defrag is piontless)

---

### Post by erlyrisa on 2007-02-21
Something to add...

Windows actually splits it's swap file over your hardrive's contents. Even when you first install.
I presume Msoft's swap file creation algorithm has access to your drives physical layout. I would presum to make a good swap file scenario is to scatter the swap file between areas of the drive where your programs are stored. Msoft may have even put in a 'momentum' algorithm: which decides where sections of the swap file should reside based on the fastest diskreads between strewn sections . ie if dirve is spinning at 32k and needle takes 7Ns to jump from track 1 - 15 then end of the swap file residing in 1 should draw a straight line to the start of swap in track 15.

-This I wreckon is where Linux is behind for the desktop computer (though it won't be problem on solid state drives anyway)

-Oh in the old days when defraging in dos with symantecs ne defrag utility - I found that it only took a week for my computer to 'become slower' than it was before I defraged it. I wreckon it's because my files were strewn according to the way I use them, but once defraged ,everytime I would for example 'add content' to like a spreadsheet - the file would get split over the drive - therfore, once you defrag - you get addicted to defrag.

---

### Post by jdhore on 2007-02-21
i'd use either FAT32 or EXT2 or EXT3

---

### Post by EngDrewman on 2007-02-22
does linux have the _native_ (meaning no additional drivers necessary) ability to read and write to fat32? Because I know it can with fat16 but I'm not sure about 32.

---

### Post by rsambuca on 2007-02-22
Yes.  Fat32 can be natively written to by both Windows and linux (and Mac, I think).

---

### Post by erlyrisa on 2007-02-22
Why fat32 and the older fat's can be read and written to by practically every OS....

It's the floppy disk! - back in the old days everything was shared via the the floppy. So if a mac user or any other OS user wanted to read the most common OSes (DOS) native filesystem they had to get with the game. At first - and for quit a while mac couldn't read 'DOS DISKS' but it didn't take long for them to finally give in and provide the compatibility to be able to read the majority of the floppies around the world. FAT was actually an advanced disk format, where the File Allocation Table, once read provided faster access to files than other systems around. This could be evidenced by how long you had to wait for a macs smiling clock cursor to read a floppies contents, vs. typing 'dir a:'.

---

