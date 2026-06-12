---
title: "Unable to mount filesystem"
date: 2010-03-29
forum: System76 Support
---

### Post by pnjabi on 2010-03-29
Hello - I am kinda novice in linux and need some help in debugging the following problem:
 
I have Meerkat Nettop w/ Ubuntu 9.10 and when I turn on it starts running all the checks and then gives the error:
 
"Unable to mount filesystem A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry"
 
Control-D just terminates and that's it.
 
I know the filesystem is corrupted...is there a way to get it back or do I need to do a clean install? Any help will be greatly appreciated.
 
Thanks,
Jaz

---

### Post by thomasaaron on 2010-03-29
You can try running fsck from a live CD to fix the filesystem. Here are instructions...

> -------------------------------------------------------
To run fsck, first boot from a live CD. Once you are booted, to to System > Administration > Partition Editor. This will show you your current partiton layout and the designations of your partition. For example, your partitions may be /dev/sda1, /dev/sda5, and /dev/sda7. Whatever the designations, make note of them. 

Then open a terminal (Applications > Accessories > Terminal) and run fsck as follows (only use your own partition designations)...

sudo fsck /dev/sda1
sudo fsck /dev/sda5
sudo fsck /dev/sda7

fsck will examine your filesystems and try to repair any damage. Occasionally, filesystems get too broken for fsck to fix them. In this is the case, it may be necessary to put a fresh image on your machine.

It could also mean that you have a faulty hard drive. However, this is pretty rare, and it is better to try re-imaging the machine first.
------------------------------------------------------


Also, did you encrypt your home partition when running through the initial user set-up routine.

---

### Post by pnjabi on 2010-03-29
Thank you! I will try the instructions later tonight and No, I didn't encrypt the home partition during the initial setup. 
 
> **thomasaaron said:**
> You can try running fsck from a live CD to fix the filesystem. Here are instructions...
 
 
 
Also, did you encrypt your home partition when running through the initial user set-up routine.

---

### Post by jpoRS on 2010-03-29
Thomas,

I get an almost identical error on my Panp4i, running a fresh Karmic install.  Error message is the same except when I hit Ctrl-D it restarts the filesystem scan, eventually kicking me back to the same error.

Also, tried live disking already, and get an "Error: Cannot read Boot CD" message.  Tried manually running fsck, fixed errors as prompted, still no dice.

Sorry for threadjacking if our problems aren't as related as they seem.

Thanks,
jim

---

### Post by pnjabi on 2010-03-30
The instructions by Thomas worked for me. I was able to fix the errors using the live CD...will keep an eye out to see if it happens again. 

Thanks again.


> **jpoRS said:**
> Thomas,

I get an almost identical error on my Panp4i, running a fresh Karmic install.  Error message is the same except when I hit Ctrl-D it restarts the filesystem scan, eventually kicking me back to the same error.

Also, tried live disking already, and get an "Error: Cannot read Boot CD" message.  Tried manually running fsck, fixed errors as prompted, still no dice.

Sorry for threadjacking if our problems aren't as related as they seem.

Thanks,
jim

---

### Post by thomasaaron on 2010-03-30
jpoRS, did you encrypt your home partition? Does your error say anything about not being able to mount the swap partition?

---

### Post by jpoRS on 2010-04-04
Sorry for the delay, have to wait to have access to another computer.

I did not encrypt, and it makes no mention of an issue mounting swap. Will not mount /home.

Thanks,
jim

---

### Post by thomasaaron on 2010-04-05
I definitely would try running fsck from a live CD. If you're getting...

"Error: Cannot read Boot CD"

...you may have a bad live CD. You also may try re-seating your DVD drive if you're sure your CD is good.

---

### Post by jpoRS on 2010-04-05
Downloaded and burned two disks, both check out fine on my girlfriends computer.

Do you mean re-seating the disk, or opening the actual body of the laptop.

Thanks,
jim

---

### Post by thomasaaron on 2010-04-06
I mean pulling the actual DVD drive out and putting it back in. There's a deeply inset screw, and another screw close to it. You'll have to remove the larger panel on the bottom of the computer to expose the other screw.

Then you can pop the drive out.

---

### Post by jpoRS on 2010-04-06
Sigh.  I was hopping that wasn't what you meant.  Will try asap, thanks TA.

---

### Post by Eldera on 2010-04-06
Tom, could jpoRS also check things out with an eternal USB CD/DVD drive, if he or his friends have one? That is what I have been using on my panp4n since I dropped it and banged the CD/DVD drive out of line.

---

### Post by thomasaaron on 2010-04-07
Sure. If he has one, that would be a great idea.

---

