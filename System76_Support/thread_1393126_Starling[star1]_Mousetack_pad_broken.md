---
title: "Starling[star1] Mouse/tack pad broken"
date: 2010-01-28
forum: System76 Support
---

### Post by black_ice=cream on 2010-01-28
Hey peoples! I installed the new updates on my star1 and after words, the screen went blank and the mouse wouldn't move. So I cycled the power and when it rebooted my mouse and the track pad both were unresponsive! I can't do anything because the mouse doesn't work. WHAT NOW?!?!?!?!?! BTW I have xfce and gnome using synaptic. ALSO, when it boots up, on the log in screen it has a message that says: MAL [something] is not running. And the title of the window is: Xfce power manager. IDK if this has anything to do with it. Please comment.

---

### Post by thomasaaron on 2010-01-29
Try using a USB mouse until we get it figured out.

We don't support xfce, but try booting into gnome and see if you have the same problem.

---

### Post by jsimmond on 2010-01-29
> **black_ice=cream said:**
> Hey peoples! I installed the new updates on my star1 and after words, the screen went blank and the mouse wouldn't move. So I cycled the power and when it rebooted my mouse and the track pad both were unresponsive! I can't do anything because the mouse doesn't work. WHAT NOW?!?!?!?!?! BTW I have xfce and gnome using synaptic. ALSO, when it boots up, on the log in screen it has a message that says: MAL [something] is not running. And the title of the window is: Xfce power manager. IDK if this has anything to do with it. Please comment.

The same thing happened to my Starling this morning, while updating. I loaded the kernel in recovery mode, but everything I've tried there isn't helping. When I ran the "Repair broken packages" option, it says that there are problems with the "winbind" package. I tried to remove/purge it using aptitude, to no avail. 

Any ideas?

---

### Post by jsimmond on 2010-01-29
> **thomasaaron said:**
> Try using a USB mouse until we get it figured out.

We don't support xfce, but try booting into gnome and see if you have the same problem.

I tried that, it doesn't work ..

---

### Post by thomasaaron on 2010-01-29
OK, I'm updating my Starling to see if anything goes wrong...

---

### Post by thomasaaron on 2010-01-29
OK, I just ran updates and nothing broke. So it is something specific to your set-up.

It kind of sounds like a grub issue to me. Are you running 9.04 or 9.10

---

### Post by jsimmond on 2010-01-29
> **thomasaaron said:**
> ok, i just ran updates and nothing broke. So it is something specific to your set-up.

It kind of sounds like a grub issue to me. Are you running 9.04 or 9.10

9.10

---

### Post by thomasaaron on 2010-01-29
When you see the "Grub" in the upper left, try pressing the "Shift" key to get a kernel menu. Select the previous non-recovery mode kernel and boot from it. Let me know if your touchpad works there.

---

### Post by jsimmond on 2010-01-29
> **thomasaaron said:**
> When you see the "Grub" in the upper left, try pressing the "Shift" key to get a kernel menu. Select the previous non-recovery mode kernel and boot from it. Let me know if your touchpad works there.

Yeah, I had already tried this. It doesn't work - no mouse, and looks like no keyboard either (since I can't ctrl-alt-F to another tty).

Looked at dmesg, the only errors I can find are hal segfaults (about 5 in a row each time):

hal[1655]: segfault at ef8ce37c ip 08057d36 sp bf8edd40 error 5 in hald[8048000+5a000]

---

### Post by jsimmond on 2010-01-29
Fixed it! I reinstalled the hal package, and now everything is back to normal after rebooting. Thanks for all your help, Tom!

I'm guessing something in this morning's update broke hal ...

---

### Post by black_ice=cream on 2010-01-29
AHH!!! Okay, let's not forget about me!!!!! Okay, I can't do anything because when I turn the comp. on it just boots up, but the mouse doesn't work!?!?!?!

---

### Post by cposs on 2010-01-30
I had this same problem and also had to drop in to recovery mode to fix it.  [black_ice=cream]("http://ubuntuforums.org/member.php?u=984488"), try this:

1. Plug the computer in to a network connection.  It's easier to just have wired networking come up than try to get wireless working from the command line. 

2. Reboot your computer  and enter recovery mode as thomasaaron directed in one of his earlier posts (hit shift when you see "grub" come up on your screen after the bios screen goes away).  Once you are booted into recovery mode (the screen should be mostly blue) go to the "console as root with network" or something like that, and the screen will go black with white command line text. 

3. First enter this to get rid of the package that (probably) didn't install correctly:
 ```
apt-get remove winbind
```4. Enter ```
apt-get install hal winbind
``` to reinstall hal, and put winbind back.  This time, unlike the automated upgrade, you should be asked if you want to keep your current version of a config file or switch to a new one.  Unless you've made changes to the file yourself, say "y" to switch to the new one.

5.  Reboot, and you should be ok.  If you can't get the winbind to remove, you might have to run a "dpkg --configure -a"; I forget exactly what I had to do.

There's probably a way around removing and then reinstalling winbind, but that's what worked for me.  Good luck.

---

### Post by black_ice=cream on 2010-01-31
when I press shift when grub is loading, nothing happens...

---

### Post by jsimmond on 2010-02-01
> **black_ice=cream said:**
> when I press shift when grub is loading, nothing happens...

I had to press Esc to get the Grub menu on my starling, maybe it's the same on yours.

---

### Post by black_ice=cream on 2010-02-01
yeah Mines Esc 2 I figured out. But I did the instructions and didn't work... I'm going to go try it again. Okay it still didn't work. I booted into safe mode and did the 'drop in root shell prompt' (or something like that) and typed: apt-get remove winbind and then apt-get install hal winbind and then I typed reboot and the mouse still doesn't work and I still get the message of: HAL is not running. What now?!

---

### Post by cposs on 2010-02-01
Oh, yeah, I forgot on grub v1 it's ESC and on grub v2 it's shift to go to the list.

I made a mistake in my earlier instructions, too.  Sorry about that. You need to run: ```
apt-get install hal --reinstall
```If you don't tell it to reinstall it just assumes that the installed files are OK, and does nothing.  Since you're trying to fix a corrupted or missing file you need it to do the reinstall.   

You might need to have a network connection so it can download the hal package if you don't have the deb on your hard drive.

---

### Post by black_ice=cream on 2010-02-01
YES THANK YOU THAT FIXED IT!! Thank you so much man!! :] I really appriciate the help, as I am a complete nooby! :P It was weird though... I tried it first wirelessly, and it didn't work and when I tried it with a wired connection, it worked!!! :D

---

### Post by MarkID on 2010-03-25
I finally upgraded my Starling to 9.10 and had the problem with the broken touchpad.  I tried the procedure described here (reinstalling hal) and it seemed to work.  But the next day when I turned my Starling on, the touchpad was broken again.  I tried both "drop in root" and "drop in root with networking," and I had a wired connection.  I'm leaving this weekend and I need my Straling to work.

---

### Post by thomasaaron on 2010-03-25
MarkID,

Please boot into netroot and run...

sudo apt-get install grub-pc

Did that fix it?

---

### Post by MarkID on 2010-03-25
Thank you, Thomas.  It appears to have solved the problem.  Ubuntu is great.  S76 is better.

> **thomasaaron said:**
> MarkID,

Please boot into netroot and run...

sudo apt-get install grub-pc

Did that fix it?

---

