---
title: "/etc/fstab and its zero-tolerance to parsing errors"
date: 2015-06-04
forum: Ubuntu, Linux and OS Chat
---

### Post by syntaxerror74 on 2015-06-04
Hi everybody, I just couldn't really believe that /etc/fstab had ever been *that* intolerant to parsing errors in Linux 2.x times.
OK, there *were* warnings now and then, but the system would NEVER stop starting up. However, now as the finalization of Linux 4 is knocking on the door, things have really gotten rough.

Imagine an ordinary /etc/fstab like this:

```

UUID=...               /boot    ext4  rw  0  1
UUID=...                none     swap  sw,pri=8  0  0
UUID=...               /usr     ext4 defaults 0 2 
UUID=                  /        ext4  defaults 0  2
UUID=...               /home    ext4  defaults 0  2
UUID=...               /opt     ext4  defaults           0  2

```

Now deliberately (preferably in a VM) try to mess up the /etc/fstab by simply typing some garbage line, e. g. *asdfasdfasdfasdf* right in the line under the /opt mount.
_Ubuntu WILL NO LONGER BOOT_. This is a fact.
It will hang forever at the (in)famous message **Stopping initial device creation...** (well, at least here it will)

What do you think?
Does this really have to be that ONE erroneous line in /etc/fstab can really inhibit the boot process from completing?
I think that's idiotic, especially for new users.
Plus, I ran into this idiocy by being a lazy typist, and just CUTTING/PASTING stuff from elsewhere into there (middle mouse button).

As my /etc/fstab is way more complex than just what I quoted above, I had simply overlooked the line I had pasted TWICE!
This cost me no less than 45 minutes of digging, because I had no idea what the problem was.
Made an /etc/fstab backup, changed partition mounting sequence many times, deactivated swap, reactivated swap, etc. etc.

...To no avail. Until I finally spotted that one bogus line.

But HOW did I spot it? Well, by fscking my drives in the **recovery console**. There was a seemingly less important notice "/etc/fstab line XY parse error: blah blah ignored".
Well, just for the hell of it, opened a root shell (CTRL-D), edited /etc/fstab, and there was the erroneous line I had overlooked first time.

I mean ... COME ON.

This can't be a great idea to do IMHO. I do agree that the user must be informed about parse errors in /etc/fstab, but that it **won't even make it to e. g. lightdm** any more (i. e. to the GUI prompt) is fairly unacceptable.
Wish I knew who has ever had the idea to make /etc/fstab so insanely intolerant to (sometimes maybe just minor) parsing errors?

---

### Post by buzzingrobot on 2015-06-04
If the drive where the code that is lightdm lives cannot be reached because /etc/fstab is typoed, then lightdm can't be executed.  Remember, the system doesn't know it's a typo.  It just knows it's a drive that isn't there and does the only thing it can do:  Stop.

The simplest fix is to get a root shell in recovery mode and edit /etc/fstab, then reboot.

Been there, done that. ;)

---

### Post by syntaxerror74 on 2015-06-04
Yes, that's just what I had done too, read above. 

But er ... no. The typo (or mispaste) was *BELOW* all the mounts, so that should mean all partitions needed have been mounted and are ready to get programs loaded from them?
lightdm is /usr/sbin/lightdm, and this means that /usr is required. However it is mounted very early in the sequence, so that should not matter. But I can even get the startup process to a stop by cramming an erroneous line between the /home and /opt mount.

Plus, I am not too sure whether lightdm is loaded directly after the "Stopping initial device creation" message or whether it stopped after something else in between. "Debugging" this does not look too easy to me...

> It just knows it's a drive that isn't there and does the only thing it can do:  Stop.
Even THIS is pretty unacceptable. I can't seem to believe that in recent Linux I always have to fiddle with fstab when I connect or disconnect drives. AFAIR, this has never been the case in Precise or earlier releases. Sometimes it complained, yes, but then I got asked if I wanted to press S for Skip. However, no more skipping in current Ubuntus AFAICS...
Why can't it just IGNORE a drive that isn't there and say, shrug, so what, drive isn't there but I can get over it?
Why does the startup process have to be HALTED because of that? Who designed such madness? Lubuntu will show ' . . . . ' -- infinitely.

---

### Post by cariboo on 2015-06-04
From what I gather, you are complaining about your installation not knowing about a mistake you made, and that fact that you are to impatient to wait for the system to time out. This is a non-issue as far as I'm concerned.

---

### Post by syntaxerror74 on 2015-06-05
> **cariboo said:**
> From what I gather, you are complaining about your installation not knowing about a mistake you made, and that fact that you are to impatient to wait for the system to time out. This is a non-issue as far as I'm concerned.
Uhm...not quite, actually. It should simply WARN if there is something wrong with the fstab but not HALT (or block) the system either for good or for too long.

Funny too that you're questioning my lack of patience :) I once was in this situation, had to leave for 20 (!) minutes, then came back and there were still the four ' . . . . ' dots. So I hit the big one.
I other words, I don't believe you that the system will recover from this timeout too soon in my case...I would have to witness it myself.

---

### Post by QIII on 2015-06-05
As far as I recall booting has always been sensitive to certain malformations of fstab and you have to include in fstab instructions for what to do, such as nofail and nobootwait (not universally supported), when something like this occurs.

Your machine and OS are very stupid.  They can't look things over and say "Oh, I think I know what The User wants!"

I do not believe for one minute that I could ever have put a random string somewhere in the text and had it succeed.

What you believe your machine should do in the case of a mount fault and what it does do are separate matters.

---

### Post by buzzingrobot on 2015-06-05
> **syntaxerror74 said:**
> Uhm...not quite, actually. It should simply WARN if there is something wrong with the fstab but not HALT (or block) the system either for good or for too long.


If the mistake in /etc/fstab prevents the system from booting -- e.g., misidentification of the boot drive -- then you can wait forever and it won't boot. So, its not so much that the system is halting when the boot might proceed.  It can't proceed if fstab is wrong. Proceeding with the boot by making some kind of random guesses would, potentially, play havoc with filesysytems and data on the drives. It doesn't know where partitions begin and end, what file system is in use, etc. Fstab is just one of those things that need to be right.

---

### Post by cariboo on 2015-06-06
I have a system with 8 hard drives, jbod raid,  if i screwed up creating /etc/fstab, I can press Ctrl-C to continue. This system uses /dev/sda1 to boot, so the system loads first before the rest of the drives are mounted.

The system has been up for about 2½ years, in that time I've had to replace 4 drives, I started with several Seagate 750GiB that all went defective very shortly after being put in service, after replacing all of them under warranty at least 3 times, I finally gave up on them and went with WD, every time a disk was replaced /etc/fstab needed to be edited, as I use UUID to identify and mount the disks, just so you know where I'm coming from.

---

### Post by syntaxerror74 on 2015-06-06
> **cariboo said:**
> I started with several Seagate 750GiB that all went defective very shortly after being put in service
(offtopic) Doesn't surprise me a thing. You had better burn your dollar bills spent on these to have it warm in winter...:p

But to your CTRL-C thing...yes I know CTRL-C works. However, I think I hit it 20 times in a sequence, but still could not make it to the GUI logon screen (lightdm in my case). Maybe you were just lucky :razz:

---

### Post by Copper Bezel on 2015-06-08
Yeah, insulting syntaxerror's patience or understanding of how computers work is not helpful here. But it's important to realize that fstab isn't a simple script to be executed sequentially here. 

fstab *is *a place where you want fail-fast, fail-hard, fail-safe. Mounting a partition incorrectly could be very bad news (let's see what happens when the user home partition gets read as swap, yeah?) But I've also seen that "press S to skip or M for manual recovery" as lately as 14.04, which I've been doing most of my computing on, so I wouldn't know about 15.04. And yeah, that's during the dots splash and, therefore, long after the first time fstab is called, too. If a whole entry in fstab is duplicated, then the system is probably trying to assign the same UUID twice, and that seems like ... a slightly bigger problem. = / 

But it *should *have a way to recover from this, too, even if that's dropping you straight into a recovery shell. That is, again, what it means to manage failure states, which is precisely the logic behind having the system hang instead of progressing on its merry way when there's an issue in fstab in the first place. There's really no having it both ways. 

I do rather imagine that nothing has in fact changed in the boot process and that these are simply different failure states caused by different problems. I've only ever had the "skip" prompt for drives that actually existed, for one thing (whether they were physically present or not.)

---

### Post by buzzingrobot on 2015-06-08
Is it the bootloader or the kernel that parses fstab?  If the former, I wonder if there's enough room to add some accident proofing?

Ideally, it would sense when fstab was wrong, then trigger a dialogue listing all the actual partitions found on the system, and asking which one to boot from.  Dunno if that's actually possible.

---

### Post by mastablasta on 2015-06-08
actually OP is right - this is pretty stupid.

once I had partitions corrupted on windows disk. data drives D: E: just disappeared. panic ensued.

but OS still booted, and since all programs were on C:, I could brose the internet, find a solution (via 3rd party program), download the program via torrent, repair the table and well the rest is history. 

in Linux it seem I just wouldn't be able to boot not really knowing why and how to resolve it. robust OS?

---

### Post by buzzingrobot on 2015-06-08
Windows assumes C: is the boot drive. I don't think it will boot if it can't find C:.

But, yes, exposing fstab to editing -- the 'founders' assumed that users would not be doing that -- opens the door to mistakes and typoes.  As long as Unix/Linux doesn't lock into to booting from a specific physical drive, whatever mechanism is used to identify the partitions has to be configurable.

---

### Post by mastablasta on 2015-06-09
> **buzzingrobot said:**
> Windows assumes C: is the boot drive. I don't think it will boot if it can't find C:.


probably true. I am not sure but I think it assigns the C: letter to system disk but I forgot what happens if you have system on two disks and you remove one disk. I think from what I remember from the DOS era it would just assign C to the other disk and boot from it. at least I think MS-DOS did it like so. 

 however it does a better job at reporting what is wrong. "error: no system disk found" If I remember correctly - which means system disk is missing, cable is unplugged/bad contact, no system loaded on disk drive on disk or partition table missing /corrupted.
you can eliminate the first 3 options quite fast. as OP stated it didn't say what was wrong and hunting for error proved to be difficult.

fstab - yes probably not assumed it would be edited, but how else are you going to manipulate partitions on non gui OS? I am not sure if any alternative was offered.

---

### Post by buzzingrobot on 2015-06-09
> **mastablasta said:**
> ...it assigns the C: letter to system disk but I forgot what happens if you have system on two disks and you remove one disk. I think from what I remember from the DOS era it would just assign C to the other disk and boot from it. at least I think MS-DOS did it like so.

I can't recall.  The other drive would need a bootloader on it before it would boot. DOS was created for systems without hard drives, with A: and B: being floppy drives. When it eventaully could work with hard drives, when prices and size dropped, the (assumed to be only) drive was tagged C: and most people, for obvious reasons, booted from it. Pretty sure you could still boot from A:, if you wanted.

DOS had an easier time of it because it assumed there was one physical drive to boot from with one file system on that drive using a very limited partition scheme. Unix has to handle the possibility of many physical drives with complex partition schemes.  It needs to discover which of those partitions to boot from very, very early after the kernel wakes up.

The usual partition scheme for the usual desktop Linux users is dead simple. I agree that fstab's error messages are obtuse, but I don't know if there's any way to improve them. Most people do no understand partitioning and the need to think about it -- especially for dual booters -- is a real drag on the adoption of Linux.

---

### Post by Copper Bezel on 2015-06-10
People end up seeing fstab for a lot of reasons, though. Usually it's that drive the computer stupidly insists on mount ro, because 10 years of being a desktop OS isn't enough time to fix that....

Incidentally, [this error]("http://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or"), which the boot process does recover from or allow you to skip, is the one I've seen previously on my machine. (The solution? Manually editing fstab.)

---

### Post by syntaxerror74 on 2015-06-29
> **Copper Bezel said:**
> Yeah, insulting syntaxerror's patience or understanding of how computers work is not helpful here.
Thanks for that. :) 

[QUOTE=Copper Bezel]
But I've also seen that "press S to skip or M for manual recovery" as lately as 14.04, which I've been doing most of my computing on, so I wouldn't know about 15.04.[/QUOTE]
Well, recently, I've been spotting it again. But I think you must boot with upstart, NOT systemd. (I could still be wrong in thinking it is dependent on that, though.)

> But it *should *have a way to recover from this, too, even if that's dropping you straight into a recovery shell.
Right! And currently, one would have to wait in vain for that...PLUS...I consider myself an experienced user, so I can fix that even though it's a time-waster to locate the issue!
However, less experienced users (who do not necessarily deserve the honorable "noob" badge) might be searching in vain for the issue, and THAT is why I'd like to see things alleviate themselves in future.

---

### Post by mc4man on 2015-07-02
Added 'garbage' lines here to bottom of fstab in both 15.04 & 15.10. Both booted up to the desktop. 
So are you saying only in 4.x or as implied in orig. post anything over 2.x?

---

### Post by syntaxerror74 on 2015-07-08
> **mc4man said:**
> Added 'garbage' lines here to bottom of fstab in both 15.04 & 15.10. Both booted up to the desktop. 
So are you saying only in 4.x or as implied in orig. post anything over 2.x?
I guess it must be 3.x only, then. Because I've *never* installed any 4.x so far. And 2.x was way more tolerant to these things, that's for sure.

---

