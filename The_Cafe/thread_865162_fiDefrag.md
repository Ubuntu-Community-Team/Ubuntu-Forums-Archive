---
title: "fiDefrag"
date: 2008-07-20
forum: The Cafe
---

### Post by solarwind on 2008-07-20
**=== fiDefrag ===**
Author: solarwind
Email: [email]x.solarwind.x@gmail.com[/email]
Language: Python - Requires Python 2.4 or greater.
Dependencies:
	Libraries:
		* Standard Python libraries
		* python-psyco - Not a requirement, but greatly improves performance.

	Executables:
		* find
		* du
		* filefrag
		* rsync
		* lsof


**--- Introduction: ---**

fiDefrag is a filesystem independent file defragmenter written in Python. It is loosely based on John Dong's pyFragTools
but is cleaner, faster, more efficient and newer. The structure of the code is also easier to understand and more organized.

It can be run on any Unix-like system which meets with the above dependencies. It was originally written to minimize the
file fragmentation on JFS filesystems but can be run on ANY Unix-like system with any filesystem which meets the above
dependencies. It was tested on and works very well on JFS filesystems. It's also useful on ext2 or ext3 filesystems and even ReiserFS.

**--- Usage: ---**

* fiDefrag requires root privileges to run.

sudo python fiDefrag.py -h | -a <dir> | -d <dir> [-p <passes>]

* Run sudo fiDefrag.py for more usage information.

**--- Project: ---**

* The project is hosted at [https://launchpad.net/fidefrag](https://launchpad.net/fidefrag)
* The project is a bzr tree, so you can branch it by typing the following. This will always get the latest version.
	$ bzr branch lp:fidefrag
* The project directory is an Eclipse Pydev project, so you can use Eclipse and Pydev to edit/test the project.
* If you have any fixes/improvements for the project, please register a blueprint or a bug at the launchpad project page.
* You can also submit a patch or push your own branch and request a merge.

**--- What the output means: ---**

Here is a sample output when I defragged my .mozilla folder.

```
=== Defragmenting /home/vg/.mozilla/ - 137M - 824 Files - 5 Passes ===

=== Building File List...
=== Building Extended File Info...
        824 /     824 - 100%

--- Pass 1 / 5 ---

   0.09 MB    4 P   44.26 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    4.00 P -->    3.00 P
   0.03 MB    4 P  127.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    4.00 P -->    1.00 P. Appending to blacklist.
   0.03 MB    4 P  128.35 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    4.00 P -->    3.00 P
   0.03 MB    6 P  221.57 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    6.00 P -->    1.00 P. Appending to blacklist.
   0.09 MB    3 P   32.99 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.08 MB   11 P  129.81 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:   11.00 P -->    1.00 P. Appending to blacklist.
   0.11 MB    3 P   26.97 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    4.00 P
   0.02 MB    3 P  134.38 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.13 MB    4 P   30.71 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    4.00 P -->    3.00 P
   0.28 MB    3 P   10.67 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.08 MB    6 P   70.76 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    6.00 P -->    1.00 P. Appending to blacklist.
   0.10 MB    3 P   28.86 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.32 MB    8 P   25.01 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    8.00 P -->    1.00 P. Appending to blacklist.
   0.03 MB    3 P   99.57 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.05 MB    7 P  154.30 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    7.00 P -->    1.00 P. Appending to blacklist.
   0.02 MB    3 P  179.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
  12.11 MB   26 P    2.15 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement   26.00 P -->   27.00 P
   0.13 MB    7 P   55.88 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    7.00 P -->    3.00 P
   2.31 MB   14 P    6.07 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:   14.00 P -->    5.00 P
   0.31 MB    6 P   19.16 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    6.00 P -->    3.00 P

--- Pass 2 / 5 ---

   0.09 MB    3 P   33.19 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.03 MB    3 P   96.26 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.09 MB    3 P   32.99 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.11 MB    3 P   26.97 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    4.00 P
   0.13 MB    3 P   23.03 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.28 MB    3 P   10.67 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    4.00 P
   0.10 MB    3 P   28.86 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.03 MB    3 P   99.57 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.02 MB    3 P  179.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
  12.11 MB   26 P    2.15 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:   26.00 P -->   25.00 P
   0.13 MB    3 P   23.95 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   2.31 MB    5 P    2.17 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    5.00 P -->    7.00 P
   0.31 MB    3 P    9.58 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P

--- Pass 3 / 5 ---

   0.03 MB    3 P   96.26 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.11 MB    3 P   26.97 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.28 MB    3 P   10.67 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.10 MB    3 P   28.86 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.02 MB    3 P  179.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
  12.11 MB   25 P    2.06 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement   25.00 P -->   25.00 P
   0.13 MB    3 P   23.95 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   2.31 MB    5 P    2.17 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    5.00 P -->    5.00 P
   0.31 MB    3 P    9.58 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P

--- Pass 4 / 5 ---

  12.11 MB   25 P    2.06 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement   25.00 P -->   25.00 P
   0.13 MB    3 P   23.95 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   2.31 MB    5 P    2.17 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.31 MB    3 P    9.58 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.

--- Pass 5 / 5 ---

  12.11 MB   25 P    2.06 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.


=== DEFRAG OPERATION COMPLETE.

```

Let's take this line for example:
Note that the term "fragment" and "part (P)" have the same meaning as far as we're concerned and refer to the number of fragments, parts or pieces a certain file is split into.
>    0.05 MB    7 P  154.30 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
The first number shows the size of the file (0.05 MB). The second number (7 P) shows that this file has 7 fragments. The third number (154.30 P/MB) shows that this file has an average per megabyte fragmentation of 154.30 fragments per megabyte.
The line after it: > --> Improved:    7.00 P -->    3.00 P
Shows the result of the defragmentation process for that file. In this case, the file has improved from 7 fragments to 3 fragments. This is a pretty good improvement, but the program think that it can do better so it so it defragments it again on the next pass.

---

### Post by solarwind on 2008-07-20
Download fiDefrag by typing:

Install bzr:
```
sudo apt-get install bzr
```
Branch (download) fiDefrag:
```
bzr branch lp:fidefrag
```

It's that simple.

Please test and tell me how it goes. This project is pretty safe right now. I've tested it on a few systems with no problems at all.

---

### Post by articpenguin on 2008-07-20
Does this do low level operations in jfs?

---

### Post by solarwind on 2008-07-20
> **articpenguin said:**
> Does this do low level operations in jfs?

No, this one is a high level filesystem independent defragmenter. I'm collaborating with the JFS maintainers to make an offline defrag tool that works entirely on low level operations.

---

### Post by articpenguin on 2008-07-20
How many jfs devs are there? If i remember there is only one working on it part time.

---

### Post by solarwind on 2008-07-20
> **articpenguin said:**
> How many jfs devs are there? If i remember there is only one working on it part time.

Haha ;) One is better than none. There are a few, but I've been collaborating with Dave.

---

### Post by myusername on 2008-07-21
so is this stable?

---

### Post by solarwind on 2008-07-21
> **myusername said:**
> so is this stable?

It is now. I've never had a problem with it.

---

### Post by L815 on 2008-07-21
I though Linux didn't need defragging? (seriously asking)

---

### Post by myusername on 2008-07-21
no it does but most filesystems dont show the need as bad as windows. some filesystems are just cleaner

---

### Post by articpenguin on 2008-07-21
Overtime every filesystem will eventually need to be defragged. Such if the filesystem is filled up then free space becomes fragmented and all that. People saying ext3 not fragmenting need to get there facts straight.

---

### Post by solarwind on 2008-07-21
> **L815 said:**
> I though Linux didn't need defragging? (seriously asking)

Some Linux fanboys or Mac fanboys will tell you that their filesystems don't need to be defragmented. (Fanboys don't know what they're talking about.) While that may be true, that's **not to say** that filesystems don't get fragmented.

I'm pretty sure every filesystem ever created gets fragmented. It's just that Linux filesystems get much LESS fragmented than windows ones. Unless there's some super high CPU and time consuming filesystem that defragments and carefully selects file allocation as it's being used, all filesystems get fragmented.

That's why I wrote this defragger, to improve file performance and lower fragmentation. How this works is it constantly rewrites the file until it's number of fragments is below a certain threshold (below 2 pieces or 0.5 pieces/MB by default, I'll add the option to override that later). In short, it lets the filesystem arrange its files how it wants.

---

### Post by solarwind on 2008-07-22
Revision 26. Eliminated as many bugs as I could find. Very stable now.

---

### Post by solarwind on 2008-07-22
Revision 28. Faster defragging.

---

### Post by solarwind on 2008-07-23
Revision 31. Colour output! I need testers to test this and post ways to improve it. The core system is stable so no need to worry about it corrupting anything.

---

### Post by TravisNewman on 2008-07-23
This is very slick. Tested it on my /home with no issues at all, seems like less disk seeking and faster seek time, though I'm not sure how much is placebo (I haven't formatted or defragged that partition since 2004)

---

### Post by solarwind on 2008-07-23
> **panickedthumb said:**
> This is very slick. Tested it on my /home with no issues at all, seems like less disk seeking and faster seek time, though I'm not sure how much is placebo (I haven't formatted or defragged that partition since 2004)

Thanks! Did you find anything that could be improved?

---

### Post by solarwind on 2008-07-24
Revision 36 (Version 1.7 Stable) released. Full colour easy to read output. Fast defragging.

---

### Post by neoaddict on 2008-07-25
No chance of data corruption, am I right?

---

### Post by solarwind on 2008-07-25
> **neoaddict said:**
> No chance of data corruption, am I right?

I'll answer your question with another question:

No chance of getting struck by lightning, right?

What I'm saying is that nothing is guaranteed. Nothing. But I assure you that I have extensively tested it and have found no problems whatsoever. It worked very well. It's licensed under the GNU GPL v3.

---

### Post by mips on 2008-07-25
I would not mind trying this in Arch linux. Someone just tell me how.

---

### Post by solarwind on 2008-07-25
> **mips said:**
> I would not mind trying this in Arch linux. Someone just tell me how.

I *made* it in Arch Linux.

It's simple.

Install bzr:
$ pacman -S bzr

Download the latest branch directly from launchpad:
$ bzr branch lp:fidefrag

cd into the src folder in the fidefrag folder. Run as root the following:
python fidefrag.py -d /whatever/directory/you/want/to/defrag

If you'd rather analyze a directory first (do not modify any files at all), run the following as root:
python fidefrag.py -a /some/dir/you/want/to/analyze

It's that simple. Tell me how it goes. If people actually like this thing, I'll make a GUI and a .deb package for it for Ubuntu (us Arch Linux users don't need a silly package!).

---

### Post by TravisNewman on 2008-07-25
Can you actually defrag just a single folder and not a full partition? I was using /home, which gets the whole partition.

---

### Post by solarwind on 2008-07-25
> **panickedthumb said:**
> Can you actually defrag just a single folder and not a full partition? I was using /home, which gets the whole partition.

Yes, you can defrag anything. It only defrags everything under the folder, so if you specify the folder as "/" then EVERYTHING will get defragged.

That reminds me, be sure to unmount any partitions mounted under /media or /mnt that you do not want or need to defrag such as flash drives or windows partitions. I'll add that in in the next version which will ignore flash drives and windows partitions or anything under /mnt or /media altogether.

So:

You can defrag a "/" partition just the same as defragging your /home/user/Music folder just the same as defragging your /home/user/Downloads/ThePirateBay folder (oops :)).

---

### Post by mips on 2008-07-25
> **solarwind said:**
> 
python **[COLOR="Red"]fidefrag.py[/COLOR]** -d /whatever/directory/you/want/to/defrag


It's that simple. Tell me how it goes. If people actually like this thing, I'll make a GUI and a .deb package for it for Ubuntu (us Arch Linux users don't need a silly package!).

That should be fi**[COLOR="#ff0000"]D[/COLOR]**efrag.py, tried it a few times until I actually noticed the uppercase D in the src folder.

First time I ran it I got an error but that was because lsof was not installed.

You are right, it's so simple I actually made it hard for myself lol :) So far so good. I ran it on my folder I keep iso files in and it worked. I'm now running it on my 361GB xfs /home folder and it is going to take some time I think. I should have installed psyco but to late now, not sure if it is OK to interrupt with ctrl-c to install psyco and start again.

I would not mind an arch package in the community repos, no need for a gui. Have you posted this in the Arch forums?

Just one suggestion, maybe drop the capital D in fiDefrag.py as that just cause confusion in unix/linux land.

PS. I suggest people look at their Virtualbox folder as the images are *^&^%& fragmented, (17483 P).

Keep up the good work.

EDIT: Actually did not take long, was done by the time I finished this post.

---

### Post by articpenguin on 2008-07-25
Will this eventually do low level stuff in JFS or is that a seperate project with the JFS devs?

I defragged a badly fragmented ubuntu iso image (10k extents) and got defragged to around 4k extents. So it seems to me its only doing how the filesystem allocates space 4KB at a time.

---

### Post by solarwind on 2008-07-25
> **mips said:**
> That should be fi**[COLOR="#ff0000"]D[/COLOR]**efrag.py, tried it a few times until I actually noticed the uppercase D in the src folder.

First time I ran it I got an error but that was because lsof was not installed.

You are right, it's so simple I actually made it hard for myself lol :) So far so good. I ran it on my folder I keep iso files in and it worked. I'm now running it on my 361GB xfs /home folder and it is going to take some time I think. I should have installed psyco but to late now, not sure if it is OK to interrupt with ctrl-c to install psyco and start again.

I would not mind an arch package in the community repos, no need for a gui. Have you posted this in the Arch forums?

Just one suggestion, maybe drop the capital D in fiDefrag.py as that just cause confusion in unix/linux land.

PS. I suggest people look at their Virtualbox folder as the images are *^&^%& fragmented, (17483 P).

Keep up the good work.

EDIT: Actually did not take long, was done by the time I finished this post.

1. XFS comes with its own low level defrag utility called xfs_fsr. For xfs, use that. It's a lot faster and highly optimizing fo xfs. Sorry for the lower case "d".

2. You can interrupt. It's safe.

3. I'll drop the capital "D". Thanks for the suggestion.

4. I'll try to make an Arch Linux package.

5. I'll add a function to make sure everything is installed so it's less frustrating to figure out what's wrong.

---

### Post by solarwind on 2008-07-25
> **articpenguin said:**
> Will this eventually do low level stuff in JFS or is that a seperate project with the JFS devs?

I defragged a badly fragmented ubuntu iso image (10k extents) and got defragged to around 4k extents. So it seems to me its only doing how the filesystem allocates space 4KB at a time.

This will remain filesystem independent. Meanwhile, I'm working on a larger, MUCH faster and highly optimizing JFS low level defragmenter with the JFS devs. I'll keep both projects maintained. Once I get how to do JFS properly, ext3 shouldn't be too hard (there's already an ext2 defragger). xfs comes with its own defragger as well (xfs_fsr).

---

### Post by articpenguin on 2008-07-25
Ext4 has a defragger. But the devs arnt really paying much attention to it right now.

---

### Post by ferd on 2008-07-28
sudo python fiDefrag.py -h. File not found.

---

### Post by mips on 2008-07-28
> **ferd said:**
> sudo python fiDefrag.py -h. File not found.

Try:
```
sudo python fidefrag.py -h
```
as he might have changed the 'D' to a 'd'

---

### Post by ferd on 2008-07-28
> **mips said:**
> Try:
```
sudo python fidefrag.py -h
```
as he might have changed the 'D' to a 'd'

Thanks for the quick reply."No such file or directory" is the latest response to your suggestion, lower or upper case 'd.'

---

### Post by miabe on 2008-08-08
hi, your defragger sounds very promising, but unfortunately I have problems installing it on ubuntu 7.10. I get the following message:

~$ bzr branch lp:fidefrag
[http://code.launchpad.net/fidefrag/](http://code.launchpad.net/fidefrag/) is redirected to [https://code.launchpad.net/fidefrag/](https://code.launchpad.net/fidefrag/)
bzr: ERROR: Unknown branch format: 'Bazaar pack repository format 1 (needs bzr 0.92)\n'

any idea what I can do?
cheers, michael

---

### Post by solarwind on 2008-08-08
> **miabe said:**
> hi, your defragger sounds very promising, but unfortunately I have problems installing it on ubuntu 7.10. I get the following message:

~$ bzr branch lp:fidefrag
[http://code.launchpad.net/fidefrag/](http://code.launchpad.net/fidefrag/) is redirected to [https://code.launchpad.net/fidefrag/](https://code.launchpad.net/fidefrag/)
bzr: ERROR: Unknown branch format: 'Bazaar pack repository format 1 (needs bzr 0.92)\n'

any idea what I can do?
cheers, michael

Upgrade your bazaar. You have the really old version.

---

### Post by miabe on 2008-08-08
thanks!
after adding this software source
deb [http://bazaar-vcs.org/releases/debs/gutsy](http://bazaar-vcs.org/releases/debs/gutsy) ./
it worked!
great script!

---

### Post by solarwind on 2008-08-08
> **miabe said:**
> thanks!
after adding this software source
deb [http://bazaar-vcs.org/releases/debs/gutsy](http://bazaar-vcs.org/releases/debs/gutsy) ./
it worked!
great script!

Tell me how it worked, what you liked and what you disliked. I'll improve it as much as I can.

---

### Post by miabe on 2008-08-10
hi solarwind,

I tried out your script on my system now and it seems to be very stable and optimized quite some files but also leaving a lot behind. I was surprised how many fragments the ext2 filesystem produces - I thought ext2 is more efficient in this area. But the fragmentation is not very high and on my system partition the performance gain will not be noticeable anyway as it is a SSD on my eeePc ;)

I mainly want to use your script on my slow external NTSC drive which I use for video recording and conversion. These files get heavily fragmented but fiDefrag cannot clean it out so I have to go back to XP from time to time to defrag and create continuous free space on the drive. 
fiDefrag gives back these kind of log:

--- Pass 2 / 5 --- 

 329.45 MB  229 P    0.70 P/MB   /media/ICE/movies/rec.mpg 
        --> No improvement:  229.00 P --> 1582.00 P 

--- Pass 3 / 5 --- 

 329.45 MB  229 P    0.70 P/MB   /media/ICE/movies/rec.mpg 
        --> Too many consecutive no-improvements. Appending to blacklist. 

--

The drive has 50% free space (40GB) and the file sizes are between 300 and 3000MB. The windows defragger has no problems with it.
Is there a way to make your script work on the files till they are completely defragmented and also optimize the free space area on the drive?

---

### Post by furialis on 2008-08-10
Thanks for the great app solarwind, works great!

---

### Post by solarwind on 2008-08-10
> **miabe said:**
> hi solarwind,

I tried out your script on my system now and it seems to be very stable and optimized quite some files but also leaving a lot behind. I was surprised how many fragments the ext2 filesystem produces - I thought ext2 is more efficient in this area. But the fragmentation is not very high and on my system partition the performance gain will not be noticeable anyway as it is a SSD on my eeePc ;)

I mainly want to use your script on my slow external NTSC drive which I use for video recording and conversion. These files get heavily fragmented but fiDefrag cannot clean it out so I have to go back to XP from time to time to defrag and create continuous free space on the drive. 
fiDefrag gives back these kind of log:

--- Pass 2 / 5 --- 

 329.45 MB  229 P    0.70 P/MB   /media/ICE/movies/rec.mpg 
        --> No improvement:  229.00 P --> 1582.00 P 

--- Pass 3 / 5 --- 

 329.45 MB  229 P    0.70 P/MB   /media/ICE/movies/rec.mpg 
        --> Too many consecutive no-improvements. Appending to blacklist. 

--

The drive has 50% free space (40GB) and the file sizes are between 300 and 3000MB. The windows defragger has no problems with it.
Is there a way to make your script work on the files till they are completely defragmented and also optimize the free space area on the drive?

I'll do my best to fix it. What is NTSC?

---

### Post by miabe on 2008-08-10
ups, hehe I should switch on my brain before typing a post. Its a NTFS formated drive! but my digicam NTSC movies make also always problems when converting to PAL so thats probably why it popped into my mind...

---

### Post by ThrobbingBrain66 on 2008-08-10
Thanks for this defrag tool.  It's worked wonders for me.

I think I've found a small bug, however.

I was just beginning to defrag my /home folder when your program errored out on me.  I had Firefox open while fiDefrag built the file list. But while fiDefrag was building the extended info, I closed Firefox.  Apparently, this removes a file called 'sessionstore.js' from the .mozilla folder.  Having that file in the file list but not being able to get extended info on it made fiDefrag spit the following error:
```

Traceback (most recent call last):
  File "fiDefrag.py", line 259, in <module>
    mfiles.append(mfile(f))
  File "fiDefrag.py", line 198, in __init__
    self.size = filesize(file)
  File "fiDefrag.py", line 56, in filesize
    return os.path.getsize(file)
  File "/usr/lib/python2.5/posixpath.py", line 139, in getsize
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/home/username/.mozilla/firefox/tvgesguh.default/sessionstore.js'
```

EDIT:  I reported this bug on Launchpad as well.

---

### Post by solarwind on 2008-08-10
> **miabe said:**
> ups, hehe I should switch on my brain before typing a post. Its a NTFS formated drive! but my digicam NTSC movies make also always problems when converting to PAL so thats probably why it popped into my mind...

Do you have windows installed? Or did you just decide to format one of your partitions as NTFS?

---

### Post by miabe on 2008-08-10
I have windows running on an other computer but the drive I am talking abut is an external one which I use as well under xubuntu on my eeepc for video recording and editing.

---

### Post by solarwind on 2008-08-10
> **miabe said:**
> I have windows running on an other computer but the drive I am talking abut is an external one which I use as well under xubuntu on my eeepc for video recording and editing.

For NTFS defragging, I recommend you use ultimate defrag 2008 which is a windows program. It's a pay-for app but email me and I'll hook you up ;)

---

### Post by miabe on 2008-08-11
thanks, but on windows I don't need any other defrag software. the default XP  defrag does a very good job! but it would be great to have a similar tool in ubuntu :)

---

### Post by solarwind on 2008-08-11
> **miabe said:**
> thanks, but on windows I don't need any other defrag software. the default XP  defrag does a very good job! but it would be great to have a similar tool in ubuntu :)

Problem is, winbloze uses only two filesystems (FAT and NTFS). On Linux, there are *many*.

---

### Post by solarwind on 2008-08-17
Bug fixed. Update your download with:

```
bzr branch lp:fidefrag
```

---

### Post by solarwind on 2008-08-17
> **ThrobbingBrain66 said:**
> Thanks for this defrag tool.  It's worked wonders for me.

I think I've found a small bug, however.

I was just beginning to defrag my /home folder when your program errored out on me.  I had Firefox open while fiDefrag built the file list. But while fiDefrag was building the extended info, I closed Firefox.  Apparently, this removes a file called 'sessionstore.js' from the .mozilla folder.  Having that file in the file list but not being able to get extended info on it made fiDefrag spit the following error:
```

Traceback (most recent call last):
  File "fiDefrag.py", line 259, in <module>
    mfiles.append(mfile(f))
  File "fiDefrag.py", line 198, in __init__
    self.size = filesize(file)
  File "fiDefrag.py", line 56, in filesize
    return os.path.getsize(file)
  File "/usr/lib/python2.5/posixpath.py", line 139, in getsize
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/home/username/.mozilla/firefox/tvgesguh.default/sessionstore.js'
```

EDIT:  I reported this bug on Launchpad as well.

Thanks for reporting, fixed.

---

### Post by Twitch6000 on 2008-08-17
I vote for this to go in ubuntu 8.10 :).

---

### Post by solarwind on 2008-08-17
> **Twitch6000 said:**
> I vote for this to go in ubuntu 8.10 :).

Haha, thanks! There's still a lot to fix and improve though; so any bug reports, feature requests and so on will be appreciated. I'm going to make a GUI for this soon.

---

### Post by psusi on 2008-08-17
> **miabe said:**
> thanks, but on windows I don't need any other defrag software. the default XP  defrag does a very good job! but it would be great to have a similar tool in ubuntu :)

If you are using ext2/3 you can boot from the livecd ( can't run on mounted partitions ) and install the defrag package in the universe repository and run e2defrag on your hard disk partition(s).  It's command line and uses an ASCII gui, but it gets the job done.  You can even tell it to place specific files in order at the start of the drive.

---

### Post by solarwind on 2008-08-18
> **psusi said:**
> If you are using ext2/3 you can boot from the livecd ( can't run on mounted partitions ) and install the defrag package in the universe repository and run e2defrag on your hard disk partition(s).  It's command line and uses an ASCII gui, but it gets the job done.  You can even tell it to place specific files in order at the start of the drive.

But I think you'll need to downgrade to ext2 first (if you're using ext3) to use e2defrag.

---

### Post by theglu on 2008-08-21
It's works perfectly for me (I have a vmware fragmented file and I can restore my virtual machine in 15s and not in 4 minutes °o°)

And if you made it on Archlinux it's better ;)

I found some bugs, I will send you a patch with fix asap !

---

### Post by solarwind on 2008-08-21
> **theglu said:**
> It's works perfectly for me (I have a vmware fragmented file and I can restore my virtual machine in 15s and not in 4 minutes °o°)

And if you made it on Archlinux it's better ;)

I found some bugs, I will send you a patch with fix asap !

I did make it on Arch Linux. That's the *only *distribution I use (other than a custom one I made from scratch for my PC104 board).

---

### Post by theglu on 2008-08-21
> **solarwind said:**
> I did make it on Arch Linux. That's the *only *distribution I use (other than a custom one I made from scratch for my PC104 board).

Me too, but shhhhh, we're on ubuntu forums ;)

---

### Post by Skorzen on 2008-08-21
I'll give it a try.

Thanks for the project.

---

### Post by gorn on 2008-09-07
For the ArchLinux users I've made a PKGBUILD to install this. It's for the BZR version, perhaps one should be made for a stable version too. I've submitted to AUR, but solarwind, I'd be happy to turn the AUR over to you if you want it.

[http://aur.archlinux.org/packages.php?ID=19786](http://aur.archlinux.org/packages.php?ID=19786)

If you have yaourt install, you can install fidefrag simply with:
yaourt -S fidefrag-bzr

Then just run fidefrag -d /path/you/want/to/defrag


(Without yaourt you can download the tar and extract it, then run makepkg, then run pacman -U fidefrag-bzr-1.tar.gz to install)

---

### Post by solarwind on 2008-09-07
> **gorn said:**
> For the ArchLinux users I've made a PKGBUILD to install this. It's for the BZR version, perhaps one should be made for a stable version too. I've submitted to AUR, but solarwind, I'd be happy to turn the AUR over to you if you want it.

[http://aur.archlinux.org/packages.php?ID=19786](http://aur.archlinux.org/packages.php?ID=19786)

If you have yaourt install, you can install fidefrag simply with:
yaourt -S fidefrag-bzr

Then just run fidefrag -d /path/you/want/to/defrag


(Without yaourt you can download the tar and extract it, then run makepkg, then run pacman -U fidefrag-bzr-1.tar.gz to install)
Excellent! I think you should be in charge of the AUR thing. I know nothing of managing PKGBUILDS (yet) and I'm sure you're much better at managing packages than I am :P I'll create a stable branch and let you know when updates are pushed.

---

### Post by kyfho23 on 2008-09-10
I must be missing a step...I keep getting [Errno 2] No such file or directory OR sudo: fidefrag.py: command not found error messages whenever I try to run fidefrag.py

I tried re-checking out the file and got:  bzr branch lp:fidefrag
bzr: ERROR: Target directory "fidefrag" already exists.

What am I doing wrong? 
 
BTW...this was with both the D capitalized & not, and yes, I install bzr first.

Thanks!

---

### Post by solarwind on 2008-09-10
> **kyfho23 said:**
> I must be missing a step...I keep getting [Errno 2] No such file or directory OR sudo: fidefrag.py: command not found error messages whenever I try to run fidefrag.py

I tried re-checking out the file and got:  bzr branch lp:fidefrag
bzr: ERROR: Target directory "fidefrag" already exists.

What am I doing wrong? 
 
BTW...this was with both the D capitalized & not, and yes, I install bzr first.

Thanks!

1. Delete your fidefrag directory
2. bzr branch lp:fidefrag
3. cd fidefrag
4. cd src
5. ls *.py
6. In the list make sure you see a python file.
7. sudo ./fidefrag.py <appropriate options>

---

### Post by kyfho23 on 2008-09-10
That worked. Thanks
& BTW...there is no 64-bit version of psyco. fiDefrag works fine without it, but the documentation in the source code for psyco says there is none and none is planned. Just thought I'd mention this for any other amd64 users who happen on this. Solarwind, the documentation did mention something called pypy...maybe something to consider changing?

Thanks again

---

### Post by solarwind on 2008-09-10
> **kyfho23 said:**
> That worked. Thanks
& BTW...there is no 64-bit version of psyco. fiDefrag works fine without it, but the documentation in the source code for psyco says there is none and none is planned. Just thought I'd mention this for any other amd64 users who happen on this. Solarwind, the documentation did mention something called pypy...maybe something to consider changing?

Thanks again

I'll look into it, thanks.

[http://codespeak.net/pypy/dist/pypy/doc/home.html](http://codespeak.net/pypy/dist/pypy/doc/home.html)

---

### Post by linuxology on 2008-09-14
I am a basic linux user and been using Ubuntu for ~6 months and have everything like I want it.  Can you lead me to the directories I mainly want to defrag?  I do not want to break anything.  Thanks.

---

### Post by solarwind on 2008-09-14
> **linuxology said:**
> I am a basic linux user and been using Ubuntu for ~6 months and have everything like I want it.  Can you lead me to the directories I mainly want to defrag?  I do not want to break anything.  Thanks.

Only two I can think of is /home and /usr. Other stuff shouldn't be fragmented since it doesn't get written to all that much.

---

### Post by mahuyar on 2008-09-17
Does the following mean that the folder "songs" is defragmented?  That's the result I got from the first time running didefrag on that folder.  I was expecting a bit more output.

```

mahuyar@theater:/media/space$ sudo python fidefrag.py -d /media/space/.d_drive/media/songs
 
=== Defragmenting /media/space/.d_drive/media/songs - 20G - 3727 Files - 5 Passes ===

=== Building File List...
=== Building Extended File Info...


--- Pass 1 / 5 ---


--- Pass 2 / 5 ---


--- Pass 3 / 5 ---


--- Pass 4 / 5 ---


--- Pass 5 / 5 ---



=== DEFRAG OPERATION COMPLETE.

```

---

### Post by solarwind on 2008-09-17
> **mahuyar said:**
> Does the following mean that the folder "songs" is defragmented?  That's the result I got from the first time running didefrag on that folder.  I was expecting a bit more output.

```

mahuyar@theater:/media/space$ sudo python fidefrag.py -d /media/space/.d_drive/media/songs
 
=== Defragmenting /media/space/.d_drive/media/songs - 20G - 3727 Files - 5 Passes ===

=== Building File List...
=== Building Extended File Info...


--- Pass 1 / 5 ---


--- Pass 2 / 5 ---


--- Pass 3 / 5 ---


--- Pass 4 / 5 ---


--- Pass 5 / 5 ---



=== DEFRAG OPERATION COMPLETE.

```

Yep. The program considers that to be defragmented. Of course, it doesn't mean that every single file is in one piece, it just means that there is no significant fragmentation that would improve by forcing the process. You can run "sudo filefrag <some file>" to see how many fragments it has.

The defragmenter has built in thresholds. Look in the source code to see the thresholds.

---

### Post by Pro-reason on 2008-09-21
> **psusi said:**
> If you are using ext2/3 you can boot from the livecd ( can't run on mounted partitions ) and install the defrag package in the universe repository and run e2defrag on your hard disk partition(s).  It's command line and uses an ASCII gui, but it gets the job done.  You can even tell it to place specific files in order at the start of the drive.

Never tell people to run e2defrag on ext3.  I did it once and lost everything.

---

### Post by solarwind on 2008-09-21
Which reminds me,

I've been working on this app quite a bit lately (behind the scenes). Although I haven't been pushing updates to the bzr repository, I've been working on these things:

* Restructure application into a library and a (text mode) frontend to improve program structure, speed and let others build on the system. - **Done.**
* Improve reliability by preserving all file permissions and md5 sums (will use sfv crc32 later on for speed) into a database and checking to make sure everything's the way it was after operation is complete. If something goes wrong, it will handle the situation appropriately. This can be forced off to improve speed. - **Almost Done.**
* GUI - **Haven't Started.** If someone can design a nice GUI shell in pyGTK using GLADE and send me the GLADE files and any other relevant files, I would greatly appreciate it.

---

### Post by Pro-reason on 2008-09-22
Someone on Launchpad PPAs has [packaged]("https://launchpad.net/ubuntu/+ppas?name_filter=fidefrag") this software.  You can install it via Synaptic instead of using bzr.

---

### Post by vikrant82 on 2008-09-22
I saw some logs like these :

```
No improvement after defrag:   601.00 P -->   1101.00 P
```

There are lots of logs like those. So, does that means that it increased the number of fragments for that file from 601 to 1101 or was that just a read only test.

Also would love to know, what's the basic principle you follow, for defragmenting files.

---

### Post by solarwind on 2008-09-22
> **vikrant82 said:**
> I saw some logs like these :

```
No improvement after defrag:   601.00 P -->   1101.00 P
```

There are lots of logs like those. So, does that means that it increased the number of fragments for that file from 601 to 1101 or was that just a read only test.

Also would love to know, what's the basic principle you follow, for defragmenting files.

No improvement after defrag means that the system increased the number of fragments. All fidefrag does is copy files. Everything is done on the high level. So the operating system did that. The same would have happened if you had manually copied the file. You can run another pass on it and see if it improves anything.

---

### Post by solarwind on 2008-09-23
Version 2.10 pushed. Includes a lot of improvements and regex excluding! Cleaned up source and improved efficiency. Now starts defragging immediately without "analyzing" first.

---

### Post by Pro-reason on 2008-09-23
> **solarwind said:**
> Version 2.10 pushed. Includes a lot of improvements and regex excluding! Cleaned up source and improved efficiency. Now starts defragging immediately without "analyzing" first.
Version 2.10 is broken.

```

Traceback (most recent call last):
  File "./fidefrag.py", line 4, in <module>
    import libfidefrag, config
  File "~/fidefrag/fidefrag/src/libfidefrag.py", line 2, in <module>
    import config
ImportError: No module named config

```

---

### Post by solarwind on 2008-09-23
> **Pro-reason said:**
> Version 2.10 is broken.

```

Traceback (most recent call last):
  File "./fidefrag.py", line 4, in <module>
    import libfidefrag, config
  File "~/fidefrag/fidefrag/src/libfidefrag.py", line 2, in <module>
    import config
ImportError: No module named config

```

Oops! Forgot to add the config file during push process. Check it out now and it will work. Sorry for that.

---

### Post by SomeGuyDude on 2008-09-23
Teehee. "John Dong".

---

### Post by solarwind on 2008-09-23
> **SomeGuyDude said:**
> Teehee. "John Dong".

Lol, yeah, that's JDong...

---

### Post by lisati on 2008-09-23
Based on the posts I've read, this project looks promising, a potentially useful addition to the repetoire of disk management tools available.

<off topic>
> **miabe said:**
> ups, hehe I should switch on my brain before typing a post. Its a NTFS formated drive! but my digicam NTSC movies make also always problems when converting to PAL so thats probably why it popped into my mind...
I once read that "NTSC" means "**n**ever **t**wice the **s**ame **c**olour" and "PAL" means "**p**retty **a**wful **l**ook".
The three tape-based camcorders I have record in PAL (the main TV system used here in NZ) and the newest (a HDD beast) records in NTSC. Odd, since all were purchased here in NZ.

</off topic>

---

### Post by solarwind on 2008-09-23
There was another little bug. Fixed it, runs perfectly now.

---

### Post by EmoDx on 2008-09-24
Can you please post the exact command I'll need to defrag my entire file system. <I'll cut and paste> I have tried several times but I guess I am not up to par on my geek speak.

- Emo

> **solarwind said:**
> **=== fiDefrag ===**
Author: solarwind
Email: [email]x.solarwind.x@gmail.com[/email]
Language: Python - Requires Python 2.4 or greater.
Dependencies:
	Libraries:
		* Standard Python libraries
		* python-psyco - Not a requirement, but greatly improves performance.

	Executables:
		* find
		* du
		* filefrag
		* rsync
		* lsof


**--- Introduction: ---**

fiDefrag is a filesystem independent file defragmenter written in Python. It is loosely based on John Dong's pyFragTools
but is cleaner, faster, more efficient and newer. The structure of the code is also easier to understand and more organized.

It can be run on any Unix-like system which meets with the above dependencies. It was originally written to minimize the
file fragmentation on JFS filesystems but can be run on ANY Unix-like system with any filesystem which meets the above
dependencies. It was tested on and works very well on JFS filesystems. It's also useful on ext2 or ext3 filesystems and even ReiserFS.

**--- Usage: ---**

* fiDefrag requires root privileges to run.

sudo python fiDefrag.py -h | -a <dir> | -d <dir> [-p <passes>]

* Run sudo fiDefrag.py for more usage information.

**--- Project: ---**

* The project is hosted at [https://launchpad.net/fidefrag](https://launchpad.net/fidefrag)
* The project is a bzr tree, so you can branch it by typing the following. This will always get the latest version.
	$ bzr branch lp:fidefrag
* The project directory is an Eclipse Pydev project, so you can use Eclipse and Pydev to edit/test the project.
* If you have any fixes/improvements for the project, please register a blueprint or a bug at the launchpad project page.
* You can also submit a patch or push your own branch and request a merge.

**--- What the output means: ---**

Here is a sample output when I defragged my .mozilla folder.

```
=== Defragmenting /home/vg/.mozilla/ - 137M - 824 Files - 5 Passes ===

=== Building File List...
=== Building Extended File Info...
        824 /     824 - 100%

--- Pass 1 / 5 ---

   0.09 MB    4 P   44.26 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    4.00 P -->    3.00 P
   0.03 MB    4 P  127.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    4.00 P -->    1.00 P. Appending to blacklist.
   0.03 MB    4 P  128.35 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    4.00 P -->    3.00 P
   0.03 MB    6 P  221.57 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    6.00 P -->    1.00 P. Appending to blacklist.
   0.09 MB    3 P   32.99 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.08 MB   11 P  129.81 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:   11.00 P -->    1.00 P. Appending to blacklist.
   0.11 MB    3 P   26.97 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    4.00 P
   0.02 MB    3 P  134.38 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.13 MB    4 P   30.71 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    4.00 P -->    3.00 P
   0.28 MB    3 P   10.67 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.08 MB    6 P   70.76 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    6.00 P -->    1.00 P. Appending to blacklist.
   0.10 MB    3 P   28.86 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.32 MB    8 P   25.01 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    8.00 P -->    1.00 P. Appending to blacklist.
   0.03 MB    3 P   99.57 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.05 MB    7 P  154.30 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    7.00 P -->    1.00 P. Appending to blacklist.
   0.02 MB    3 P  179.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
  12.11 MB   26 P    2.15 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement   26.00 P -->   27.00 P
   0.13 MB    7 P   55.88 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    7.00 P -->    3.00 P
   2.31 MB   14 P    6.07 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:   14.00 P -->    5.00 P
   0.31 MB    6 P   19.16 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:    6.00 P -->    3.00 P

--- Pass 2 / 5 ---

   0.09 MB    3 P   33.19 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.03 MB    3 P   96.26 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.09 MB    3 P   32.99 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.11 MB    3 P   26.97 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    4.00 P
   0.13 MB    3 P   23.03 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.28 MB    3 P   10.67 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    4.00 P
   0.10 MB    3 P   28.86 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   0.03 MB    3 P   99.57 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.02 MB    3 P  179.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
  12.11 MB   26 P    2.15 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Improved:   26.00 P -->   25.00 P
   0.13 MB    3 P   23.95 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   2.31 MB    5 P    2.17 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    5.00 P -->    7.00 P
   0.31 MB    3 P    9.58 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P

--- Pass 3 / 5 ---

   0.03 MB    3 P   96.26 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Fully defragmented:    3.00 P -->    1.00 P. Appending to blacklist.
   0.11 MB    3 P   26.97 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.28 MB    3 P   10.67 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.10 MB    3 P   28.86 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.02 MB    3 P  179.22 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
  12.11 MB   25 P    2.06 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement   25.00 P -->   25.00 P
   0.13 MB    3 P   23.95 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P
   2.31 MB    5 P    2.17 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    5.00 P -->    5.00 P
   0.31 MB    3 P    9.58 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement    3.00 P -->    3.00 P

--- Pass 4 / 5 ---

  12.11 MB   25 P    2.06 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> No improvement   25.00 P -->   25.00 P
   0.13 MB    3 P   23.95 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   2.31 MB    5 P    2.17 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.
   0.31 MB    3 P    9.58 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.

--- Pass 5 / 5 ---

  12.11 MB   25 P    2.06 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
	--> Too many consecutive no-improvements. Appending to blacklist.


=== DEFRAG OPERATION COMPLETE.

```

Let's take this line for example:
Note that the term "fragment" and "part (P)" have the same meaning as far as we're concerned and refer to the number of fragments, parts or pieces a certain file is split into.

The first number shows the size of the file (0.05 MB). The second number (7 P) shows that this file has 7 fragments. The third number (154.30 P/MB) shows that this file has an average per megabyte fragmentation of 154.30 fragments per megabyte.
The line after it: 
Shows the result of the defragmentation process for that file. In this case, the file has improved from 7 fragments to 3 fragments. This is a pretty good improvement, but the program think that it can do better so it so it defragments it again on the next pass.

---

### Post by Pro-reason on 2008-09-24
> **EmoDx said:**
> Can you please post the exact command I'll need to defrag my entire file system. <I'll cut and paste> I have tried several times but I guess I am not up to par on my geek speak.

- Emo

Your whole system is “/”, so to defragment it all, you just need to do:
```

fidefrag -d /

```

Install the version from the [PPA]("https://launchpad.net/~chameleondave/+archive"), and you can then get documentation by typing “man fidefrag”.

---

### Post by solarwind on 2008-09-24
1. type *bzr branch lp:fidefrag fidefrag211*
2. type *cd fidefrag211/src*
3. type *sudo ./fidefrag.py -d /home* - This will defrag your home directory. If you feel like it do:
4. *sudo ./fidefrag.py -d /usr*
5. *sudo ./fidefrag.py -d /lib*
6. *sudo ./fidefrag.py -d /opt*

---

### Post by solarwind on 2008-09-24
> **Pro-reason said:**
> Your whole system is “/”, so to defragment it all, you just need to do:
```

fidefrag -d /

```

Install the version from the [PPA]("https://launchpad.net/~chameleondave/+archive"), and you can then get documentation by typing “man fidefrag”.
I updated it to version 2.11 a few hours ago. Version 2.10 had a few bugs. Which one does your package have? Also, how hard is it to maintain a debian package?

---

### Post by solarwind on 2008-09-28
If people request any new features or report any bugs, I'd be happy to start fixing bugs and adding features! Just post!

---

### Post by NullHead on 2008-10-08
A GUI would be nice. I'll test this on my laptop in a bit and post back.

---

### Post by WattoDaToydarian on 2008-10-13
I am trying this out on my server running Ubuntu-server 8.04 with an EXT3 file system.
This is the output that I get:
```
sudo python fidefrag.py -d /home/watto

=== Defragmenting /home/watto - 296M - 379 Files - 5 Passes ===

=== Building File List...

--- Pass 1 / 5 ---


--- Pass 2 / 5 ---


--- Pass 3 / 5 ---


--- Pass 4 / 5 ---


--- Pass 5 / 5 ---



=== DEFRAG OPERATION COMPLETE.

```
For some reason I am not seeing the lines that look like this:> 0.09 MB    4 P   44.26 P/MB 	 /home/vg/.mozilla/firefox/tfmpeoug.defau...
Is it working and there just isn't any fragments or something?
One thing that I notice is right after it displays "--- Pass 1 / 5 ---" it stops for about 10sec and then displays all the other lines of text instantly.

---

### Post by treesurf on 2008-10-14
Great little app.  Thank you.  It should be in the main repos.

---

### Post by solarwind on 2008-10-14
> **WattoDaToydarian said:**
> I am trying this out on my server running Ubuntu-server 8.04 with an EXT3 file system.
This is the output that I get:
```
sudo python fidefrag.py -d /home/watto

=== Defragmenting /home/watto - 296M - 379 Files - 5 Passes ===

=== Building File List...

--- Pass 1 / 5 ---


--- Pass 2 / 5 ---


--- Pass 3 / 5 ---


--- Pass 4 / 5 ---


--- Pass 5 / 5 ---



=== DEFRAG OPERATION COMPLETE.

```
For some reason I am not seeing the lines that look like this:
Is it working and there just isn't any fragments or something?
One thing that I notice is right after it displays "--- Pass 1 / 5 ---" it stops for about 10sec and then displays all the other lines of text instantly.

Yeah, that's fine. It means that your files are not fragmented.

---

### Post by Pro-reason on 2008-10-14
> **solarwind said:**
> Yeah, that's fine. It means that your files are not fragmented.

It should make that clear then.

---

### Post by solarwind on 2008-10-14
> **Pro-reason said:**
> It should make that clear then.

I'm on it.

---

### Post by mkalen on 2008-10-15
Works fine on my ext3 and reiserfs partitions, thanks!

An idea for improvement: use the available console width instead of a fixed width format. I am testing fiDefrag in a console window with 138 columns but get output chopped at 86 columns.

Using the full console width would make it easier to determine the filenames when defragmenting directory trees with many files using similar names (eg: which one of x...y.tgz or x...y.tgz is x-1.0-y.tgz and which one is x-2.0-y.tgz?).

---

### Post by solarwind on 2008-10-15
> **mkalen said:**
> Works fine on my ext3 and reiserfs partitions, thanks!

An idea for improvement: use the available console width instead of a fixed width format. I am testing fiDefrag in a console window with 138 columns but get output chopped at 86 columns.

Using the full console width would make it easier to determine the filenames when defragmenting directory trees with many files using similar names (eg: which one of x...y.tgz or x...y.tgz is x-1.0-y.tgz and which one is x-2.0-y.tgz?).

Thaks for the suggestion! I'll fix it this weekend. Hmmm, I need a way to keep track of all of these ideas...

---

### Post by NullHead on 2008-10-15
You could try to get something like the ubuntubrianstorm, or you could just put 'em all into a open office document.

---

### Post by solarwind on 2008-10-15
> **NullHead said:**
> You could try to get something like the ubuntubrianstorm, or you could just put 'em all into a open office document.

Launchpad blueprints is the best, but it requires people to sign up for a launchpad account (not a bad idea to do so anyway).

---

### Post by JohnFH on 2008-10-16
It works for me, except that python-psyco package isn't available in the repository (I'm running 64bit).  :(

---

### Post by kat_ams on 2009-01-01
I found a bug.

When I try to defrag my home folder. But fidefrag is installed in my home folder... the program hangs.
I can defrag a specific folder in my home folder as long as the recursive path does not contain the fidefrag.py file.

so:
with fidefrag.py located in /home/kat/fidefrag/src/fidefrag.py

kat@leon:~/fidefrag/src$ ```
sudo ./fidefrag.py -a /home/kat
```

is broken. When I interrupt with CTRL+C

```
Traceback (most recent call last):
  File "./fidefrag.py", line 54, in <module>
    libfidefrag.analyze_op()
  File "/home/kat/fidefrag/src/libfidefrag.py", line 204, in analyze_op
    file_count = filecount(operation_dir) #Get number of files.
  File "/home/kat/fidefrag/src/libfidefrag.py", line 62, in filecount
    filecount = os.popen("/usr/bin/find \"" + dir + "\" -xdev -type f 2> /dev/null | wc -l").read()
KeyboardInterrupt
```

if I defrag a single folder

kat@leon:~/fidefrag/src$ ```
sudo ./fidefrag.py -a /home/kat/buddha
```

the folder defrags as normal.

---

### Post by solarwind on 2009-01-01
> **kat_ams said:**
> I found a bug.

When I try to defrag my home folder. But fidefrag is installed in my home folder... the program hangs.
I can defrag a specific folder in my home folder as long as the recursive path does not contain the fidefrag.py file.

so:
with fidefrag.py located in /home/kat/fidefrag/src/fidefrag.py

kat@leon:~/fidefrag/src$ ```
sudo ./fidefrag.py -a /home/kat
```

is broken. When I interrupt with CTRL+C

```
Traceback (most recent call last):
  File "./fidefrag.py", line 54, in <module>
    libfidefrag.analyze_op()
  File "/home/kat/fidefrag/src/libfidefrag.py", line 204, in analyze_op
    file_count = filecount(operation_dir) #Get number of files.
  File "/home/kat/fidefrag/src/libfidefrag.py", line 62, in filecount
    filecount = os.popen("/usr/bin/find \"" + dir + "\" -xdev -type f 2> /dev/null | wc -l").read()
KeyboardInterrupt
```

if I defrag a single folder

kat@leon:~/fidefrag/src$ ```
sudo ./fidefrag.py -a /home/kat/buddha
```

the folder defrags as normal.

Thanks for reporting the bug. I've been a bit busy lately with school and all so I didn't have time to fix the bug.

---

### Post by jrusso2 on 2009-01-01
Everytime I make the point that all filesystems need defrag some just need it more often then others I am flamed into submission here.  Now everyone is saying what I have been saying all along.

---

### Post by kat_ams on 2009-01-02
> **solarwind said:**
> Thanks for reporting the bug. I've been a bit busy lately with school and all so I didn't have time to fix the bug.

I did another test and discovered that the program was not actually hanging but taking an extremly long time to report any activity. After about 10 mintues it gave it's first report of === Defragmenting

My home filesystem is 2.6 GB in size and this only happend with /home/kat

All the other file systems including /opt which is larger at 2.8 GB started defragmenting right away.

---

### Post by ubulette on 2009-12-20
Gave fiDefrag a try yesterday, i initially thought it will be good for me, it turned out it's even worse than without it. Let me explain.

When i 1st tried fiDefrag, it was on a few directories that i knew were heavily fragmented. I let it run on a few GB of my main HD for ~1h, fiDefrag was able regain some extents, and e2freefrag showed an improvement regarding free-space fragmentation. So far, so good. So i decided to let it run on / for the night.

"/" is obviously not a good idea when you have multiple disks (like i do). fiDefrag starts with "du -sh /" (which spans all mounted disks) then "find / -xdev" (which stays on the root disk) - both commands take a really long time - and the work is then done in "/.defgrag", which will be of no good for files in other disks (or partitions)

I let the thing run for ~11h, with absolutely no idea of where it was the next day, i guess probably still somewhere in the 1st pass (this system has ~1TB used, and a few millions files).

a progress bar of some kind would be nice, along with a summary of the gain/losses. The truncated files names are useless when you have a lot of files. (not to mention the bug with short names)

Attached a graph showing the results of e2freefrag for sda1. It's a 300GB ext2 partition, and it had ~9GB free.

In blue, that was before. ~25% of the free blocks were about 4~8MB. After 1h (in orange), this improved a bit. The line moved to the right, meaning less fragmentation of free space, which is good for the other files to come (either new ones or the next ones to be "defragmented"). I expected a longer run on more files would give me a line even further to the right... but, in yellow, that's what i got: much further to the left.
The bigger (free) blocks are all gone, and i have a lot more smaller free blocks, that means more fragmentation for the next files.
And indeed, fiDefrag was mostly showing "No improvement" messages when i interrupted it, with figures like nP -> 20nP or even 100np, showing the system was doing badly.
Worse, my nice 9GB free were down to 3.5GB free, and Gnome showed some popups during those 11h saying less that 1GB free on sda1. So i've lost 5~6GB in the process and went dangerously low during the night.

by trying to optimize files one by one, fiDefrag ends up degrading the filesystem organization. My guess is that results may vary from disk to disk depending of how full they are and how fragmented the free space is.
What i would need is a lower level defrag, which has an idea of where the extents of each file and the holes are, then play smartly with sparse files to maximize the free blocks.

I'm not sure fiDefrag could do anything here.

---

