---
title: "What just happened???"
date: 2011-04-23
forum: Security
---

### Post by Jeff Root on 2011-04-23
Maverick Meerkat 64-bit.  Dial-up Internet connection via
external modem with all the lights.  Firefox 3.6.10.
All automatic updating that I know of is turned off.
  
A few minutes ago I was online, visiting two or three highly
trusted websites.  I was backing out of the last one, only a
single window open, to my home page which is completely inert,
the simplest possible HTML which I made myself, when I saw
that the modem download and upload lights were flashing.
 
I closed Firefox and opened System Monitor.  (I think there
may be a more useful tool than System Monitor to monitor
Internet communications, but I haven't learned what it is
yet, or where to access it, so System Monitor was the best
I could do in a hurry.)
 
I saw that most of the activity was download.  It went on
for one or two minutes.  When it stopped, three of the four
CPU cores began major activity, which lasted 30 seconds to a
minute.  System Monitor was not set to show file activity.
 
After disconnecting, I went into the filesystem and listed
the folders in order of most recently modified.  I found
that the sys and proc folders both had timestamps that were
about 25 minutes in the future!  The sys folder contained
seven folders with timestamps about 25 minutes in the future,
and the proc folder contained 84 such folders.  Most of the
files were zero bytes, but there were hundreds or thousands
of files in total, and I only looked at a handful.  I had to
use the root terminal since Nautilus told me I didn't have
permission to get into those folders.
 
So, what did this, why did it do it, and why did it do it
covertly?
 
   -- Jeff, in Minneapolis

---

### Post by Ryan Dwyer on 2011-04-23
It could have been your computer checking for updates.

It is normal for /proc and /sys to do that. They are not real files. For example, each numbered directory in /proc relates to a process which is currently running. They appear and disappear all the time.

If you get high processor usage in the future, open a terminal and run "top" to see what's happening, then Google the process name to see what it is. Press Q to quit top.

---

### Post by Blasphemist on 2011-04-23
You could also run the sysmonitor screenlet as it lists the top 10 processes as well as other good information.

---

### Post by Jeff Root on 2011-04-30
I thought I had automatic checking for updates and
the like turned off.  I can't find anyplace where it is
turned on.  Where should I look?
 
   -- Jeff, in Minneapolis

---

### Post by Jeff Root on 2011-04-30
Any idea why the sys and proc folders, and many of
the files they contained, had timestamps that were
about 25 minutes later than the then-current time?
 
   -- Jeff, in Minneapolis

---

### Post by Blasphemist on 2011-04-30
First, why turn off updates? Security updates are included. In update manager, settings, updates tab, you can set your preferences including not to check.

Second, I wonder if your pc bios time is correct?

---

### Post by Ryan Dwyer on 2011-04-30
For the updates, go into the Software Centre and go to Edit > Software Sources. On the updates tab, if "Check for updates" is ticked then that could explain the net/processor activity.

Even if it's not ticked, it could have been something else that's running in the background and isn't to be concerned about. You can't be sure what it is until it happens again and you use top or System Monitor to see what's happening.

---

### Post by Jeff Root on 2011-04-30
Huh.  I *thought* I had updates turned off.  I apparently
didn't notice the "Settings" button at the bottom-left of
the Update Manager window, and didn't think to look in
"Software Sources" in the Software Center.
 
The main reason I don't want automatic updates is that I
don't want to stay connected for the week or two it would
take to download all those files.  When I had Windows 98
I kept being told that I should download the updates.
I finally read through the detailed descriptions of dozens
of updates, and only one of them applied to my situation.
That one was of no significance.  Maybe the updates to
Meerkat include something I should have, but my guess is
that they don't.
 
 
If the BIOS time were off by more than a minute, I'd
notice right away.  Looking in the proc directory just
now, the newest files, just created or updated, have the
current time on them.
 
   -- Jeff, in Minneapolis

---

### Post by EGamerHDK on 2011-05-02
Wait wait wait wait wait...


Did you just say "Dial-up Internet"?


I can understand why you would want to turn off automatic updating.

---

### Post by wilee-nilee on 2011-05-02
Go to the startup applications in the menu, and untick the update manager, you will actually gain some memory as well next time you reboot, with it off.

---

### Post by Jeff Root on 2011-05-02
I had already turned off Update Manager in Startup
Applications several weeks ago.  But it wasn't turned
off in the Update Manager Settings.
 
   -- Jeff, in Minneapolis

---

### Post by wilee-nilee on 2011-05-02
> **Jeff Root said:**
> I had already turned off Update Manager in Startup
Applications several weeks ago.  But it wasn't turned
off in the Update Manager Settings.
 
   -- Jeff, in Minneapolis

Right, but if you run it, it is then on, the key is don't run the manager, but use the cli, which may turn it on to not sure really.  But if turning it off in the software sources works better cool baby.

Personally I just have it off to get the lowest memory being used from the startup, all I work with is laptops, so on and off all the time goes the computer.

---

