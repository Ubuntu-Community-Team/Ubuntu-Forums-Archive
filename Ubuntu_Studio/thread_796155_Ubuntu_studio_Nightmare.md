---
title: "Ubuntu studio Nightmare"
date: 2008-05-16
forum: Ubuntu Studio
---

### Post by jonesints on 2008-05-16
Hi, 

I'm running Ubuntu Studio Hardy 64bit, on AMD64, (dual processor), 3GB RAM on a 500GB SATA HD. 
I also have a dual boot on another HD with the generic, 32bit Hardy + xp. 
I've had no probs with Hardy 32bit at all, but for some reason Studio 64bit is extremely unstable! I did a fresh DVD install. 
What I usually have problems with is:

1) System hangs often, even doing menial tasks like copying files. Any idea why?
2) Jack: if the pc freezes, I get no capture sound when i re-start it after stopping or killing Jack. I end up having to restart the pc! 
so 2nd question is > how can i restart jack COMPLETELY through the terminal without having to restart my pc?

3) Ardour: sometimes it hogs all my CPU, without any armed tracks! Strangely enough the first times I used Ardour on Studio64bit, I recorded 8 tracks at once, without xruns or CPU demand, until it hanged suddenly after 5 mins of recording.

These 3 problems could be related. I have used the Ubuntu Studio Controls to lock memory to different % to see if this was a memory issue. I changed the memory locking, from disabling it, to having it over 86%. no luck, system and Ardour still cause problems.


The sound card used with jack, in both versions of ubuntu, is an RME hammerfall, with the same settings, only 32bit hardy is not running RT kernel.
I dont have problems running jack in RT, i might add. no xruns or CPU overload. Its when I open Ardour things are ugly.

Any help on the above issues is v much appreciated!


Jonesints

---

### Post by thorgal on 2008-05-16
did you try to compile ardour yourself ?

---

### Post by jonesints on 2008-05-16
No... this is the default installation of jackd and ardour from the DVD. Im afraid im still learning linux, since i started some months ago from scratch, being fed up of windows.. but surely a clean DVD install of 8.04 ubuntustudio shouldnt be a problem?

btw, i didn't edit the audio-group limits.conf since I thought this version (8.04) took care of it with the GUI provided.

---

### Post by jonesints on 2008-05-16
please, any help is greatly appreciated! am really stuck not using ubuntu studio until i can sort out whats wrong!

---

### Post by Stochastic on 2008-05-16
This sounds almost like there's an issue with your hard drive being corrupted.  Does it only hang when Ardour runs?  You might want to do an fsck on the drive in question.  Boot into your other install, then do ```
sudo fsck /dev/sda1(or whichever drive your UbieStudio install is on)
```

Another useful step would be to run an strace on ardour (if that's the only time it hangs) do ```
strace -o ardourLog.txt ardour
```
Then, after things lock up and you reboot, take a look at the fiel ardourLog.txt that strace creates for possible signs as to where the error is coming from.  You may want to attach it to this thread if there looks to be any useful error messages.

---

### Post by jonesints on 2008-05-16
Thanks Stochastic, I ran the fsck on it, here are the results on terminal:

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb1: recovering journal
Clearing orphaned inode 29605921 (uid=1000, gid=1000, mode=0140755, size=0)
/dev/sdb1: clean, 124829/29786112 files, 2994305/119127991 blocks

Looks ok?

On the other hand I didn't get to run the strace since as soon as I logged in to Ustudio, it hanged. Its gotta be something else other than ardour?

thanks again for the help!

---

### Post by thorgal on 2008-05-16
does your PC hang in console mode only ?
I suggest you boot in single user mode (i.e. 'recovery mode' if it shows up in your grub menu at boot start). Log in as root in the console and do a few minor things in the shell ... are you familiar with shells by the way ? I think you could see if your PC is unstable due to certain services like Xorg (which graphics card are your  running ? a faulty X driver can hang the PC just like that). Another thing, when it hangs, is the kernel still alive (have you ever used the 'kernel hacks' aka SysRq key and the reverse BUSIER sequence ?)

---

### Post by beepo on 2008-05-16
I also have 64-bit system that I used to run with 64-bit version of Fedora / Planet CCRMA. The system was _really_ unstable. it hanged up for example when I created a large tar archive.

Any 32 bit OS worked fine.

The reason ultimately was the clerk at the computer store that sold me memory chips that were not compatible. The chips were both suitable for my motherboard but from different vendors.

You should try to run Memtest86+ over night (I think it is a option with Ubuntu Studio / Ubuntu DVD boot menu) and if any errors appear first try to change your memory modules to the same maker and the excactly same model. Then run Memtest again. If it still fails it is your processor or the motherboard.

I was able to get away with quarantee. Although it took 18 months of unusable system time of my brand new workstation to figure out the stupid mistake at the store.

---

### Post by jonesints on 2008-05-17
i ran a strace when i opened ardour. i attached a part of the log created (it was 19mb big!)

thorgal, im running a GeForce 7600 GS. I heard some cards are incompatible with ubuntu studio?  
I'm afraid i'm no good with shells.. yet. still got loads to learn!

I'll get back on the case when im home again on sunday. i'll run beepos suggested memtest then. 


thanks for your help

---

