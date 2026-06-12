---
title: "Horror story: (re)install XP :( Install Ubuntu :)"
date: 2006-11-01
forum: Testimonials &amp; Experiences
---

### Post by gosh on 2006-11-01
Just want to share a recent experience with you.
IMO one of the biggest differences between XP and Ubuntu is the installation proces. 
My recent project cost me about 40 hours to install XP and just 2 hours to install Ubuntu!

Since it was Halloween yesterday, here is my horror story. Read and shiver.....:twisted:

My son ran XP on an old Dell PC. The thing was performing with more errors, virusses and spyware every week. So he got an (less old) Compaq.
However, it only had a 10 Gb harddisk. So I decided to switch the hd from the Dell to the Compaq.
Simple, isn't it? No, it isn't!!

Problem 1: the thing didn't boot from the new HD!
I googled around and found at the Microsoft-site that I should run FIXMBR from the Recovery Console. Did that, but did not work.
The same site suggested then to do a Recovery Installation of XP. That means installing XP again without losing your data. For this I had to enter the product-code. This worked well, except that I could not activate XP.
So I called MS and they asked if I had changed any hardware. I told my story and they said I had to use a new key. They gave me an gigantic long string of digits to enter and voila, XP was up again.
But, I still didn't boot from HD.
So I created a bootdisk and that made that I could get XP up.
I logged in and downloaded AVG free virus and anti-spyware software. I found a lot, a whole lot of misery there. Some things even didn't want to be removed and had to be removed using various tips and tricks I found googling.

With PartionMagic I then made 5GB free to install Ubuntu. Just over 30 minutes work. But then it still didn't boot. GRUB wasn't even loaded.
So there had to be something wrong with the MBR (master boot record). I found a CD-image of a wonderfull set of utilities called Ultimate Boot CD. On it was TestDisk. This program found all partitions and nothing seemed wrong with them. I fixed the MBR with it. But still the same problem. 

After a lot of fiddling about with TestDisk and other MBR- and partitioning tools I found out that the number of heads of the XP NTFS partition was 240, where it should be 255. So I changed that, but again no solution.

Still TestDisk came up with this same thing about the heads on the disk. That brought me to the idea to delete the Ubuntu-partitions, run chkdsk and convert NTFS to FAT32. 
This was it!!!

Reinstalled XP again. Even that the installer came up with several errors of missing .dll files it completed and worked.
And then of course (?) I had to reinstall all updates like Service Pack 2 and over fifty Security Updates. One of the updates that gave errors was Microsoft Installer 3.1. Googled again and found out that a certain service was not started at boot.

Then I found out that Office didn't work so I had to remove it, install it and update it again.

I then ran disk-defragmenter just for good measure. It took 7 hours to clean a 30 Gb disk!!!

Pew, fortunately all data and other programs on the disk were still there.

I put the 10Gb disk in the old Dell and installed Ubuntu Dapper it as well as on the 5Gb free space, updated them to Edgy, installed my broadcom driver and all this in just a few hours.:D

So, this is what I have learned:

When using Windows Software Murphy's Law does not apply. He was far to optimistic!

---

### Post by jhenager on 2006-11-01
I'd probably have put the 10GB hard disk in the old XP system and backed up all the important data to it, and then move both disks to the Compaq and do a clean install to the bigger HD.
Glad you got it. You probably learned a lot, tho.

---

### Post by smoker on 2006-11-05
hi, gosh,

just think of all the extra computing time you will have with ubuntu, rather than spending hours every week scanning and keeping windows clean!

good luck:D

---

### Post by rfruth on 2006-11-05
Nothing like a good horror story, thanks :rolleyes:

---

### Post by cosmint_1973 on 2006-11-06
Yeah dude I just realized I started to forget XP chores. Using Edgy at home and Windoze XP at work. Well at work I am the local guru on PC's but now as I am less interested in Windoze at home I realized I started to forget a lot of Windows stuff. No regrets for me ...:)

---

