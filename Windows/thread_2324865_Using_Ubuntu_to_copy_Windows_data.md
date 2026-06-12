---
title: "Using Ubuntu to copy Windows data"
date: 2016-05-17
forum: Windows
---

### Post by tech291083 on 2016-05-17
Hi Friends,

I have Windows 7 Home Basic 64 bit installed on a 500 GB HDD as the only OS, but a couple of days ago, I got this error called "unmountable boot volume", I tried everything I can, including System Repair with the original Windows 7 install Disc and what not, but nothing has worked so far. Windows doesn't boot at all.

Then I ran Ubuntu 16.04 LTS Desktop as a Live OS from CD ie I chose the Try Ubuntu option to see whats going on, as I ran Ubuntu off DVD, I came to know from the in-built program called "Disks" that my HDD had 11 bad sectors, as I know this HDD is 4+ yrs old. Are these 11 bad sectors to many? Is this is a signal to the fact that my HDD is on its way to the graveyard? Is my HDD totally gone? 

Here is my exact error,

[http://www.howtogeek.com/wp-content/uploads/2011/06/652x313x2011-06-20_151256.jpg.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.NBlPx2rO-l.jpg](http://www.howtogeek.com/wp-content/uploads/2011/06/652x313x2011-06-20_151256.jpg.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.NBlPx2rO-l.jpg)

I am not able to back up my data using the latest - Ubuntu 16.04 LTS Desktop DVD, something I used to do a lot when my Windows was not booting for any reason whatsoever. Now, I am not even seeing Windows partitions, data. What should I do? How can I save my Windows data? Should I buy a new HDD?  Please help me out, I am really stressed out. Thanks a lot.

I hope I can recover my Windows data by doing something like the below videos have shown.

[URL="https://www.youtube.com/watch?v=AvsJ6OtSgTY"]https://www.youtube.com/watch?v=tH_IByvAqIg


https://www.youtube.com/watch?v=AvsJ6OtSgTY[/URL]

---

### Post by mastablasta on 2016-05-17
the S.M.A.R.T. scan will usually have border values shown so you know when the disk will fail.

hard to say what wen't wrong here, but it might still be the hard disk. although 11 bad sectors is not muhc. but it could be they are at the boot part of the disk.

if this is a desktop you should easilly check the disk data cables. perhaps they are loose.

can you at least see the disk from ubuntu? if so, you could try and image it with clonezilla.
however if the disk failed, recovery would be difficult.

---

### Post by tech291083 on 2016-05-18
Hi,

Thanks for the reply. 

> **mastablasta said:**
> 
the S.M.A.R.T. scan will usually have border values shown so you know when the disk will fail.


Yes, I agree with you, despite the fact that I know nothing when it comes to interpreting SMART test results, which basically are numbers against a number of attributes. 

Since Windows was not booting at all and only showing the error "unmountable boot volume" and freezing, I used a number of Linux distributions as a live medium to conduct this SMART tests. I tried the below 3 Linux distributions as the hard drive failed Fedora SMART test, forcing me to try another distribution ie Ubuntu and then finally Knoppix, just to make sure that SMART test results were all the same no matter what the Linux distribution was.
====================================================================================
Fedora 23 workstation (32 bit)

Please have a look at the 4 screenshots below,

[http://postimg.org/gallery/21c7ngozm/a00453af/](http://postimg.org/gallery/21c7ngozm/a00453af/)

Image 1 doesn't show any Windows partitions at all.

Image 2 is a screen-shot of a common Linux program called Disks, which shows 11 bad sectors.

Image 3 shows SMART test (Extended) results.

Image 4 shows an error while I tried to create a disk image.
====================================================================================
Ubuntu 16.04 LTS desktop 
(32 bit)

Please have a look at the 4 screenshots below,

[http://postimg.org/gallery/1jh3v5bwi/22b2bf6a/](http://postimg.org/gallery/1jh3v5bwi/22b2bf6a/)

Image 1 doesn't show any Windows partitions at all.

Image 2 is a screen-shot of a common Linux program called Disks, which shows 11 bad sectors.

Image 3 shows SMART test (Extended) results.

Image 4 shows an error while I tried to create a disk image.
====================================================================================
Knoppix 7.6.1

Please have a look at the 4 screenshots below,

[http://postimg.org/gallery/fibyr1qa/b7c183e3/](http://postimg.org/gallery/fibyr1qa/b7c183e3/)

Image 1 doesn't show any Windows partitions at all.

Image 2 is a screen-shot of a common Linux program called Disks, which shows 11 bad sectors.

Image 3 shows SMART test (Extended) results.

Image 4 shows an error while I tried to create a disk image.
=====================================================================================
> 
hard to say what wen't wrong here, but it might still be the hard disk. although 11 bad sectors is not muhc. but it could be they are at the boot part of the disk.


I had the same feeling that MBR might have been a victim. How many bad sectors are really bad or what the exact number is for anyone to just discard the drive and buy a new one?

> 
if this is a desktop you should easilly check the disk data cables. perhaps they are loose.


Yes, I did check the cables, they seem to be OK, even I use 3/4 other drives with other Linux distributions on them regularly. I like trying different Linux distributions. All other drives connected to this pc are working fine.

> 
can you at least see the disk from ubuntu? if so, you could try and image it with clonezilla.


I can see the disk, but not Windows partitions from Ubuntu Live DVD, the same goes for Fedora and Knoppix Live DVDs.

I used CloneZilla many years ago, but I will try it again with the latest version of its iso, which I have already downloaded 2 months ago.

Thanks

---

### Post by tech291083 on 2016-05-18
I can't believe this. I just used one program called "netboot.me", which was on this CD called Ultimate Boot CD (UBCD).


[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

All I did was boot Windows with this CD and kept the pc connected to the internet via a router at home. Then i just ran this program "netboot.me". Although, this program is not for Windows 7 as far as I understand, its meant for Linux distributions. not sure really. As the program started running connecting itself to some remote server, but I thought this was too slow and disconnected it by Ctrl+C ,but when I restarted the pc without the Ultimate Boot CD (UBCD), Windows booted without any fuss.

Please have a look at screen shots taken with my mobile, I never really allow to run this program "netboot.me" its full course, and still Windows booted. I really do not know as to how this happened.

[http://postimg.org/gallery/u4hmntoi/c7764c93/](http://postimg.org/gallery/u4hmntoi/c7764c93/)

Thanks,

---

