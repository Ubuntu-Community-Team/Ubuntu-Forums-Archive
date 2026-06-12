---
title: "Post your Linux Horror Stories"
date: 2009-06-18
forum: The Cafe
---

### Post by aphexcoil on 2009-06-18
Here are my two favorite:

1.  I was rushing and needed to get going but I needed to clean out every file under the /var/www/thumbs folder because it had too many images.  I was switching back and forth between two ssh terminals and thought I was in /var/www/thumbs when I did a "sudo rm *.*" but instead I was in /var/www.  This is why backups are so very important.

2.  I set up a cron job for a process that needed around 5 minutes to run -- sometimes 10 max.  So I decided to schedule it every two hours to balance the need for updating a particular application and using up resources.  

I loaded up crontab -e with nano and proceeded to type in my once every two hour syntax.

* */2 * * * (command) >> (log)

Needless to say, when I came back an hour later, I had 50+ processes all trying to do the same thing and corrupting data in the process.  What?  I put a */2 in the hour field!  It should run every other hour!!  My cron was broken!  

Nope.  I just didn't realize it was going to run every minute every other hour and take an hour break for the others.  

Moral of the story -- don't rush important things and when something complicated isn't working, look for the simplest possible reason.  

(Now happily using cron with 0 */2 * * *)

:popcorn:

---

### Post by HappyFeet on 2009-06-18
> **aphexcoil said:**
> 
Moral of the story -- don't rush important things and when something complicated isn't working, look for the simplest possible reason.  


That's usually the case as with anything in life. But sorry, I have no linux horror stories to share. Everything (for the most part) works as advertised. Plus, I keep all important stuff on separate drives. And then I backup the separate drive on another drive. That way if my main OS drive goes bad, (hasn't happened ever) I'm covered.

---

### Post by cariboo on 2009-06-18
> **HappyFeet said:**
> That's usually the case as with anything in life. But sorry, I have no linux horror stories to share. Everything (for the most part) works as advertised. Plus, I keep all important stuff on separate drives. No backups needed.

What if the separate drives fail? I always have at least two current backups of my important files.

---

### Post by aphexcoil on 2009-06-18
> **cariboo907 said:**
> What if the separate drives fail? I always have at least two current backups of my important files.

One thing I learned a long time ago about backups is this:

1.  You can never have too many.

2.  You should never have them all physically in the same area.

3.  You should always keep them up to date.

4.  You should occasionally run "blow up" drills to make sure you can recover successfully and quickly from a system failure.

I lost a ton of old project samples and god knows how many years of e-mails when I took a hard-drive out and moved and my little brother thought it would be awesome to have 300 gigs of extra storage.  I don't fault him -- it was my fault.  If the data is important enough to miss, it is important enough to backup.



*"I'd rather have a file full of timestamps with no information than a file filled with information with no timestamps." -- old boss who programmed by moving rocks around.*

---

### Post by HappyFeet on 2009-06-18
> **cariboo907 said:**
> What if the separate drives fail? I always have at least two current backups of my important files.

I think the chances of 2 backup drives going bad at the same time is very remote. (plus I have a UPS so my computer won't get fried) If 1 were to go bad, it would quickly be replaced with another. No problem. Plus, I actually have a third (flash) drive that I sync once a month or so. I'm not too worried. Beyond what I do for backup is, how you call it, anal retentive?

---

### Post by Clorow on 2009-06-18
I used Wubi. I think my signature says it all, but I'll go into detail.

A long time ago, I installed Ubuntu via Wubi. I was fine for a while, until a few months later, the computer crashed while software was installing. I thought "no big deal," so I restarted the computer.

The computer threw a bunch of errors at me. I freaked out.

I backed up all my personal data using an Ubuntu Live CD. I was still freaking out. I ran fsck, and everything was fine... for Ubuntu.

I tried booting into Windows, and it said "Windows did not shut down normally. Choose one of these options:"

No matter which option I chose, they all apparently meant "reboot."

So I'm just using Ubuntu now, and my brother got angry at me when he got home from college because he wanted to play his games and stuff.

Moral of the story: **Don't use Wubi for long term use. It's just for trying Ubuntu.**

---

### Post by Twitch6000 on 2009-06-18
I think the only horror story that I have had is finding a distro I like and can work with 100% of the time.

OH wait I am still in this story lol..

Don't worry though I will find a distro darn it lol..

---

### Post by HappyFeet on 2009-06-18
> **Clorow said:**
> 
Moral of the story: **Don't use Wubi for long term use. It's just for trying Ubuntu.**

I agree. "Ain't nothin like the real thing baby". (older folks may remember that)

---

### Post by Mighty_Joe on 2009-06-19
Never, ever, Ever, EVER do an upgrade without testing the Live CD.  Even then, don't upgrade.  Buy a new hard drive and install to that.  And backups.  Lots of backups.
I had a solid system with Ubuntu Fiesty Fawn.  I upgraded to 7.10 via Synaptic and kaboom - system locks up within minutes of a boot.  I can't downgrade to 7.04.  I have gigs of data and documents and I don't have enough space elsewhere to move them. I'm boned. ](*,)
After a day or two of sweating, I ended up using Gparted to create a new partition, install 7.04 to that and mount my "old" home directory in the new install.  
After I saw the same problem in 8.04, I filed a bug and discovered the problem was a [discrepency between the kernel and X on which should set the AGPMode]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/141551")

---

### Post by fatality_uk on 2009-06-19
What have the issues got to do with Linux. They aren't Linux horror stories, they are PC user horror stories. What you were doing is not what average users will usually get into, so from that point of view, you should have taken more care.

---

### Post by dragos240 on 2009-06-19
I've had too many windows horror experiences and zero linux horror stories. Too many windows ones to count.

---

### Post by Eisenwinter on 2009-06-19
I was experimenting with installing a chroot Arch 32bit system within my Arch 64 system.

After playing around with it for a little, I decided it's time to get rid of it, so I rm -rf'ed its' folder.

What I didn't know was my home folder was somehow linked to it... you can guess what happened... my entire home folder was deleted too, along with all the configuration files and perl scripts I've written.

It took me 10 minutes to set everything back up, but it was annoying, as it shouldn't have even happened.

---

### Post by The Real Dave on 2009-06-19
Not Linux's fault, but a horror story all the same. Had recently upgraded from 8.04 to 9.04 (made a partimage of 8.04 and installed over it), and after 3 or 4 days, had just got it how I liked it, Compiz, programs, the lot, and had yet to make my backups.

And I had also just download, and tried out Windows 7 in Virtualbox, liked it, and wanted to try it natively. So gparted my 80Gb drive (used for DVD files, seperate to the 320Gb that all my data, and OS's are on) and installed Windows 7.

Unfortunately, forgot to unplug my 320Gb drive to prevent it being able to touch that. 

So, when I booted 7, I noted that GRUB was gone, and made a mental note to put that back soon. Went into 7, into Computer manager to see how it was working with my hardware, and then popped into disk management. 7 found 50Gb's of unpartitioned space on my 320Gb drive. 

"Ah" I said, "Windows 7 doesn't understand ext4, thats what it is *laugh at Windows*". So, boot into a live disc to replace GRUB, "find /boot/grub/stage1" "Error: File not found"

Then it dawned on me that what 7 reported as "Unpartitioned Space" really was unpartitioned space. Windows had just wiped my Linux install. 

Is this a method placed by Windows to attempt to wipe out the opposition? :lolflag:

Luckily most of my Data is either on a Fat partition on the 320Gb drive, or on my server :D Just shows the need to backup ALL THE TIME :lolflag:

---

### Post by WatchingThePain on 2009-06-19
I haven't got any Linux Horror stories.

Plenty of Windows ones but it's a Ubuntu forum.

---

### Post by anaconda on 2009-06-19
> **dragos240 said:**
> I've had too many windows horror experiences and zero linux horror stories. Too many windows ones to count.

++
Same here. My horror stories are from windows world.


One thing from linux. When I first tried linux in 1996, I couldn't even mount anything, so no cd:s disks or hd:s, and coulndt even get the internet connection working.

---

### Post by Viva on 2009-06-19
Tried to install firefox 1.5 ago, there was a dependancy problem, but I foolishly chose to install it anyway despite the warnings. Removed almost everything including apt:(

---

### Post by linuxguymarshall on 2009-06-19
Trying to get it (Linux) to work with 2 different video cards on one machine and dual-screen them, an intel integrated card and an Nvidia 6200. That was hell.

---

### Post by hanzomon4 on 2009-06-19
I can remember times when the package management system imploded. It''s like a run-away train where apt wants to remove everything including itself. Magically I got everything back with out reinstalling. This was an dist-upgrade thing

---

### Post by Hallvor on 2009-06-19
Everything that has gone wrong has been my own fault. Messing with xorg without making a backup, for instance. ;)

---

### Post by Kareeser on 2009-06-19
Too many "rm" misfires to count.

In one thankful scenario, I was setting up version control on some work that I had already spent all day on (a php frontend to a MySQL database, I code quite slowly). I was afraid I'd mess up, so I backed up the folder onto another computer just in case.

Checked out the first revision, only to realize it spawned inside another folder I meant to have the version control applied, so I deleted the empty folder that just got checked out, and went to the parent directory.

Pressed up to run the checkout command again, and deleted the real directory.

It was such a shock, since I had so accurately predicted my own stupidity.

---

### Post by calrogman on 2009-06-19
Oh **** I have 50 GB of swap space.

The moral of the story: root can be a cruel, heartless admin.

---

### Post by Philitas on 2009-06-19
After installing gentoo alongside ubuntu, I ended up spending two days trying to figure out why my ethernet card wasn't being recognized in gentoo. I completely ignored the reasonable, rational explanations and spent my time trying all kinds of overly technical fixes. After taking a break from it, I came back to find, but of course, that my ethernet card was not, as I had thought, listed under the 10/100 section of the kernel configuration, but the gigabit. A make && make modules_install later, I was kicking myself for missing something so stupid. So that was my linux-induced blond moment.

---

### Post by Stitz on 2009-06-19
I have been saving lots of important files on a memory stick for several months now...it always goes everywhere I go, in case I need it.  Today I was installing Fedora 11 on a new computer and while it was in "live" mode, I used my memory stick to test a package that I had saved on it a few days earlier.  Anyway, when I went to install Fedora, I forgot about the memory stick and ended up wiping it out completely.  It's not only empty, but it no longer has a partition on it (I yanked it out when the light started flashing, but it was too late).

---

### Post by ZackM on 2009-06-19
This isn't really a "horror" story, but funny and involves Linux. 

I was in college and we went to another room to work on some old desktops that were in there. There were HPs, Dells, Compaqs(Pre-HP buyout) and others. It was pretty fun though to get all these old systems hooked up and seeing what was on them. The systems ranged from 98, to XP. This is where Linux came in. 

A kid in our class, who of which we all knew was gay, but he didn't realize we knew... That's another story, but we didn't care he was gay. He was one of those guys that thought he knew anything about everything, even getting bold enough to state he was the smartest in the class (Which was extremely false). Well, he had a computer hooked up and turned it on. A couple of friends and myself were near him at this point when "Fedora" popped up (The version has escaped me). Now, since he was the self-proclaimed brightest in the class, he tried logging in. He tried his login and password that were setup in AD for the college network (STUPID). Obviously that didn't work. So, having been able to login with his credentials, he stoodup, shook his head and claimed "It must not have a system." But with a slight lisp... You'd have to hear it.. It was pretty hilarious.

So I, having seen this, shook my head and proclaimed. "Right, no system... It just be the BIOS that's automatically running. Must be a Fedora motherboard!" Haha, a couple of my friends laughed, knowing that I was the only one in the class to have Linux experience. So I turned the machine on and tried some generic stuff, which didn't work (But I didn't expect it to). 

Some of you may not find this funny, but it may just be one of those "Had to be there" moments. But, the hilarity of the story comes with "FEDORA" popping up, and a login prompt showing. Then, five minutes later, the proclamation that there was no operating system installed. Hahahahaha

Edit: I should probably mention that we were in college for computer programming and networking. He went onto networking, whereas I went on for programming to be able to obtain a programming or networking job. So... He should have known better.

---

