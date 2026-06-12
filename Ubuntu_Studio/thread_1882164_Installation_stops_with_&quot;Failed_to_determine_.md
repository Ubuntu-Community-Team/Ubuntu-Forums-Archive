---
title: "Installation stops with &quot;Failed to determine code name . . .&quot;"
date: 2011-11-16
forum: Ubuntu Studio
---

### Post by tomryantx on 2011-11-16
I have run into a problem that apparently has been encountered in earlier releases of Ubuntu("Failed to determine codename of the release") in trying to install Ubuntu Studio 11.10. I believe the first evidence  of the difficulty in the install sequence is at "Retrieving dmraid-udeb" where I am told there is "a problem reading data from the CD-ROM. Please make sure it is in the drive . . . ." The installation continues through the partitioning sequence, but then gives me the "Failed to determine . . . code name" message. I have found a work-around in a couple of posts in the Installation/Upgrade Forum section that suggests modifying a script file, but I need more help to make the change in the script (if that's what I should do).

Any help or advice would be much appreciated.

Thanks,

Tom

Quote:
Originally Posted by justin.cherniak  
I ran into this issue with the 10.10 alternate installer. Note, at least on that disk, the file to edit is /var/lib/dpkg/info/cdrom-detect.postinstall.

Thanks for the help!

---

### Post by jejeman on 2011-11-17
Did you check md5 sums for iso file, burned dvd?

---

### Post by tomryantx on 2011-11-17
I hadn't, but I just did using winMD5Sum and the sums for both the downloads I did checked out correctly.

I did finally get past the "Failed to Determine the Code Name" stop. I returned to "Find and Mount CD-ROM" and "Detect System Disks" and removed and reinserted the CD-ROM at various points. I tried to systematize the process so I could describe it more clearly, but ultimately it seemed pretty random, which I guess could indicate a hardware problem with the drive (if you haven't already noticed, I have no idea what I'm talking about).  In some of my attempts I was allowed to partition the drive and set up a root account.

In any case, after the Install process relocated the drive, it started loading the  "base system" which proceeded joyfully until it froze again at "Configuring APT Sources." I've been able to go into a BusyBody terminal (but don't know what to do when I get there) and to see by pressing ALT F5 (or F4) the system's request for a name for the disk; it looks like the script is supplying ' ' which is not accepted. 

I'm trying to install it on an ACER Travelmate 800 with 512 MB of ram and an 80 GB hard drive. 

Thanks for any advice or help.

Best wishes,

Tom

---

### Post by sgx on 2011-11-18
You can clean the burner, buy a new burner, use different types of media, higher quality media, or a unetbootin install. Also, different ubuntu versions, and variants can be customized post-install to your desire. The apps are the same, and different repos and PPAs can be chosen, if some crucial apps are not as current, or as old, as you need. :popcorn:

---

### Post by tomryantx on 2011-11-26
The problem is solved. I was using without even noticing a DVD+R DL disc. When I switched to a non-DL 4.97 GB disc, the installation proceeded okay. 

Thanks for your help.

---

