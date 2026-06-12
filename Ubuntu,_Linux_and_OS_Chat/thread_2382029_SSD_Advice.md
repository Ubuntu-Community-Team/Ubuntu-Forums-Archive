---
title: "SSD Advice"
date: 2018-01-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2018-01-08
I would appreciate some ssd advice using ramdisk. I have ordered a ssd (Samsung evo 850) and have 8GB of RAM.  I am fairly comfortable installing the ssd, having read quite a lot recently, but have some questions re ramdisk.  Is it worth having a portion of ram set aside as ramdisk or is this not worth it as the ssd will be fast enough (I will be having a storage HDD but both / and /home will fit on the ssd with more than enough free space)?  It seems to me that as ramdisk looses data after shutdown then although a browser might run faster, if you save a new password, are you not going to lose it?  (I assume the same applies to Thunderbird re passwords, and in the context of saving an email to a local folder).  I have read about persistent ramdisk but why not make all of your RAM persistent?  So with my new ssd I'm unsure whether to a) leave the RAM alone b) setup 2GB ramdisk c) setup 8GB ramdisk. Is ramdisk more suited to servers rather than home Desktop machines?

---

### Post by oldfred on 2018-01-08
Linux keeps everything you have recently done in RAM.
[https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
I do some of above. I create my own trim in daily with logging, add noatime to mount of / in fstab and add a tmpfs mount in fstab.

---

### Post by Tadaen_Sylvermane on 2018-01-08
Ramdisk situational at best. I run my minecraft servers in a ramdisk. I run minecraft on my laptop in a ramdisk. But never found a use outside of that for a ramdisk other than what Ubuntu does on it's own. I also don't do anything special with an ssd either. Current gen ssds are rock solid and don't need a bunch of care or special settings. Ubuntu runs trim by itself automatically.

---

### Post by Quarkrad on 2018-01-08
Thank you - very useful links.  In section 9 of [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) it says: **When you have more mounted EXT4 partitions, you'll have to adapt the command line accordingly. For example, if you have a separate home partition (although that's not very useful), then the command is:** Is this the case for SSD (as oppose to HDDs)?  For sometime on my HDD I have had separate / and /home partitions to make new OS versions easier to install.

---

### Post by oldfred on 2018-01-08
The noatime mount option just prevents writing to drive every time you access a file. You can use it on HDD also. But a very few applications (mutt) want that info updated. 
see this for more details:
man mount 

 Info on trim and ext4 without journal, ext2 does not support TRIM, with newer SSDs relatime a reasonable alternative to noatime and works with some apps that need timestamps like mutt 
I normally use relatime on HDD partitions I mount.

---

### Post by Quarkrad on 2018-01-08
Sorry - I did not explain myself clearly.  I am happy with the fstab additions - my reading of the bold text in #4 is that it is suggesting not to have separate **/** and **/home** partitions, i.e. mounting everything under**/** (a single partition for ubuntu).  Additionally (not related to #4), I am thinking of putting the swap partition on the HDD and mounting to the specific UUID via fstab (as well as assigning vm.swappiness=1 in etc/sysctl.conf .

---

### Post by oldfred on 2018-01-08
For very new users, I typically suggest just / and a bit larger.
Then for regular users a separate /home may offer advantages as it adds entry to fstab, and sets ownership & permissions.

But for more advanced users and with an SSD, you have keep /home inside / (root), but then mount additional data partition(s). The disadvantage is you have to edit fstab and link or mount those partitions into /home and set your own ownership & permissions so you can use them. The user setting are then on SSD, so those also load quickly, but data which is not loaded as often is on slower HDD.

 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below. 
   The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Quarkrad on 2018-01-11
A neighbours machine I look after suffered serious hw problems yesterday so I find myself building a new pc(!). We opted to go for a (Kingston) 120gb ssd but I find it reads as 111.79gb.  Looking into this it appears the Sandforce Controller in this device reserves about 6.8% of the drive for over provisioning.   (The same applies to their 240gb drives - they read 223.57).  I had planned to leave 10gb unallocated (this has been recommended elsewhere) but now unsure whether to un-allocate a further 2gb to give me the approx 10gb unallocated or actually un-allocate a further 10gb giving me only a 101gb drive. Sorry to be a pain but my experience is only with mechanical drives - this unallocated space for over provisioning is a new thing.

---

