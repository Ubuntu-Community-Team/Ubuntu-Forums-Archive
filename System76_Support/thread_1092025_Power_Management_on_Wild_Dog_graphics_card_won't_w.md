---
title: "Power Management on Wild Dog: graphics card won't wake from sleep"
date: 2009-03-09
forum: System76 Support
---

### Post by darmok on 2009-03-09
I apologize in advance for any deficiencies in my description.  I'm a newbie to Linux; a convert from MacOS X.

I bought a Wild Dog Performance (revision "Wilp5") from System76 a few weeks ago, and have been trying to debug this power management issue.  Basically, the system cannot wake successfully from any low-power mode, and I'm forced to restart the machine each time I try to wake it.

When I put the Wilp5 in "suspend" mode, I can wake it by pressing the power button on the front panel of the enclosure.  The computer seems to wake fine (lights turn on, hard disk and fans whir normally), but there is no signal from my graphics card to my monitor.  Reseating the monitor's plug in the DVI port doesn't help, nor does reseting the monitor.  I am forced to restart the computer.

Curiously, when I try to wake my machine from "hibernate" mode, the computer behaves as with waking from "suspend," but there appears to be a signal getting to the monitor.  The monitor's signal indicator glows, the blackness of the screen looks powered, and a cursor appears that I cannot move around the screen.  No hint of the desktop, though, just a blank screen, save for the cursor.  Again, I'm forced to restart the computer.

If it helps, I've been told that power management problems can be the root cause of some audio-visual problems.  I've also been having trouble with playing DVDs on my computer: no matter what program I use (VLC Player, MPlayer, Totem), some DVDs just won't play properly.  Sometimes the video is choppy and poor, sometimes the player can't even load the main DVD menu.  Don't know if this helps.

Thanks for reading this far.  I appreciate any help you folks might have.

---

### Post by darmok on 2009-03-10
I've also noticed a similar problem when trying to switch between users.  When I have to user accounts active then log out of one of them, I'm not taken to the Ubuntu login screen.  Instead, the signal to the monitor goes dead as with waking from suspend (described above), and I'm forced to restart the computer.

---

### Post by thomasaaron on 2009-03-10
Most likely, the suspend/hibernate-resume issue is related to the ATI card. Sleep and hibernate are not part of normal testing for desktop systems. However, we know some users would like to have this feature, so we are working on it. (It will probably progress by itself as fglrx improves.)

As for your DVD's, two things...

1. Make sure you have run this tutorial...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

2. Go to a terminal and run this command...
```
gstreamer-properties
```
Under the "Video" tab, in the first drop-down selector, choose "X Window System (No xV)."

That should cure the choppy playback.

As for which dvd player to use, I recommend VLC. Totem has always been a pain.

---

### Post by darmok on 2009-03-10
Thanks, Tom, for the post.  I was unaware of the driver used to control ATI cards.  An interesting post from Saturday's LinuxToday.com discusses the issue in greater detail:

[http://www.linuxtoday.com/news_story.php3?ltsn=2009-03-07-002-35-RV-HW]("http://www.linuxtoday.com/news_story.php3?ltsn=2009-03-07-002-35-RV-HW")

Thank you, too, for the Knowledge76 link. I'll look into the video issue further.

---

### Post by darmok on 2009-03-16
I made the change suggested above, using gstreamer, and found that not only did it solve the video flickering problem, but it also partially solved the sleep problem described at the start of this thread.  After changing the default video output plug-in to "X Window System (No Xv)" I found that my Wilp5 nearly wakes up from sleep after being put in "hibernate" mode.

When I wake the machine from hibernate, the monitor now wakes from low-power mode, and a blinking command-line cursor appears.  Following are the Intel BIOS screen, the usual Ubuntu command-line start-up messages, and the Ubuntu start-up progress bar with the message "waking up" at the bottom of the screen.  After the progress bar fills, the screen turns black and I'm forced to reboot.  The same thing happens if the default video plug-in is set to "X Windows System (X11/Xshm/Xv)," the only other plug-in listed in gstreamer.  The "suspend" function remains unaffected, behaving as described in my first post.  Any ideas how gstreamer's video options could have affected this, and if there's a setting that would fully solve the sleep problem?  Are there other plug-ins I could install that might work?

Thanks!

---

### Post by darmok on 2009-10-01
After performing a clean install of Ubuntu 9.04 (64-bit), I found that the hibernate and switch user problems were solved.  They now function as they should.  Presumably, whatever software controls these functions was fixed in 9.04.

---

