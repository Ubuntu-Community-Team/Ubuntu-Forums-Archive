---
title: "Frustrating mouse/touchpad clcik issue - PanP7"
date: 2012-01-29
forum: System76 Support
---

### Post by isaacullah on 2012-01-29
Dear Sys76 support staff and fellow Sys76 computer owners,

   I have been experiencing a very frustrating new issue with mouse behavior. I will first describe the problem I am experience, and then provide contextual information.

Description of the problem: Intermittently, the mouse stops being able to click anything at all. Neither left nor right click nor scroll wheel work. Eventually, if I hit the right click button several times (like 20 clicks), a right click context menu will appear. Once that happens, I can then left click in the current window, but not in any other window or in the background. Not until I close the window, that is. Then, I get to start this joyous process all over again with the next window! I should say that this regardless of whether I am using the touchpad or any variety of external mice (I've tried four). The mouse works fine at login, but this behavior starts again after Ubuntu loads up. Sometimes, I am able to briefly restore normal mouse behavior by typing the >sudo rmmod psmouse command followed by the >sudo modprobe psmouse command in a terminal. But this does not last. Sometimes, I also get an error window with the "Cannot grab your mouse" error in it, but only when I try to start the System76 driver or other system configuration tools from the start menu.

Contextual information: This is on a PanP7, and started last week when I finally committed to doing the latest kernel upgrade. I was still on Ubuntu 11.04, and everything was peachy keen before the kernel upgrade. I then tried to update to Ubuntu 11.10 hoping that would solve it, but no luck. Then, I did a fresh install of Linux Mint 12, but still had this problem. Finally, I've done a fresh install of Ubuntu 11.10, and am still having this issue. I have also tried the "system restore" function in the System76 driver (figured it couldn't hurt)
 
Extraneous information that may also help: The only other thing that has changed recently is that upon startup, the screen is always set to it's lowest brightness, and I have to manually turn the brightness up with Alt-F9. This happens every time.

Preliminary hypotheses: Extensive googling hasn't yielded any concrete help for me. I have read some forum and blog posts that suggest that mouse issues have become widespread since the last kernel update. 

Next steps: Is anyone else having this issue? It is quite frustrating, and makes it very difficult to use the computer. I'm in the middle of writing my PhD dissertation right now, and this is making it very difficult for me. Any concrete ideas on what is going on, and what I can do to things back working properly? I have a disk image snapshot that I made with Clonezilla before I did the kernel update. Should I just revert back to that image? Things definitely were working then...

Any help will be GREATLY appreciated...

~Isaac Ullah

---

### Post by isaacullah on 2012-01-29
Well finally (!), after many many google searches, I have discovered that I have fallen prey to a very long-lived outstanding bug (ongoing since 2007): [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)

The good news is that the last fix listed in the above bug-report thread worked like a charm!

I uninstalled "mousetweaks", reinstalled "xserver-xorg-input-mouse" and  "xserver-xorg-input-synaptic-touchpad" for good measure, restarted, and the issue is gone! 

The monitor is still at it's dimmest setting, however. I'm currently trying to install the proprietary ATI driver, however, and hopefully this may solve that issue. I'll post back with an update after the proprietary driver is installed....

---

### Post by isaacullah on 2012-01-29
Well, installing the proprietary ATI drivers has fixed the dim display issue!

Isaac: 2
Annoying "bugs": 0

:)

Hope this lovely series of posts helps someone!

---

### Post by isaacullah on 2012-01-30
Well, sadly, I have bad news. The above fix didn't actually work completely. While it seemed to have solved the problem, plugging in a peripheral (in this case, and external sound card) brought the problem right back. Even after reboot the problem persists... I am SURE that I am experiencing the bug I linked to earlier, as the symptoms described in that thread are exactly what I am experiencing... 

I'm not sure if the Sys76 support staff can help me with this issue? It seems to be an internal Ubuntu bug... But perhaps they know of a workaround for Sys76 hardware?

Again, any help would be greatly appreciated!

---

### Post by smarmytime on 2012-01-30
I don't know if this helps, but I had a problem with the touchpad on my PanP7 a while back...it would seem to just stop working, for no apparent reason. Turns out there's some kind of a "feature" where if you hold down the shift key (or maybe it's the control key, I can't remember) for 8 seconds, it locks the touchpad (unconscious habit of mine, when I pause to think while typing, I'll sometimes hold that button down, usually at the beginning of a sentence - so probably the shift key). Once I realized that that's what was locking it, I realized that holding it for another 8 seconds would unlock it.

Like I said, probably unrelated to your problem, but I figure any information, no matter how peripherally related...

---

### Post by isaacullah on 2012-01-30
@Smarmy. Thanks for the suggestion, but yeah, that's not the issue here... It's a more fundamental bug in the system... If I can't figure out a workaround or real fix in the next few days, I am seriously considering going back to my last Clonezilla snapshot, and staying at the old kernel in 11.04 forever... That's a bit drastic, but I definitely can't live with the mouse acting this way!

---

### Post by smarmytime on 2012-01-30
That's not that bad an idea...go with what works, wait for the LTR to come out. Wish I had more to offer...

---

### Post by isaacullah on 2012-01-30
Well, I did just that. Thankfully I had the sense to take that snapshot before "upgrading" to the latest kernel. I've been burned in the past by kernel updates, so I was kinda expecting something to go wrong this time! Now I'm back in 11.04, and my mousey works the way it should! Three cheers for Clonezilla!

---

### Post by isantop on 2012-01-31
We have seen this bug before (I've seen it a few times myself). 

Luckily, in my pre-initial Precise testing, the issue seems to have gone away for good. We don't recommend upgrading this early on, since stability issues are almost certain to arise. That said, we can look forward to this issue being gone once 12.04 is released.

---

### Post by isaacullah on 2012-01-31
Good! Because, believe it or not, the issue is still here, even though I reverted to a Clonezilla snapshot that I am SURE I took before I started experiencing the issue! I was so hopeful that I could just go back to the happy past where my mouse and trackpad just worked! Any ideas on why it occurs, and what I can do in the meantime to minimize its affect on my daily computing life (until 12.04 comes out)?

---

### Post by isantop on 2012-01-31
I haven't seen it occur on a system that's been up and running for a while, so that might be an option. As for why it happens, I'm not really sure.

---

### Post by isaacullah on 2012-02-01
Well, thanks for the help anyhow... I'll await the 12.04 release, but in the meantime I'll keep trolling the forums and buglists and trying things out. If I somehow discover a fix that works, I'll report back here...

---

### Post by isaacullah on 2012-02-02
Well, I've been going down the list in the big long bug report, and trying all the work around suggested by other folks. I've found one that works, sort of. I say "sort of" because it gives me about 15 minutes or so of normal mouse behavior before the bug rears its ugly head again! The work around is to hit ctr-alt-t to bring up a terminal, and to enter the following command: ```
sudo modprobe -r psmouse && sudo modprobe ps mouse
```

Like I said, this only gives me about 15 minutes of normal mouse behavior, but at least I can get it back! Thank the flying spaghetti monster! So I guess until this bug is truly fixed in a future version of ubuntu, I am living my computing life in 15 minute increments. Why am I getting flash-backs to the first season of LOST? ;)

---

### Post by isaacullah on 2012-02-02
I just want to report that restarting the x-server provides a better workaround for me. I had to restart it two times, but on that second time, mouse behaviour is now normal, and has stayed normal for three hours now. I had to enable the ctrl-alt-backspace key shortcut (it's turned off by default in ubuntu).
The exact procedure that worked for me was to reboot, log in, immediately resart X, log in again, immediately restart X again, and then log in one last time.

I haven't run the updates yet as I'm working on something important at the moment and can't risk a (more) broken system. I will likely run the updates sometime this weekend, and will report back about whether or not they have any effect on this bug (that is, if they don't break my system!).

---

### Post by isaacullah on 2012-02-08
Just reporting back in. Finally had time to do the latest updates. Got the new kernel and new version of X. Rebooted, and thought that things were fixed for a few moments (!), and then I started Firefox and the mouse started acting screwy again! The (relatively) good news is that the work around still works. Restarting X is my new computing habit!

---

### Post by wi! on 2012-02-09
> **smarmytime said:**
> I don't know if this helps, but I had a problem with the touchpad on my PanP7 a while back...it would seem to just stop working, for no apparent reason. Turns out there's some kind of a &quot;feature&quot; where if you hold down the shift key (or maybe it's the control key, I can't remember) for 8 seconds, it locks the touchpad (unconscious habit of mine, when I pause to think while typing, I'll sometimes hold that button down, usually at the beginning of a sentence - so probably the shift key). Once I realized that that's what was locking it, I realized that holding it for another 8 seconds would unlock it.

Like I said, probably unrelated to your problem, but I figure any information, no matter how peripherally related...

  I am experiencing an issue lately that sounds like what you are describing. I have a serp7 pro. Do you remember if it does this lock if you can unlock it with the Fn+F1(Or whatever disable/enable key you have mapped)? Because I tried that and mine won't unlock with Fn+F1 so just trying to narrow the problem down. Definitly seems to be a touchpad issue because if I plug my usb mouse in, everything is fine.  Update: Nevermind I shoulda done this test before posting....My touchpad does not disable when the shift key is held down.

---

### Post by smarmytime on 2012-02-10
> **wi! said:**
> I am experiencing an issue lately that sounds like what you are describing. I have a serp7 pro. Do you remember if it does this lock if you can unlock it with the Fn+F1(Or whatever disable/enable key you have mapped)? Because I tried that and mine won't unlock with Fn+F1 so just trying to narrow the problem down. Definitly seems to be a touchpad issue because if I plug my usb mouse in, everything is fine.  Update: Nevermind I shoulda done this test before posting....My touchpad does not disable when the shift key is held down.

No, but I never tried that as a solution. As I said, it would lock when I would hold the shift key down for 8 seconds (the left one...it's a habit when I pause for thought when I'm typing), and it would unlock when I would hold the same key down, for the same amount of time.

---

### Post by HunkirDowne on 2012-02-12
> **smarmytime said:**
> No, but I never tried that as a solution. As I said, it would lock when I would hold the shift key down for 8 seconds (the left one...it's a habit when I pause for thought when I'm typing), and it would unlock when I would hold the same key down, for the same amount of time.

Well, thanks **smarmytime**, I think you have solved a '*problem*' I am having and discovered a feature at the same time.  My 'problem' is that I wanted to disable the touchpad for an extended period of time and think this just might do the trick.  I can't test it right now because I'm using an external pointing device and my trackpad is not active at all (which is the feature I alluded to above; I'm assuming that Unity is aware I have an external device and has disabled the 'internal' trackpad).

Still getting used to Unity.  My first impression several months ago was not a good one.  But now that I have a new laptop with Unity as the default, I'm getting used to, and appreciating some of, the features.  Still favor KDE at the moment but I used to favor Gnome before KDE so at least I know I can change my ways from time-to-time.  ;-)

Thanks again!

---

### Post by HunkirDowne on 2012-02-13
**_Laptop_: System76 Gazelle Professional (gazp6) running *Ubuntu 11.10 64-bit*.**

> **HunkirDowne said:**
> [QUOTE=smarmytime;11677483](The touchpad) would lock when I would hold the shift key down for 8 seconds (the left one...it's a habit when I pause for thought when I'm typing), and it would unlock when I would hold the same key down, for the same amount of time.

My 'problem' is that I wanted to disable the touchpad for an extended period of time and think this just might do the trick.[/QUOTE]

No joy on locking out the touchpad.  Tried holding down both shift keys (separately, tried the left one first as per above) and the touchpad was still active.

Incidentally, as I write this the touchpad is locked out somehow and I don't know why unless there is a significant delay in using the left shift key as a lockout mechanism.  I do have (as per default configuration) the touchpad disabled while typing, but would expect that after several seconds of no keyboard activity that the touchpad would resume.  This happened to me yesterday afternoon and my solution was to plug in my external pointing device via USB and all was well, or at least I thought it was.  I even thought that the touchpad had been disabled by me plugging in the USB device but at this time I question the validity of my earlier assumption.  I think this may be an issue for me as well as I do not always have an external device handy.

<*time lapse while I found and plugged in my external input devices*>

I now have pointing device capability via only my external.  I will do further testing by unchecking the disable while typing setting as well as booting from a liveCD (other than Ubuntu) to try to narrow down if this is a hardward or GUI issue.  But this will take some time and may not even happen today.

---

### Post by isantop on 2012-02-13
If you want to disable the touchpad, our laptops actually feature a toggle hotkey. Simply press Fn+F1 and the touchpad will be turned off. Press it once more to re-enable it.

---

### Post by isaacullah on 2012-04-10
Hi all,

   I'm just checking back in on this thread after a couple of months dealing with this problem. In that time I have been able to gain a fuller understanding of the bug, and what triggers it, and thus have been able to "dial in" my work around so that it works better. First off, "mousetweaks" DEFINITELY makes this bug more rampant, but uninstalling it DOES NOT fully banish the bug. Here are some things that I have noticed about this bug: 1) it ALWAYS appears on first login after boot up. 2) Hard restart of X-server usually works the first time, but may need to be repeated multiple times before normal mouse activity resumes. 3) Once normal mouse behavior is attained, it can revert to the "unclcikable" state due to what I term "mouse confusion". 4) "mouse confusion is ALMOST ALWAYS cased by you inadvertently touching the touchpad while using your wireless mouse (e.g., while typing or something). 5) You will notice this "mouse confusion" because it will seem like the mouse is "stuck" in a left click (moving the mouse around automatically highlights or selects things, and you can't "unclick" with the external mouse). 6) Once the mouse is "confused", you have to hard-restart the X-server again.

So.... Since touching the touchpad is main thing that triggers the bug, the simple solution I have found is to simply TURN THE TOUCHPAD off while using an external mouse. I use the convenient hotkey built into all Sys76 laptops (Fn-F1) to do so. NOTE: you will still have to restart the X-server after the first log-in after boot up. Loging off and logging back in normally will not work! A hard reset is needed (Ctrl-Alt-Backspace).

If I follow those two simple rules, I can use my computer normally for as long as I want... Note that if you put your laptop into suspend (e.g., close the lid), your touchpad will be enabled automatically upon restore. Remember to disable it again.

Hope this helps anyone else out there still experiencing this bug!):P

---

