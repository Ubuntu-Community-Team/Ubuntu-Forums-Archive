---
title: "&quot;Mount anyway&quot; button on NTFS disk mount error"
date: 2009-01-03
forum: Ubuntu Brainstorm
---

### Post by enz1m3 on 2009-01-03
Hey there, I posted this idea on Ubuntu Brainstorm and it's getting positive feedback in there, I'd like to know what do you guys think and, if possible give your honest opinion about it in there.

The link is here: [http://brainstorm.ubuntu.com/idea/17020/](http://brainstorm.ubuntu.com/idea/17020/)

Here's a copy/paste:

A great feature that I believe should be implemented in order to save some time and headaches to new (and old) Ubuntu users, is a "mount anyway" button on the popup you can see when the event described below happens.

Event: That error shows up when you connect a pen drive or disk drive which wasn't properly disconnected from a Windows computer.

The current solution is only to use force the mount using console.

This "mount anyway" button should be something warning the user some data could be lost, but it should use the force option, even if it means asking for sudo password (if not needed, better).

(I'm sorry I don't have an image to attach, but I don't have any Windows system near me right now...)

---

### Post by enz1m3 on 2009-01-04
There seemed to be an idea regarding this already, but I believe my solution is better.

[http://brainstorm.ubuntu.com/idea/4994/](http://brainstorm.ubuntu.com/idea/4994/)

---

### Post by blazemore on 2009-01-05
I think the best solution would be to have a dialogue box (Or a fancy new notification!)

"Mounting /mountpoint has failed. This could be due to a corrupt filesystem. Would you like to force a mount?
[Yes][No][Always][Never][More Info]

---

### Post by enz1m3 on 2009-01-05
Even better ;)

---

### Post by marshall.robert on 2009-01-06
> **blazemore said:**
> I think the best solution would be to have a dialogue box (Or a fancy new notification!)

"Mounting /mountpoint has failed. This could be due to a corrupt filesystem. Would you like to force a mount?
[Yes][No][Always][Never][More Info]

I would be very much in support of this method. But any "mount anyway" solution would be greatly appreciated!

---

### Post by bunty on 2009-01-06
No, I don't agree. This is just inviting users to screw up thier fs. This will ultimately be blamed on linux.

Your average Joe will just go "yes" , probably without even reading what was in the message.

Until ntfs-3g has a fsck this must be NO. 

At least making the user open a terminal means he has to actually stop and think.

Yes it's a pain , but the solution to that is correctly remove the drive in the first place. I see no interest in helping users screw up thier file system using linux.

---

### Post by enz1m3 on 2009-01-07
I think you're over-reacting.

I've seen many users screw up their file system on windows alone.

I've never seen it happen on linux though (with force).

I agree ntfs-3g should have fsck, but still I think this should be implemented.

---

### Post by Progressive on 2009-01-07
This was a major annoyance for me recently. Get this problem fixed and provide a Mount Anyway until it is. Make the warning red or something, sheesh

---

### Post by 3rdalbum on 2009-01-07
> **blazemore said:**
> I think the best solution would be to have a dialogue box (Or a fancy new notification!)

"Mounting /mountpoint has failed. This could be due to a corrupt filesystem. Would you like to force a mount?
[Yes][No][Always][Never][More Info]

Having five buttons in a dialog probably breaks the Gnome HIG, and it certainly means a lot of cognitive dissonence ("There's so many buttons... which one is the right one?"). The language is too technical for Gnome.

Better solution:
"The device <HAL device name> was unsafely removed from the last computer, or it may be corrupted. Always use the "Eject" or "Safely remove hardware" function of your operating system before unplugging storage devices, or it could lead to data corruption.

Do you want to try using <HAL device name> anyway?"
[OK] [Cancel]

It teaches the user, doesn't overwhelm them with technical language (no Windows users know the word "mount") or options, and doesn't scare them with what is generally a safe procedure.

---

### Post by enz1m3 on 2009-01-07
> **3rdalbum said:**
> Having five buttons in a dialog probably breaks the Gnome HIG, and it certainly means a lot of cognitive dissonence ("There's so many buttons... which one is the right one?"). The language is too technical for Gnome.

Better solution:
"The device <HAL device name> was unsafely removed from the last computer, or it may be corrupted. Always use the "Eject" or "Safely remove hardware" function of your operating system before unplugging storage devices, or it could lead to data corruption.

Do you want to try using <HAL device name> anyway?"
[OK] [Cancel]

It teaches the user, doesn't overwhelm them with technical language (no Windows users know the word "mount") or options, and doesn't scare them with what is generally a safe procedure.
Best solution until now

---

