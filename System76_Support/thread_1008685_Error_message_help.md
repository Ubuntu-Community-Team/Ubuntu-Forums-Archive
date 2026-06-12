---
title: "Error message help"
date: 2008-12-11
forum: System76 Support
---

### Post by Crispus K on 2008-12-11
I've had my pangolin performance for about 3 weeks now and haven't experienced any problems until the last few days.

 
Basically the system crashes if i enter hibernate or suspend mode - the screen goes black and it spits out error messages.  I also can't open some programs such as synaptic or firestarter.


Things i've recently done on the computer include installation of software (firestarter, bulk name, dvd::rip), i've ripped a DVD using dvd::rip, and created a new user for the system.

When I try to open synaptic i get this error message:

[I]"Failed to run /user/sbin/synaptic as user root.  Unable to copy the user's xauthorization file." 
[/I]

I tried to uninstall firestarted but it wont let me and i get the following message:

 [I]"Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '-o' 'Synaptic::closeZvt=true' '--parent-window-id' '58720259' '--set-selections-file' '/home/crispus/tmp6a9hUs' as user root.

Unable to copy the user's Xauthorization file."[/I]

When I go into hibernate mode the computer appears to crash and the following error message appears over and over again
[I]
[271931.225061] bad: scheduling from the idle thread!-[/I]

then after a bunch of lines of that it says

[I]-End_request: I/O error, dev srO, sector 8458244
-Buffer I/O error on device srO logical block 2114561.  [/I]

A buddy at work said this probably has something to do with difficulty reading the dvd drive but im not so sure because i removed the DVD that was in the comp and im still getting these errors.

I know i must have done something but i have no idea what or how to fix the problem.  This is only my third week running ubuntu.

Any help would be very much appreciated!  I sincerely hope I haven't already messed up this comp...

i am running ubuntu 8.10 on a 3 week old pangolin performance. Intel(R) Core(TM)2 Duo CPU P8600  @ 2.40GHz. Not sure where to get my model number.I haven't tried much other than restarting, removign that dvd and attempting to uninstall some recently installed software.

---

### Post by EnderEcho on 2008-12-11
Did you try reinstalling the system76 drivers or restoring your system to before the problem began?

---

### Post by Crispus K on 2008-12-11
No, but only because I don't know the correct way to do so.

---

### Post by jdb on 2008-12-11
> **Crispus K said:**
> 

"Failed to run /user/sbin/synaptic as user root.  Unable to copy the user's xauthorization file." 


"Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '-o' 'Synaptic::closeZvt=true' '--parent-window-id' '58720259' '--set-selections-file' '/home/crispus/tmp6a9hUs' as user root.


These two errors look kind of like SUID problems.

Some executable files that have root ownership have a bit set that causes them to have root permissions when they are run, it's called SUID (Set User IDentification).
Not many files have this because it can cause security problems, but it is neccessary for a few.

If the ownership of such a file is changed it will lose it's SUID status, even if the ownership is changed back.

It's not hard to set a file back to SUID, but it's hard to know which files to do it to.

The last time I had a problem like that I ended up reloading from a backup.
I hope someone here has a better answer :(

jdb

---

### Post by Crispus K on 2008-12-11
I went ahead and reinstalled the factory settings.  That seems to have solved all the problems.  Consider this thread closed for now.

---

