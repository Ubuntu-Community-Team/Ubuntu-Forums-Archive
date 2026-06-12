---
title: "Ubustu 8.04 setup"
date: 2008-05-26
forum: Ubuntu Studio
---

### Post by MWSTX on 2008-05-26
I'm only about 4 days into my linux experience and I am already 100% sold. Since I will still have XP on my machine at work, and after looking long and hard to make sure there wasn't something in Vista I would miss on my laptop, I have decided to strike all reference to microsoft from it. For several reasons (including "well, it can't hurt...") I am running DBAN on it right now. Since I have a few more hours to kill, I thought I'd see if I can get a few questions answered.

Aside from wasting hours on the web, my primary use for this computer will be audio recording (Ardour2 looks cool so far). Once DBAN is done I am going to do a fresh install of Ubuntu Studio 8.04 (64 bit). The machine is an HP Pavillion dv9225us w/ AMD Turion64x2 (2gig) with 2G of RAM and one 160G hard drive. I have the following questions regarding partitioning:

1) If I understand correctly, I can install everything on the drive without partitioning it. However, I have read a lot over the last few days (translation: read enought to get myself into trouble) about increasing performance and making it easier to re-install/update the OS by putting /Home on a seperate partition. Any reason for a linux noob not to do this?
2) If I do put it on another partition, how much space will Ubuntu Studio 8.04 require (how can I figure out how big to make the root)?
3) I've read some differing opinions on swap partitions. Given what I want to do with this machine, how big should I make it? How big is too big? Does there cease to be any benifit after a certain size?
4) Where should I put the swap partition? (beginning, middle, end?...)
5) Having figured out those two partitions, I'm wondering if I should make others for current or future needs. Would it be a good idea to have the data files associated with the audio recording (Ardour2) on their own partition? I have read (misc. article, not related to Ardour) that you should make several partitions since due to the way partitions are set up you can only add to the end of one. If you wanted to increase the size of partition 'X' you would have to have space available after 'X' (an empty partition, or one that could be emptied), although I'm not sure if that applies to logical partitions. I might someday get an external hard drive either to keep the recording files on and/or to back up all of my personal/data files and I want to keep that in mind as I plan.
6) If I do make several partitions, in what order should I put them (for hard drive efficiency) and what type of file system should I use (should they all be ext3 or could one or more of the partitions be better served with a different file system depending upon what is on that partition).

I've tried to research all of this but I feel like I'm only gleaning bits and pieces from several web sites and posts, all of which pertain only partially to what I'm trying to figure out. I thought it would be better to describe my machine & goals and see what people suggest. Like I mentioned earlier, I'm a complete noob to Linux but I was more than just a point & click user of windows (not an I.T. pro but more advanced than your average layman). I'm excited about getting this installation off to a good solid start.

---

### Post by Patb on 2008-05-26
Welcome.  It's good you are thinking about partitioning now, before installation, but I suspect you will get a wide variety of opinions on just what partitioning setup is ideal.  Therefore, continue to search, both on this forum and elsewhere, before you commit yourself.  You have possibly come across this: [http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

That said, your questions are very relevant, and there are a few points which are significant. I'll just comment on a couple:

> ... increasing performance and making it easier to re-install/update the OS by putting /Home on a seperate partition. Any reason for a linux noob not to do this?
Definitely make a separate partition for /home (note lower case - welcome to case-sensitive linux!).  The reason is not so much to do with performance but with the ease later of upgrading or installing a later release.   I cannot think of any reason not to.  The size will depend on how many users you expect to have - each will have a separate directory within /home.  By the way, I usually opt for 'manual partioning' during the install process because I like to be in full control.  

> Where should I put the swap partition?
I would suggest you leave that to Ubuntu.  The installation process will normally put the swap partition at the end but I believe it can be anywhere.  There might be potential disadvantages in not putting it at the end - I don't know.  Recommendations for the size of your swap partition are usually around 1.5 to 2 times the size of your RAM.  

Hope this helps. There may well be more specific advice from Studio users.  Cheers, Pat.

---

### Post by MWSTX on 2008-05-27
Thanks for the help but now I have bigger problems.  After a complete and total wipe of my hard drive, I tried to use the Ubuntu Studio 8.04 DVD that I burned for the 64 bit installation and almost got through it without problems.  On what looks like the last step of the installation process (right before I should see a pretty UBUNTU STUDIO graphic) I got a message that told me that the installation failed. It asked me if I wanted to go back and fix the failed step ("install new software" or something like that).  Doing that does not help.  None of the menu options would do anything to fix the problem or get me out of the set up menus so I gave the machine the 3 finger salute and now it will only boot to a linux command prompt:   blahblah@blah:~$
It WILL NOT go back to the Ubuntu Studio setup and it WILL NOT boot from a live cd (I have a regular Ubuntu 8.04 cd that I have sucessfully used a few days ago).  My dream of a clean install has backfired.  How do I get this machine to do anything other than blah:~$  ?

---

### Post by Stochastic on 2008-05-27
The good news is that if you get to the command prompt, then the core files are installed, and your OS is operational.  To get a GUI (desktop) up is only one step further.  Are you hard-wired to the internet?  If so, do ```
sudo apt-get install ubuntu-desktop
``` and see what it returns.

The fact that you cannot boot from a live cd scares me, and I won't even speculate as to why.  Anything the DVD installer did to your hard drive shouldn't affect the live boot process at all.  Even completely F*ing up your MBR shouldn't phase the liveCD.  It may be a bad sign that something is dangerously close to failing with your system (memory, processor, etc...).  Seek help on that as soon as you can from the General Help section of the forums.

---

### Post by ubundah001g on 2008-05-28
Note that you may want to see if your hard disk is damaged. You can check the hard disk, install a live cd, boot into a command promt and run "fsck" or the right one for the filesystem partition. If your system does not boot, then try to find out why. You can check the BIOS settings to make sure that it has the Boot from CD option set. You may want to try the installation again. You can also do a media check on the installation cd or dvd. Take a look at the cd and see if it has tons of scratches on it or is not clean enough to be fully readable. 

#cfdisk (repartition hard disk)
#mkfs.(type) (partition)
#fsck (type) (partition)
Reboot with installation cd and reinstall. 

If your hard disk has many damaged sectors, you may want to try a new hard disk, unless you don't mind losing data some time in the future if you don't make backups.

---

### Post by MWSTX on 2008-06-04
Thanks for the help.  As it turns out, there must have been a problem with the Ubuntu Studio DVD that I burned (even though I checked the MD5SUM & checked the integrity of the burn).  Once I downloaded the ISO from a different site everything went fine.

---

