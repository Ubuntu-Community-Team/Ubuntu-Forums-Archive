---
title: "wineserver: could not save registry branch to system.reg : No space left on device"
date: 2009-07-17
forum: Wine
---

### Post by the_king_of_mars on 2009-07-17
OK, im new to ubuntu, this is my first real install. completely fresh on a 500gb sata drive, simply followed the prompts from the installation cd.

I have been attempting to install a fresh world of warcraft and have been relatively unsuccessful.

Installing wine was pretty easy; however, it appears to be incorrectly configured.

Using the command line option to install nets me this error
```
wineserver: could not save registry branch to system.reg : No space left on device
```Using Gparted, my 500gig sata drive was split by the default install into a /dev/sda1 457gig partition flagged as boot. There is also an extended partition split into a /dev/sda6 ext3 section and 2 swap drives /dev/sda7 and 5.

I'm assuming that when wine is going to unpack the files, it has no idea where to place them or is attempting to place them in a drive that is too small. I haven't a clue how to check this, if im thinking of the right thing or even what it would be called.

Also, finding the install files that i have saved onto the largest drive, right clicking the Installer.exe and selecting the "Open With Wine Windows Program Loader" option nets me the standard wow installation dialogue, but I am still unable to install as the fake C: drive created by wine has no capacity. I was using the sudo natulis(i cant spell this correctly for some reason).

This may be related, earlier in the installation of ubuntu (9.04) i was promoted to update various programs that came with the fresh install, i received an error message that there was insufficient space to download all of the updates, something like 100megs worth.

---

### Post by aoanla on 2009-07-18
So, in a terminal, type

df -h

and tell us what the output is. ("df" is the command for returning the 'd'isk 'f'ree on all the filesystems currently mounted, and -h makes it give a sensible human readable format for the all the sizes).

I suspect that your problem is that you made /home a separate partition and too small - /home is where all the stuff that *you* own (as opposed to stuff that everyone can use, or stuff the system uses) goes, and as such tends to be the most filled part of the filesystem for home users.


edited with sudden realisation:
Did you actually make the 457Gig partition mount as "/boot", rather than just making it bootable? If so, then "/", which is basically "everything in the filesystem not explicitly mentioned" is in the remaining ext3 partition, which is probably pretty small, since you're dividing your remaining 40G of space between it and two swap partitions. Since /home isn't explicitly mentioned in your mount scheme, that means that /home will be amongst the things using that ext3 filesystem...

(On a side note, why two swap partitions? Ideally, you should only need one, and on modern computers with Loads of RAM, you should never really swap much anyway... more than a *couple of gig* of swap is overkill.)

Wine's "virtual C drive" is actually in the location ~/.wine/drive_c, where the ~ means "my home directory".

---

