---
title: "Woe to Ubuntu"
date: 2011-05-07
forum: Testimonials &amp; Experiences
---

### Post by HayManMarc on 2011-05-07
It appears that my love affair with the great linux OS Ubuntu may be coming to an end.

I first found Ubuntu and Linux several years ago (ver. 9.04 I believe(?) Jaunty Jackalope) and was amazed and in awe that I could have such a wonderful OS for my old laptop for FREE!  I had since upgraded a couple times, hit and miss over the years and dutifully put up with a few buggy snags.  However, just this past couple of weeks, I decided to upgrade the HDD and the RAM on the laptop and install the new version 11.04.  Much to my dismay, I could not for the life of me get the thing to install.  After many failed attempts, while trying to find help from the Ubuntu internet help and such, I've managed to gum up my brand new 320 GB HDD with a bunch of non-working Ubuntu data written over the top of one another. Now I have five days of HDD clean-up to decide what to do.

I'm pretty upset about this.  Ubuntu brags about it's ease of use and it's ability to be used by non-linux-programming-experts, but I can't even install it on a blank HDD all by itself???  What's up with that?  I understand Ubuntu is a free product, but at least it ought to work.

I haven't made up my mind what to do yet.  I'm frustrated and upset.  I like Ubuntu and I want to use it, but if I can't, then I'll have to find something that I can install.  (openSUSE, Fedora, RedHat, ... ...)

error: out of disk
grub rescue>_

error: no such partition
grub rescue>_

error: out of patience
rescue your grub, Ubuntu, so I can love you again.

---

### Post by mikewhatever on 2011-05-07
Sorry to hear you've had problems with 11.04. As this seems to be a testimonial, you should probably open a proper help request thread and explain the problem. While Ubuntu is a very good distro, other distros (including the ones you mentioned) are good too, and if some of them happen to work better for you, by all means, use them. I honestly doubt that people here will try to discourage you.
Good luck with however you wish to proceed.

---

### Post by Quackers on 2011-05-07
Well, if you're getting grub rescue prompts something must be installed (or partly) :-)
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by brettski74 on 2011-05-07
Is this still your old laptop? How old is it? I notice that you've upgraded your hard disk to a 320Gb drive. How is it partitioned?

I recently had some problems setting up some USB boot drives. They worked perfectly on one of my machines, but on the other always failed. After several days of pulling my hair out, I realized that it could be a BIOS problem. Some BIOSes - particularly older ones - may be unable to deal with partitions larger than 128Gb. When I was using GRUB as the bootloader on a machine with such a BIOS, it would always end up at the GRUB rescue prompt. EXTLINUX (another bootloader) also had problems booting. Once I changed the partitioning scheme to put all the boot files on a smaller partition, the problems went away and the drives booted perfectly on all my machines.

If you've been partitioning your drive as one big partition, re-try the installation with a smaller root/boot partition (ie. less than 128Gb). There are several ways you can do this. My usual partitioning scheme usually uses 4 partitions in the following order:

   - a small partition (around 100Mb) for /boot
   - a reasonable sized swap partition (eg. 4Gb)
   - a good sized root partition (around 32Gb on my current machine). Note that by root partition I mean mounted as /, not /root.
   - the remainder of the space for /home

This avoids any potential BIOS problems at boot time because all of your boot files are in that small 100Mb partition at the "front" of the disk.

I hope this helps.

---

### Post by akand074 on 2011-05-08
Manual installs are always the least likely to hit errors. I've helped  several people get a working install by walking them through a manual  install (pretty straight forward). What's your problem too? Just the  grub rescue thing after the install? 

> **HayManMarc said:**
> I'm pretty upset about this.  Ubuntu brags about it's ease of use and it's ability to be used by non-linux-programming-experts, but I can't even install it on a blank HDD all by itself???  What's up with that?  I understand Ubuntu is a free product, but at least it ought to work.

Because it didn't work for you, it doesn't work at all? I dislike when people bash Ubuntu or anything in general for not working with a sample size of "1". The amount of people that ran into your problem installing 11.04 is a very low percentage (<1% likely). This stuff happens, with Windows too. Try a manual install (choose "something else" from the install), you can find out how to do it pretty easily, but you can ask for help here or PM me if you need too. Or do the bootinfo script thing as explained above and try to fix your current install if you want as well.

---

### Post by tgalati4 on 2011-05-08
I have an older (2006) Thinkpad T43p.  It had an 80 GB drive.  I copied it to a 320 drive, then used gparted to fill the remaining space ~240 GB as an unused linux partition.  Then swapped drives.  So now I have a backup 80 GB drive (in a USB enclosure) and a fast 320 GB drive in my laptop.  I've been running Jaunty without issues for the past 2 years.

My set up looks like:


tgalati4@tpad-Gloria7 ~ $ sudo fdisk -l
[sudo] password for tgalati4: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9af89af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3298    26491153+   7  HPFS/NTFS
/dev/sda2   *        3299        8397    40957717+  83  Linux
/dev/sda3            8398        8716     2562367+  82  Linux swap / Solaris
/dev/sda4            8717       38913   242557402+  83  Linux
tgalati4@tpad-Gloria7 ~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              39G   25G   13G  66% /
tmpfs                 944M     0  944M   0% /lib/init/rw
varrun                944M  400K  943M   1% /var/run
varlock               944M     0  944M   0% /var/lock
udev                  944M  152K  943M   1% /dev
tmpfs                 944M  3.5M  940M   1% /dev/shm
lrm                   944M  2.2M  941M   1% /lib/modules/2.6.28-18-generic/volatile
firefox               128M   66M   63M  51% /home/tgalati4/.mozilla/firefox/4n0pfp5v.default
/dev/sda1              26G   21G  4.9G  81% /media/WinXP

I would start with Lucid as an upgrade to Jaunty.  Natty seems to have a few issues.

Unless you like that sort of thing.

---

### Post by d3v1150m471c on 2011-05-08
you can do a grub rescue post installation with a livecd. also, it's good to be proactive and see what hardware is compatible before you go installing it and expecting it to work. Here's 10 seconds of google searching that could have saved you 10 hours of grief: [http://www.linuxquestions.org/hcl/index.php](http://www.linuxquestions.org/hcl/index.php)

---

### Post by Linux BASHer on 2011-05-08
HayManMarc, I know how you feel. You can read my own ["testimonial"]("http://ubuntuforums.org/showthread.php?t=1750874") on this board. I understand there is no such thing as 100% compatibility with so many hardware manufacturers and closed specs and drivers. But I find it a little ridiculous that a relatively populat Asus netbook is not fully functional out-of-the-box. Unfortunately, Ubuntu is not where it sometimes makes it seem like they are. On top of that, though I'm glad Canonical is taking the GUI into its own hands, Unity does not seem to be the answer, at least right now.. So I am also considering jumping ship to another distro.

That said.. we must remember that we while we do not owe the Linux dev community anything, they do not owe us anything in return either, although of course, we should all be grateful for great software. Hopefully you can figure this out. Otherwise, go ahead and jump to another distro. One of the great things about Linux is the cross-pollination going on all the time. You might find another distro you like more, or come back later to see your issues fixed. Either way, I hope you get your system working again.

---

### Post by bapoumba on 2011-05-08
Moved to Ubuntu Testimonials & Experiences.

---

### Post by HayManMarc on 2011-05-08
I'm sorry, Ubuntu community.  My first post was a sore rant.  I just wanted to convey my feelings.  I  haven't given up yet.  I like Ubuntu too much to jump ship without a  fight.  I'm extremely frustrated, but I'll control my lashing out better  from now on. :S

@brettski -- I've tried 3 partitions, but not  four.  I'll try 4.  I did not partition for /home.
As I'm writing this  (on my desktop computer), I'm trying to install 10.04 Lynx on 3 partitions.  We'll  see how that goes.

Here's my system:  reconditioned HP ze5470us  laptop, original 15 GB HDD replaced with WDC 320 GB, RAM upgraded from  512 MB to 1024 MB (max).

I don't think the 15 GB HDD was original  equipment.  Also. the label on the screen says HP pavilion ze5400, so  that must have been replaced.

Here's the deal.  When I got the  laptop, I wasn't able to install windows xp because the key didn't match  the hardware anymore.  So, only barely having heard about Linux, I  looked it up online.  I found Ubuntu without much effort and gave it a  go. It was version 9.04 (I still have the disk I made) and it worked  perfectly (except for the wireless, which I could live with).  I  upgraded once to 9.10 (I think), but sometime after that the HDD crashed  and died. The laptop sat unused for some time.

Fast-forward to  now, and my current problem.  My main stink was this: version 9.10  worked fine on this somewhat Frankenstein laptop with very minor issues  that I was able to iron out.  I think I even got the wireless to work  before it died.  But a clean, fresh, virgin install of an updated newer  version of Ubuntu (11.04) on a brand new HDD gave me grub rescue.  After  trying several things to make it work, the technical level of the help  outweighed my patience thus bringing me to this forum for a rant  session.

I was kinda thinking Ubuntu wasn't wiping the drive  clean enough or something, so I downloaded DBAN utility and let that do  it's thing on the HDD.  I'm starting over.

Again, I apologize for my rant in frustration.  I'll post again after (if) 10.04 Lynx installs and give an update.


EDIT:  Update: Installation of Ubuntu 10.04 Lucid Lynx successful!  Installed without a hitch!  Now, Id like to upgrade to 11.04, but I'm afraid.  :)

---

### Post by kaldor on 2011-05-08
Whenever I install Ubuntu (I fresh install every upgrade) I use Gparted from a Live CD to "Create Partition Table" or whatever it said. That leaves it blank, and then I proceed to install Ubuntu with "use all space" option. Only had one install issue ever; I used a new CD and reburnt it, and it worked. Maybe it's just a bad download/CD?

Also, if you do jump ship to another distro, I strongly recommend Scientific Linux 6.0. I've been using it for a few days. It's based on Red Hat Enterprise Linux, meaning it's very robust and stable. You also get updates until 2017, I believe... perfect Long Term Support OS ;)

---

### Post by mikewhatever on 2011-05-08
> **HayManMarc said:**
> ...

EDIT:  Update: Installation of Ubuntu 10.04 Lucid Lynx successful!  Installed without a hitch!  Now, Id like to upgrade to 11.04, but I'm afraid.  :)

Why upgrade? Seriously, what are the reasons? 10.04 is stable and works well for you, and it's not a new laptop that requires a recent kernel for better hardware support. I'd strongly encourage you to stay with the LTS, unless there are compelling reasons to upgrade.

---

### Post by d3v1150m471c on 2011-05-08
> **HayManMarc said:**
> 
EDIT:  Update: Installation of Ubuntu 10.04 Lucid Lynx successful!  Installed without a hitch!  Now, Id like to upgrade to 11.04, but I'm afraid.  :)

Congrats. 10.04 is an excellent version. That's what I use, as it's supported till 2013 (i think), being an LTS. I'm not looking foward to using unity or having it installed so I'm riding it out lol.

You might check out this thread, [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) I used the same method to do backups and it works almost flawlessly. Just be sure to exclude any files you don't need to backup with the --exclude=/path switches. You might also want to try apt-oops from my website below if keeping a backup of debian packages and dependencies is something you need.

---

### Post by HayManMarc on 2011-05-08
In case my edit was missed--

 Installation of Ubuntu 10.04 Lucid Lynx successful!  Installed without a  hitch!  Now, Id like to upgrade to 11.04, but I'm afraid.  :smile:

Thanks everyone for your replies.  It's very nice to get support, especially when my attitude is a bit stinky.

---

### Post by mikewhatever on 2011-05-08
> **HayManMarc said:**
> In case my edit was missed--

 Installation of Ubuntu 10.04 Lucid Lynx successful!  Installed without a  hitch!  Now, Id like to upgrade to 11.04, but I'm afraid.  :smile:

Thanks everyone for your replies.  It's very nice to get support, especially when my attitude is a bit stinky.

There is no way to upgrade directly from 10.04 to 11.04, you'll have to go 10.04->10.10->11.04. If that's what you want, check out the howto -> [https://help.ubuntu.com/community/MaverickUpgrades#Upgrade%20from%2010.04%20LTS%20to%2010.10](https://help.ubuntu.com/community/MaverickUpgrades#Upgrade%20from%2010.04%20LTS%20to%2010.10)

---

### Post by d3v1150m471c on 2011-05-08
> **mikewhatever said:**
> There is no way to upgrade directly from 10.04 to 11.04
Actually you can but it most likely will not be a smooth process. Upgrading from 9.10 to 10.04 wasn't even smooth and that was recommended. Any time you plan on doing an upgrade always take the time to make a backup. See my post above ^^^

---

### Post by wolfen69 on 2011-05-08
> **mikewhatever said:**
> why upgrade? Seriously, what are the reasons? 10.04 is stable and works well for you, and it's not a new laptop that requires a recent kernel for better hardware support. I'd strongly encourage you to stay with the lts, unless there are compelling reasons to upgrade.

+1

---

### Post by brettski74 on 2011-05-08
Was going to point something out, but then noticed you've already successfully installed Lucid and I can't find a post delete button...

---

### Post by tgalati4 on 2011-05-08
Stick with Lucid for 6 months.  Then, add another partition and install natty.  Expect to have a few problems.  If the problems are severe, then you can dual boot back into Lucid and at least have a working system.  My credo is to never trash a working system.

---

### Post by Tamlynmac on 2011-05-09
> tgalati4
My credo is to never trash a working system. 	

Wisdom. I couldn't agree more with your credo.

---

### Post by collisionystm on 2011-05-09
> **HayManMarc said:**
> I'm sorry, Ubuntu community.  My first post was a sore rant.  I just wanted to convey my feelings.  I  haven't given up yet.  I like Ubuntu too much to jump ship without a  fight.  I'm extremely frustrated, but I'll control my lashing out better  from now on. :S

@brettski -- I've tried 3 partitions, but not  four.  I'll try 4.  I did not partition for /home.
As I'm writing this  (on my desktop computer), I'm trying to install 10.04 Lynx on 3 partitions.  We'll  see how that goes.

Here's my system:  reconditioned HP ze5470us  laptop, original 15 GB HDD replaced with WDC 320 GB, RAM upgraded from  512 MB to 1024 MB (max).

I don't think the 15 GB HDD was original  equipment.  Also. the label on the screen says HP pavilion ze5400, so  that must have been replaced.

Here's the deal.  When I got the  laptop, I wasn't able to install windows xp because the key didn't match  the hardware anymore.  So, only barely having heard about Linux, I  looked it up online.  I found Ubuntu without much effort and gave it a  go. It was version 9.04 (I still have the disk I made) and it worked  perfectly (except for the wireless, which I could live with).  I  upgraded once to 9.10 (I think), but sometime after that the HDD crashed  and died. The laptop sat unused for some time.

Fast-forward to  now, and my current problem.  My main stink was this: version 9.10  worked fine on this somewhat Frankenstein laptop with very minor issues  that I was able to iron out.  I think I even got the wireless to work  before it died.  But a clean, fresh, virgin install of an updated newer  version of Ubuntu (11.04) on a brand new HDD gave me grub rescue.  After  trying several things to make it work, the technical level of the help  outweighed my patience thus bringing me to this forum for a rant  session.

I was kinda thinking Ubuntu wasn't wiping the drive  clean enough or something, so I downloaded DBAN utility and let that do  it's thing on the HDD.  I'm starting over.

Again, I apologize for my rant in frustration.  I'll post again after (if) 10.04 Lynx installs and give an update.


EDIT:  Update: Installation of Ubuntu 10.04 Lucid Lynx successful!  Installed without a hitch!  Now, Id like to upgrade to 11.04, but I'm afraid.  :)


Just because its a free OS does not mean you can use old hardware ;)

Ubuntu is becoming rather updated and does need fresh hardware to do its thing. I suggest buying a new Vostro laptop. Ubuntu works perfect on them. I just installed on an 1014 that came out of the box today. Everything worked 100%..

---

### Post by Linux BASHer on 2011-05-09
> **HayManMarc said:**
> Installation of Ubuntu 10.04 Lucid Lynx successful!  Installed without a  hitch!  Now, Id like to upgrade to 11.04, but I'm afraid.  :smile:

Thanks everyone for your replies.  It's very nice to get support, especially when my attitude is a bit stinky.

Your attitude is human. Did the same thing myself. Now back to a fresh install of 10.04. Much happier. I didn't even have to fix the wireless this time. It looks like it's been properly patched. Hopefully 11.04 will receive the same fixes come time. I experimented with several other distros and I got the same kind of errors on many of them. It looks like its a kernel issue that cuts across many distros.

Frankly, my system is just for writing and browsing. I should have left it alone, but the tinkering geek in me wanted to upgrade. Truth be told, a "productivity" system and a tinkering "hobby" system are two different things. Debian is supposed to be about stability anyway. It's Ubuntu that takes it to the "cutting edge", but stability should be the number one concern for a critical system, and that's what I'm getting with 10.04 right now.

---

### Post by arunb on 2011-05-10
I have a brand new Acer Aspire 5745, i5 core 500 GB hard disk, 4 GB RAM.

And Ubuntu 10.04 works perfectly on it.

---

