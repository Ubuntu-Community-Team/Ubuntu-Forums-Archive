---
title: "I moved /home and lived to tell the tale ! :)"
date: 2013-09-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Coder88 on 2013-09-09
Never had done it before, but I decided to pull the trigger and try moving /home and it worked. A few minor glitches but I did not panic, I had enough confidence I would use the rescue command shell as well as a live distro CD to do what needed doing. I made the mistake of creating a 10GB home partition during the install, thinking it would be enough space, and it would be normally as my music and videos are on an ntfs data drive. But I forgot about GAMING. I realized I will need a lot of space for native linux, steam linux, and Wine PC games on linux. Luckily I had plenty of unformatted space on the linux sata drive so I made a new 800GB ext4 partition and moved /home. I figure i earned 10 geek points doing this!

---

### Post by grahammechanical on 2013-09-09
I crashed and burned when I tried that a few years ago. I did not relealise that I had to tell Ubuntu that the configuration files in /home folder had moved to another partition. After a lot of head scratching and worry, I solved it by re-installing and pointing /home to the new partition and everything set up fine. I also got in some practice at saving data by moving it to another partition.

Regards.

---

### Post by buzzingrobot on 2013-09-09
I've followed directions here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) to move home to a new drive.  They are thorough and intended to avoid inadvertant loss of data.

---

### Post by monkeybrain20122 on 2013-09-09
Where is the unformatted space? If it is on the same drive can you not just expand your /home with gparted?

In general I find it easist to use fsarchiver to clone the / and(or) /home and then restoring them in different drive or partitions.

---

### Post by Buntu Bunny on 2013-09-09
> **buzzingrobot said:**
> I've followed directions here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) to move home to a new drive.  They are thorough and intended to avoid inadvertant loss of data.

Thanks for the link buzzingrobot.

---

### Post by RichardET on 2013-09-09
On my old Sparc Sun Blade 100, I have two 15 gig drives - I know it's old, but it still works!  I use one drive for all system related folders and the other dive is mounted /home.  With Ubuntu on my Lenovo W530, I still have a separate /home, but it is all one 200 gig drive.

---

### Post by deadflowr on 2013-09-10
> **Coder88 said:**
> Never had done it before, but I decided to pull the trigger and try moving /home and it worked. A few minor glitches but I did not panic, I had enough confidence I would use the rescue command shell as well as a live distro CD to do what needed doing. I made the mistake of creating a 10GB home partition during the install, thinking it would be enough space, and it would be normally as my music and videos are on an ntfs data drive. But I forgot about GAMING. I realized I will need a lot of space for native linux, steam linux, and Wine PC games on linux. Luckily I had plenty of unformatted space on the linux sata drive so I made a new 800GB ext4 partition and moved /home. I figure i earned 10 geek points doing this!

Did you do the, more common than you would think, make root huge and make home tiny scenario when you first did your install?
You know, make root something like 480gb and home 10gb. 
I once made swap 20gb because I misread a zero. I forget what I did to fix it, though. I resized it, but can't remember if I merged the unallocated space somewhere or not.

---

### Post by codingman on 2013-09-10
I thought that the title of this thread was: I moved home and lived to tell the tale!

And it would be about some crazy Linux story of moving back home and telling some people about how Linux is... no joke.

Back on topic: Moved home once, and all of my files got duplicated, was a disaster. Luckily I didn't care about the computer, so I just reformated and installed Debian Stable, due to the fact that the computer was old.

---

### Post by philinux on 2013-09-11
I successfully did this years ago and then ext4 came along. Backed up and did a full format.

Recently I decided that if I wanted a clean install this had to include home so to clear out all the config files etc. I now have just root and a data partition. The data partition is used to back up the firefox, xchat and evolution folders. The rest gets nuked on install.

---

