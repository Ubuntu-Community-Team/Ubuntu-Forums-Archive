---
title: "Is Live CD installation problem fixed yet?"
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2012-03-06
Is it possible yet to install from the Live CD and select a custom install ("something else") without the thing crashing?

---

### Post by ventrical on 2012-03-06
> **sgage said:**
> Is it possible yet to install from the Live CD and select a custom install ("something else") without the thing crashing?

  I did an install of beta1 last night off of a USB persistent and it installed just beautifull but I didn't try 'somthing else' and , am about to try that now.

Edit:  "Something Else" is FUBARed. It tries to set you up to send an internal error report then crashes when you ignore it. I'll try from the "Live" install option as I have had much more success that way.

---

### Post by ventrical on 2012-03-06
Ok... it is just the same like with Oneiric. you have to choose "Try Ubuntu", load the Live Desktop and then you're off to the races but you have to  install it by using the "Unity" installer icon - otherwise .. forget it. I guess thats the name of the game right now:

Edit .. sorry for the bad pics .. I used my cam because it was faster .

---

### Post by ventrical on 2012-03-06
25 minutes .. faazzooom!  :)

---

### Post by OGpmpdog on 2012-03-06
Hi all,

I tried a clean install last night on my T61 laptop.

I used the 3-5-12 daily build (on USB stick).

Got a system error (ubiquity?) after clicking manual partioning, and install aborted...bummer.

Still cant do a fresh install:(

On another note, gnome shell always crashes after i type the action key and initiate an application search...I have the webupd8 gnome3 PPA installed but it seems there are some dependencies that need to be resolved before Gnome will upgrade from 3.2 to 3.391?

However, the new kernel 3.2.18 has the laptop running smoother:P

---

### Post by sgage on 2012-03-06
> **ventrical said:**
> Ok... it is just the same like with Oneiric. you have to choose "Try Ubuntu", load the Live Desktop and then you're off to the races but you have to  install it by using the "Unity" installer icon - otherwise .. forget it. I guess thats the name of the game right now:

Edit .. sorry for the bad pics .. I used my cam because it was faster .

For the past few days I've been trying to install first from 'Install Ubuntu', and when that failed, from 'Try Ubuntu'. But in never occurred t me that there was a difference between the install icon on the desktop and the install in the launcher. Sheesh!

Installing from the Unity launcher worked! Coming to you from a fresh install from today's daily...

---

### Post by kelpdip on 2012-03-06
Nope, had to use the alternate install image.

---

### Post by sgage on 2012-03-06
> **kelpdip said:**
> Nope, had to use the alternate install image.

Wow, this is one nasty regression. You wouldn't think it would be such a tough one, and you would think that it would be a top priority. Can't test if you can't install! :???:

---

### Post by larrypg on 2012-03-06
Hello,

Not sure which camp this falls in but installed from the livecd.  I first made the partitions with gparted.  I started the install from the first screen where it asks if you want to try or install ubuntu.  When the choice came up I chose something else and installed.  There was no problem.

---

### Post by ventrical on 2012-03-06
> **sgage said:**
> For the past few days I've been trying to install first from 'Install Ubuntu', and when that failed, from 'Try Ubuntu'. But in never occurred t me that there was a difference between the install icon on the desktop and the install in the launcher. Sheesh!

Installing from the Unity launcher worked! Coming to you from a fresh install from today's daily...


  It was just plain weird , I know. I had the same problems with Oneiric (as I mentioned). It is almost as if that beta1 release was designed to play a Turing game with us.  It is deliberately trying to train beta testers to use the Unity Launcher. I had heard also that Canonical is tending towards  employing this method totally, to eliminate from the new users any form of terminal code. Ok , thats all fine . Perhaps it may just be (as you suggest) a real regression with the installer overall.  I do not see the logic in that the developers would try any funny stuff and this (as it stands now) is a public relations disaster for that 200miilion user quota. And then , after reading Mark's blog ... I don't get it ! It just don't jive.

  But you know .. it's ok.  There is certainly some major 'fly in the ointment'. I'll be the first to confess that I am not intimate with the subroutines of the installer process but , from MY own experience, I can tell, or, more fairly put, assume, that the devs took the older installer program and just tried to build on that. So when the 'freeze' came it was like a breather for everybody. I know how hard this work is - so I am not faulting the devs at all.  Getting this installer framework just right has to be cut like a fine diamond. 

 So I am totally going to forget about that 200 million user thingy  sitting in the back of my mind and cut Mark S. some slack :) before I really  peeve him off .

---

### Post by ventrical on 2012-03-06
> **larrypg said:**
> Hello,

Not sure which camp this falls in but installed from the livecd.  I first made the partitions with gparted.  I started the install from the first screen where it asks if you want to try or install ubuntu.  When the choice came up I chose something else and installed.  There was no problem.

   I think thats the trick , setting the order of the partitions first to be able to get to install from the first install screen, but it doesn't do any good trying to do a side x side with an OS already on the hdd.

---

### Post by miegiel on 2012-03-17
Damn it, you guys got my hopes up :(

Found this thread after my installation failed for the 2nd time (the direct method and the desktop icon when trying ubuntu).

No luck here when starting *ubiquty* (the installer) from the launcher either. However this time I had *top* running in a terminal. That shed some light on what's happening. *Ubiquty* went on a memory binge, 1st consuming all my RAM and the gobbling up the swap file too. At the end I briefly saw a process called *kswap0* (if I remember the name correctly) pop up and the *ubiquty* process got terminated. Guilty of having memory leaks.

Now I need to find the bugreport ... and get the alternate CD I guess.

---

### Post by shuttleworthwannabe on 2012-03-17
I had the same issue; I posted [here and philinux solution helped me]("http://ubuntuforums.org/showpost.php?p=11762091&postcount=2"). You may want to try it as well.

---

### Post by miegiel on 2012-03-18
> **shuttleworthwannabe said:**
> I had the same issue; I posted [here and philinux solution helped me]("http://ubuntuforums.org/showpost.php?p=11762091&postcount=2"). You may want to try it as well.

I'll try formatting the root partition in gparted, but I think it's later in the installation process that something goes wrong. I've progressed to different stages and at least once I got to the copying files part (or something like that). If you wait at the *"who are you?"* window (where you make the user) or the select timezone window, the installation continues in the background. And it always goes wrong after the *"who are you?"* window.

Besides I really want this bug splat. I've got a faint dejavu with this bug. I'm not 100% sure but I think I had it with oneric too and I don't want to see it in a LTS edition. I'm also dual booting debian, so I have a working machine and don't mind retrying the installation till I figured out what needs to get fixed.

That said, I'm no coder. So If people have insights or tips regarding causes and tactics, they are more than welcome. But 1st I'm getting some sleep and tomorrow there's a list of 16 (possibly) related bug reports to dig through. :lolflag:

---

### Post by miegiel on 2012-03-21
Took a bit longer than planned. Hey, it's spring :D so many distractions.

**Bug report :** [https://bugs.launchpad.net/bugs/909179](https://bugs.launchpad.net/bugs/909179)

**Workaround :** On the liveCD (before you start installing)
```
sudo rm /usr/lib/ubiquity/plugins/ubi-webcam.py
```

---

### Post by BigCityCat on 2012-03-21
I am using the live cd to post this. The installer hangs at copying files. All though I downloaded this disk 3 days ago.

---

### Post by miegiel on 2012-03-21
> **BigCityCat said:**
> I am using the live cd to post this. The installer hangs at copying files. All though I downloaded this disk 3 days ago.

The installer (with me anyway) can hang at different points in the installation, but always after you proceed at the "who are you?" screen (where you make the default user). The installer is already busy installing while you enter your timezone, user, etc. So the installer will "seem to hang" depending on where it is in the process when I continue after making the user.

---

### Post by jerrylamos on 2012-03-22
NEVER trust Ubiquity to play around with your partitions.  EVER.

I use gparted to set up my partitions.  Over time I might get 10 or more in scrambled order with maybe 4 copies of various levels of ubuntu plus archive and swap and "live" partitions etc.

I get a partition set and formatted.

Then I use "Something Else" and make SURE it's got the right partition and make SURE it's got the right drive for grub.

This procedure has worked (mostly!) all the way thru 12.04 Alpha 1, 2, Beta 1.

Jerry

BTW I zsync ubuntu and lubuntu and boot the .iso direct from the hard drive, doing an install on one or another test pc's maybe once a week.

---

### Post by Quackers on 2012-03-22
I re-installed 12-04 last night from the beta1 iso (64 bit) by using the "try ubuntu" / desktop icon method. It ran fine and even correctly sorted 2 partitions for its use, without any problem. 
I did notice though that the last "copying files" function appeared to get stuck. It was showing the same point on the progress bar for more than 15 minutes. As soon as I wiggled my mouse (if you'll pardon the expression) things started moving again and the installation completed within 10 seconds.
It might be an idea to move your pointer about now and again during the process. I've seen the same kind of thing with other types of installation.

---

### Post by jerrylamos on 2012-03-22
Yeh, ubiquity got stuck this morning "configuring".  Re-started ran O.K.  Not a big deal, I start ubiquity and go do something useful somewhere else and check back in an hour or so.  I'm not pushing any keys, and I do have keyboard lock off.

Jerry

---

### Post by squilookle on 2012-03-22
I installed Kubuntu Beta last night. I went for manual partitioning and resized my swap and main partitions. These were resized successfully but the installer crashed not long after that. I restarted the computer and tried again, used manual partitioning again but made no changes, and it ran okay. 

It was a little unnerving in places as the progress bar did not move as expected and descriptions like "Installing System" were quite vague. Also, there were a few times when progress seemed to go backwards. it went from 90% to 86%, and then sat there for ages, then back to 90% and sat there for even longer, although this would all probably have been less of an issue if my confidence hadn't been knocked by the first failure. 

Still, the second install was successful and the system is working nicely. :)

---

