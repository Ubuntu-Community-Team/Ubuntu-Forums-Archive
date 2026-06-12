---
title: "Ubuntu worm/virus mockup"
date: 2009-03-14
forum: Security
---

### Post by bryonak on 2009-03-14
Just an idea I had while answering in another thread.



Assume that you want to make an Ubuntu specific virus and assume that autostart from USB is generally turned on.
Then you infect the USB stick with a program that starts when the drive is plugged in, but sleeps for 10-20 minutes. After that, it pops up a classical "Update Manager" window (using your current theme), showing some bogus updates and asking you to install them. If you do so and enter your password as usual, it can grab your password and root the system. Of course, it will move the slider as if downloading something and then crank up the CPU usage for a few seconds and emulate the terminal output so you think it's installing. This could actually be used to install a real rootkit.
Then it'll run a daemon detecting any USB drives and infecting those too.

This idea is limited to GNOME, but nothing hinders the virus writer to include a detection check for KDE (and maybe XFCE?) and then pop up those update manager look-a-likes, covering almost all of the desktop population.

That's also a reason why the "pop under" update manager in Jaunty isn't such an awesome idea. But the virus could display the update icon instead of popping up directly after checking whether it's on Jaunty or Hardy/Intrepid as well.

Of course, all this would be limited on the fact that not everyone has autostart on USB turned on. But the idea can be used in many other cases (emails with a fun little program), the payload stays the same.
There is little to prevent social engineering from making non-technical users (parents are the classical example) run such programs. "Here's a new screensaver, just run it. It's not dangerous since it doesn't ask your password" or something less lame ;)
The important thing is the waiting period (which could be set randomly between 10 and 30 minutes), so the act of plugging in a drive or running a file doesn't appear connected to the update manager.

Someone should write a proof of concept.

---

### Post by mikewhatever on 2009-03-14
I purchased a USB Western Digital external HDD not long ago. It had one ntfs partition and, as it turned out, some autorun software by the company. When first plugged in, a window appeared saying something similar to 'Software from this device is trying to run', with Allow and Deny buttons. Needless to say such a message should turn on a red alert, so it's not that simple.
That said, social engineering has been discussed to death here, with the general consensus that any OS is vulnerable to the uses' ignorance. The discussions included some rather complex infection vectors, such as transferring malware from the Windows partition. I guess the more complex it is, the more attention it draws, no matter how improbable it really is.

---

