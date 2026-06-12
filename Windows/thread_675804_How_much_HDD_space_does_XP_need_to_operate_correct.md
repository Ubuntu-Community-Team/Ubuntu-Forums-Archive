---
title: "How much HDD space does XP need to operate correctly?"
date: 2008-01-23
forum: Windows
---

### Post by TheOrangePeanut on 2008-01-23
I'm dual booting Windows because I need it for some classes.  My Windows partition has 16.5 GB free space, but I will be installing some pretty heavy hitting programs I think, including the Java JDK and an IDE, Visual C++ 2008 (or 2005 if it is still free), and Microsoft Publisher and Visio.  I'm worried I'm going to run out of space; I know Windows needs a certain amount for swap or virtual memory or whatever they call it in Windows.  Do you guys think 16 GB is going to be enough?

---

### Post by yaknowwat on 2008-01-23
Erm i would suggest getting a windows XP with SP3 RC already in it.
search around its legal to download and use it as long as you dont use a pirated code.

This will save you about 4 GB's from UPDATES on windows XP SP 2

then windows XP will start off needing 2GiB that way. after updates since MS will stop XP support in 2k9 I would save XP will need 3.5GiB.

Swap file for XP will come out to 1.5x your RAM.

Java JDK will take about 400MiB
Then IDE will take around 700MiB
Visual C++ 2k8 around 1-2 GiB (depends on if you get the Game Part to)
Keeping the installers just in case 600 MiB

Then for programming you'll want 2 GiB HDD space at least for each one.
so add 6-7 GiB

( 12.2-14.2 GiB + 1.5x Your RAM )

This is a rough estimate it could come out to more depending how many step point in programming you leave icons pictures you want for the product though that never comes out to much.

also use CCleaner often :P

Also your posting this on a linux forum do you just wnat these things so you can switch between windows and linux yet program at the same time?

Visual C++ is not a good cross platform program maker so you know as it has shortcuts etc added by Microsoft to mess with cross platform portability.

---

### Post by TheOrangePeanut on 2008-01-23
Whew, looks like it is going to be close!  And I have to have Windows because of some classes of mine.  Besides the obvious (Publisher, Visio), I need Visual C++ on Windows because I'm doing a 3d programming class in OpenGL and my Linux drivers can't do 3d at all.  I may be able to get away without the Java SDK, I'm not sure what language we're using in Databases, but I'm hoping it is something I can install on my Linux Partition.

---

### Post by JDorfler on 2008-01-23
Okay, here we go,  I am not sure if you have already installed WinXP and Ubuntu yet, but this how I did it.  I have a Sager 5680, with a brand new 80 GB HDD, so I have to be careful what I put on and how.

First boot up with your WinXP disk.  Using the WinXP partition manager create two partitions.  The first one as NTFS, name it WinXP OS, and have it about 20 Gigs.  Install your WinXP OS here.  After installation, do not download any updates.  Immediately after install run your defrag 3 times after you set your Virtual Memory to 0.  I don't know why it's the number 3, but a smarter man than I recommended this. 

 Reboot your PC with your Ubuntu Live disk.  There, use the Partition Manager to cut up the rest of your Hard Drive into 3 more partitions.   The Second Partition as Ext3 and primary, the third will be your swap.  (RAM x 2 = Swap Partition size for me) and the forth will be NTFS.  I label this one Programs.
After doing this Install Ubuntu using Ext3 partition in the manual install mode.
Make sure you right click Ext3 and make sure you label it (./) not root or anything else.

Now, what's great about Ubuntu is it reads and writes to NTFS.  With this in mind you can always keep your Thunderbird Mail folders in sync with both your WinXP and your Ubuntu.

Now, go back to your WinXP via Grub and set your min and max virtual memory.  Again I use RAM x 2 = Virtual Memory.  (This helps a lot with fragmentation)  Then download ALL your updates.  It's a lot, so if you have a slow connection and trust your pc to not lock up, go play a round of golf.

After you get back from your 18, go ahead and take a shower, clean your clubs, inventory your balls, or whatever it is you want to do.  Now, I am pretty sure you have a ton programs you want to install.  This is where your second NTFS partition comes into play.  I named mine, Programs.  Make sure you always to a manual install of every piece of software you install, and also make sure it is installed on this second NTFS partition.

Now, to keep your email email synced.  Install the latest version of Thunderbird.  Go ahead and set up your accounts as normal.  DO NOT AUTO DOWNLOAD ANY MAIL!  Just set up your accounts.  Now.  This is the important part, make sure you have all hidden folders able to be viewed.  If you don't want to do this WinXP, go ahead and boot into Ubuntu and do this.  Use your file manager to copy your email folder from your WinXP OS partition and place it into your Programs partition.  The path will be something like this:

Documents and Settings > (Your WinXP Profile Name) > Application Data > Thunderbird > Profiles > (bunch of letters).default > Mail

Copy (do not Cut)  the Mail folder and place it anywhere you want in your Programs Partition, but remember where you placed it.

Now, go into your WinXP Thunderbird and got to account settings and the Server Settings  to each email account you have on there and change the path to"
 Program/Mail/(and that particular mail account's name.) 

It's best to use Browse in order to do this.

Go to Ubuntu, download Thunderbird, set up your email accounts, and have Thunderbird look into the exact same folders as you set up in WinXP.

You can also do the same thing as all the above for your Newsgroups as well.

Now, this is a huge warning.  If you have an anti-virus program in WinXP like AVG, it will only scan emails that are coming in whilst in WinXP.  All emails downloaded in Ubuntu will not be scanned.  Thus, if you're not sure about an email whilst in Ubuntu, delete that email from your system immediately before returning to WinXP.

The quick and dirty way of syncing your Lightning is to use the Google Provider extension.  Also, using the Foxmarks in Firefox to help you sync your bookmarks in either WinXP or Ubuntu.

Now, you can download your emails until your heart's delight.  If you download and read them in Ubuntu, they'll registered as downloaded and read in WinXP, or vise versa.  Have fun.

---

### Post by yaknowwat on 2008-01-24
> **TheOrangePeanut said:**
> Whew, looks like it is going to be close!  And I have to have Windows because of some classes of mine.  Besides the obvious (Publisher, Visio), I need Visual C++ on Windows because I'm doing a 3d programming class in OpenGL and my Linux drivers can't do 3d at all.  I may be able to get away without the Java SDK, I'm not sure what language we're using in Databases, but I'm hoping it is something I can install on my Linux Partition.

oh. hmm no 3D what graphics do you have on your computer?.

anyways I'm not sure if you would like it but a decent development program that Im using in Linux to learn C++ or at least try is 'Eclipse' It also has support for Java.

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

There's a version of it for all 3 major platforms.
Linux, Mac OS X, Windows.

though for C++ when you make a project to ease things up i suggest using ' managed ' instead of ' standard ' helps with compiling quicker.

---

### Post by LittleLORDevil on 2008-01-24
Eclipse is awesome I use it for my Java projects and with the CVS repository functions it makes team projects so simple to manage.

---

