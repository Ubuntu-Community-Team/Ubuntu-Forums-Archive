---
title: "Recovering encrypted home directory"
date: 2009-11-22
forum: Security
---

### Post by Ck.asdf on 2009-11-22
Hello, last night I was listening to music in Ubuntu 9.10, and the battery died.  I plugged it back in, and it gave me an error about there being corruption in the filesystem, etc, and it couldn't boot.  Windows boots just fine, but Ubuntu won't.
I booted to Ubuntu Live & tried to look at my home directory, and saw two files, relating to the encrypted home directory stuff (which I chose to enable at install time).

Access-your-private-data.desktop
README.txt

I tried to follow the instructions but I got a message after typing my encryption password:

> setmntent: Read-only file system
After that, it still didn't show me my stuff.  I tried a wrong password just to see what would happen, and it did indeed complain about being wrong, so my first password was right.

Any suggestions of other things I can do to get my data back?

---

### Post by FuturePilot on 2009-11-22
I think all you may need to do is to run fsck on the drive. You can do that from the recovery console (boot into Recovery Mode from Grub) or from a Live CD by running

```
sudo fsck -C /dev/sdXY
```

Where XY is the corrupted partition. For example, /dev/sda2

If that doesn't fix your corruption you can access your files from a Live CD with these instructions. [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

---

### Post by Ck.asdf on 2009-11-23
> **FuturePilot said:**
> 
```
sudo fsck -C /dev/sda3
```
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

Thanks for the help!  I did see something about fsck among trying to get things working again, but when I tried to run it at one point in time (not sure if it was in the console of the installed OS or on the live CD), it claimed the command didn't exist, or maybe I just wasn't using it correctly.
Anyway, after running it and furiously tapping "y" to fix everything, about five minutes later I was back in Ubuntu!

I didn't need the link you gave me, but I'm going to hang on to it just in case I need it in the future.


Do you think that now that I've run fsck my system should be stable enough to use as is, or should I reinstall Ubuntu after backing up my stuff?

---

### Post by cariboo on 2009-11-23
Your system is repaired and should run normally, I had that happen on a raid array and running fsck repaired the problem. It ran for another year until I broke the array apart.

---

### Post by FuturePilot on 2009-11-23
> **Ck.asdf said:**
> Thanks for the help!  I did see something about fsck among trying to get things working again, but when I tried to run it at one point in time (not sure if it was in the console of the installed OS or on the live CD), it claimed the command didn't exist, or maybe I just wasn't using it correctly.
Anyway, after running it and furiously tapping "y" to fix everything, about five minutes later I was back in Ubuntu!

I didn't need the link you gave me, but I'm going to hang on to it just in case I need it in the future.


Do you think that now that I've run fsck my system should be stable enough to use as is, or should I reinstall Ubuntu after backing up my stuff?

Great! Yeah, your system should be fine. No need to reinstall.

---

### Post by Ck.asdf on 2009-11-23
Very cool, thanks again. :)

Is there some way I can click something that gives you thanks or something?  I know that sort of thing is implemented on a few different forums I've been to, but I can't remember if there's such a thing here.

Also, how do I change this thread to being "[SOLVED]" ?

---

### Post by FuturePilot on 2009-11-23
> **Ck.asdf said:**
> Very cool, thanks again. :)

Is there some way I can click something that gives you thanks or something?  I know that sort of thing is implemented on a few different forums I've been to, but I can't remember if there's such a thing here.

Also, how do I change this thread to being "[SOLVED]" ?

There used to be a thanks button but it was removed because it was making the forum unstable. To mark it solved click "Thread Tools" at the top of the thread and "Mark Thread as Solved"

---

### Post by Ck.asdf on 2009-11-23
Well, at least you have my unofficial thanks. ^_^

Have a great day!

---

### Post by Ck.asdf on 2009-11-23
Ruh, roh, Raggy!
So, I was browsing Amazon, looking for some music I could pick up (this week is Black Friday sale, get $3 in free MP3s!), when all of a sudden, Firefox locked up (stopped responding, faded to black).

I waited around for a little bit (couple minutes) to see if it would come back, but it didn't, so I opened the System Monitor and chose to "stop" Firefox.  I did that a couple times, no go, then chose "kill."  Still nothing.  I right clicked on the Firefox button in the task manager, close, finally it said "this window's not responding, kill it?"  I selected yes, and it disappeared from the task bar, but not the System Monitor.

I waited, then tried kill again, nothing.  I decided to log off, figuring that'd kill everything.  It was difficult logging off, but I eventually managed it, but it dropped me to the console instead of GUI.  I pressed ctrl + alt + F7 and saw it attempting to re-load the GUI, but it never got there.

Restarted, got the same message as what brought me to create this thread.
Ran "fsck -C /dev/sda3 -y"  and I'm back ... but I'm worried that it isn't going to last.

Is there anything I can do to find out what might be causing this instability?
A few notes:

I'm using ext4 file system
Ubuntu 9.10 x86 32bit
hardware details in my signature

I'm attempting to use this as a sort of hobbyist audio production machine (as well as standard user things such as Firefox, etc), and as a result I have Jack audio on here. I also have pulseAudio because I can't seem to get rid of it.

One thing I just remembered is both times I've had this problem, I've been playing music from Aqualung - to be specific, MP3s from an NTFS partition.
The first time the problem occurred, I was using Jack to power the audio for Aqualung, the second time (tonight) I was just using pulseAudio, since Jack didn't seem to want to start (it claimed something else was using hw0).

The only two things I had running tonight were Firefox & Aqualung.

Any suggestions?

---

### Post by FuturePilot on 2009-11-24
Hmmm. I'm really not sure on the freeze problem. I would suggest making a new thread on that problem in the appropriate forum as you probably won't get too much help in the security forum for an issue like that.

---

### Post by Ck.asdf on 2009-11-24
Okay, good point. I shall do that. Thanks again!

---

