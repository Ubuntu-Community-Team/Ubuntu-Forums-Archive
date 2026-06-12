---
title: "Ok, im gonna do it! Sometime, hopefully today."
date: 2005-08-13
forum: The Cafe
---

### Post by xequence on 2005-08-13
Im about to burn the ISO of the installer, and I am gonna ask some final questions. You might know the specs of my computer from all my questions, but here they are:

Windows ME (I think its fat32 as someone said)
18.9 GB HDD, about 3 GB free. (I can delete 1 GB of TV and a 700 mb movie, and the 600 MB INSTALLER ISO after I burn it, also 500 MB of software archived in .rar or .zip)
191 mb ram
700 mhz celeron

It is completly nessecary to keep my 3.5 GB of music.

I want to dual boot, but all the guides ive seen are for NFTS and I dont know if they still work with FAT32.

I would like someone to give me the steps I would do to partition the disk, install ubuntu, put my music onto ubuntu from windows, reformat the windows part so it only has 3 GB of space and a new installation of windows.

(Again) Thanks in advance, I just dont want to loose my music :)

EDIT: Ok, ill be back in ten minutes to view this again. I have to burn the installer and it blue screens me then I have to restart if I do anything else.

---

### Post by wmcbrine on 2005-08-13
If anything, FAT should be easier to work with from Linux than NTFS. Steps should be the same.

---

### Post by aysiu on 2005-08-13
[QUOTE=xequence]Im about to burn the ISO of the installer, and I am gonna ask some final questions. [/quote] Make sure you burn it at a slow speed (4x, for example).

> 
I want to dual boot, but all the guides ive seen are for NFTS and I dont know if they still work with FAT32. Same process for FAT32.

> 
put my music onto ubuntu from window I'm confused by this. Presumably, if you wanted to dual boot, you'd share music between Windows and Ubuntu, right? If you put your music on Ubuntu, Windows will not be able to access it. Or maybe you just want to boot into Windows occasionally for other reasons?

> reformat the windows part so it only has 3 GB of space and a new installation of windows. Still using ME, right? Or is this a new, new installation of Windows?

It is possible to shrink your Windows partition. You don't have to reinstall Windows. This is what I would do:

1. Back up your data. This is absolutely essential. Find any way to do it that you can--burn CDs, load them onto an MP3 player, borrow a friend's MP3 player. Back it all up, including your internet settings and email.

2. Then, delete everything except your base Windows installation.

3. Boot up Ubuntu. Manually edit the partition tables. Shrink your Windows partition. Then, create 380 MB swap partition, and whatever size /home and /root partitions you want.

4. When asked where you want to install Grub, install it the MBR.

5. After Ubuntu has finished installing, boot back into Windows to double-check that your Windows installation is still intact.

6. Copy back the files you backed up earlier.

---

### Post by xequence on 2005-08-13
I had burnt both the live cd and installer at 8x and they worked. Would that be more prone to errors at 8x?

>  I'm confused by this. 

I want my music to be on linux, though first I have to test a program that might work with linux to put it to my mp3 player.

>  Still using ME, right? 

Yep

> 3. Boot up Ubuntu. Manually edit the partition tables. Shrink your Windows partition. Then, create 380 MB swap partition, and whatever size /home and /root partitions you want.
 

What size /home and /root partitions would I want? What do they do?

> 4. When asked where you want to install Grub, install it the MBR. 

What is the MBR? Or will it tell me when I install it?

> You don't have to reinstall Windows 

I thought it would be the best way to get rid of all the stuff I dont use. I have a whole bunch of stuff I dont use on it. I just want a clean installation with a couple games on it. (Age of empires, Age of mythology, and maybe a game boy advance emulator)

Edit: Ok, I have 4 CD-Rs to burn. 650 + 650 + 650 + 700 = 2.6 GB. I can probly just burn my favorite out my collection... (Having an 800 song music collection doesent much help when switching operating systems...)

---

### Post by aysiu on 2005-08-13
[QUOTE=xequence]I had burnt both the live cd and installer at 8x and they worked. Would that be more prone to errors at 8x?[/quote] No. 8x is probably fine, and if the live CD worked for that, it'll probably be fine for the installer as well.

> 
What size /home and /root partitions would I want? What do they do? Well, /root is basically everything--it has /home, /etc, /var, /usr, /bin, and a whole bunch of other folders. If you create a separate /home partition, Ubuntu will trick itself into thinking it's a folder in /root. Why would you want to do that? Well, /home has all your files and user preferences. So, if you ever reinstall Ubuntu (or install over Ubuntu with another Linux distribution), you can do so without disturbing your settings and files. If you don't care about preserving that stuff, you can set up just a / and swap.

> 
What is the MBR? Or will it tell me when I install it? The MBR is the master boot record. It's best to install the Grub boot loader to the MBR because Ubuntu will recognize Windows as a choice to boot from, but Windows will not recognize Ubuntu as a choice. Right now, Windows' boot loader is on the MBR.

> 
I thought it would be the best way to get rid of all the stuff I dont use. I have a whole bunch of stuff I dont use on it. I just want a clean installation with a couple games on it. (Age of empires, Age of mythology, and maybe a game boy advance emulator) If that's the case, I'd do a clean install of ME *first*. Then, install Ubuntu.

---

### Post by m0biu5 on 2005-08-13
When I dual-booted, I rarely used the linux install, just out of comfort. Just a thought (maybe give Ubuntu a shot by itself for a week or so)

---

### Post by varunus on 2005-08-13
You can leave your music on the windows partition; Ubuntu can access it just like it was on the linux partition.  So you don't need to burn it to CD.  There won't be any hassle transferring your music collection since you can just access the windows drive from Ubuntu!  Just use this guide, with pictures, to repartition; they talk about NTFS but its the exact same process for FAT32:
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

Then go here to find how to mount your windows drive in linux:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

And here to get all the codecs you'll need to play all your stuff:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Good luck with the MP3 loader, you can also try running the windows software under wine, but make sure to follow the WINE guide in the "Hoary Tips and Tricks" section of the forum, they document how to get it set up properly.

---

### Post by az on 2005-08-13
[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by aysiu on 2005-08-13
[QUOTE=varunus]You can leave your music on the windows partition; Ubuntu can access it just like it was on the linux partition.  So you don't need to burn it to CD.  There won't be any hassle transferring your music collection since you can just access the windows drive from Ubuntu![/quote] This is true, theoretically, but any time you're installing an OS or shifting around partitions, it's always a good idea to back up important data.

---

### Post by xequence on 2005-08-13
Thanks everyone :)

I am backing up my data now and hopefully I can have all this stuff done by tommorow and working great :)

---

### Post by Brunellus on 2005-08-13
[QUOTE=m0biu5]When I dual-booted, I rarely used the linux install, just out of comfort. Just a thought (maybe give Ubuntu a shot by itself for a week or so)[/QUOTE]

I'm dual-booting, and I only boot XP up to play games.  three-quarters of my computer time is Ubuntu...over that proportion, I guess.

If you don't use the new OS, how do you expect to learn it?

---

### Post by xequence on 2005-08-13
> If you don't use the new OS, how do you expect to learn it? 

Yea :P

I am gonna get alot of use out of ubuntu, after all I am sacrificing alot of multimedia to do so :P Like over two thirds of my music collection, the family guy movie, and other stuff.

---

### Post by Brunellus on 2005-08-13
[QUOTE=xequence]Yea :P

I am gonna get alot of use out of ubuntu, after all I am sacrificing alot of multimedia to do so :P Like over two thirds of my music collection, the family guy movie, and other stuff.[/QUOTE]
 ubuntuguide is your friend for multimedia codecs.

Unless you've got your music in wmv or aac.

---

### Post by xequence on 2005-08-13
Wmv is video :P

Wma is audio, and I woouldent ever use them. MP3 works with just about everything.

---

### Post by Brunellus on 2005-08-13
[QUOTE=xequence]Wmv is video :P

Wma is audio, and I woouldent ever use them. MP3 works with just about everything.[/QUOTE]

...including ubuntu, if you install the appropriate codecs.  What I'm trying to say here is that you dont' need to 'give up' much, if anything at all, by migrating to ubuntu or gnu/linux in general.

---

### Post by poofyhairguy on 2005-08-14
[QUOTE=xequence]Yea :P

I am gonna get alot of use out of ubuntu, after all I am sacrificing alot of multimedia to do so :P Like over two thirds of my music collection, the family guy movie, and other stuff.[/QUOTE]

Why? None of us give that up. Heck....Fat32 is a great thing to have!

---

### Post by benplaut on 2005-08-14
i tried to dual boot (w/ SuSE), it messed up the windows partition, SuSE had a bunch of problems, so i commanded Ubuntu to install over the whole HDD

using it ever since  :)

---

