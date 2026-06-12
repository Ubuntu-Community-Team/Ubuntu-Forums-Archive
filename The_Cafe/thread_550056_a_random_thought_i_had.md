---
title: "a random thought i had"
date: 2007-09-13
forum: The Cafe
---

### Post by Choad on 2007-09-13
tell me if it's already there, but i think there should be a system built in to the linux kernel, or at least somewhere very low level, that carries messages intended for the user to see. so whether the user is using a command line, or is using a gui, the message pops up. now there are many terminal type things and there are many guis, so it would have to be a case of the guis and the clis writing hooks to receive the generic information output by the message system.

now, this may sound pointless, but it would be a very neat feature. remember, linux is supposed to be the best! i know gnome for example gives you many error messages for many things (not meaning it's badly coded, you know what i mean) but i find that a lot of the time something has happened that i as a user should very well be made aware of, and yet nothing has apparently happened because i was given no feedback.

read/write permissions, disk busy errors, other hardware errors, driver not loaded for hardware etc. etc. could all be taken care of, that leaves the gui dev's to think about the gui errors alone, and then incorporate a way of sending the message the kernal system gives in the same manner so they all look the same.

think about it.... it would be a very good step :D

---

### Post by az on 2007-09-13
> **Choad said:**
> tell me if it's already there, but i think there should be a system built in to the linux kernel, or at least somewhere very low level, that carries messages intended for the user to see. so whether the user is using a command line, or is using a gui, the message pops up. now there are many terminal type things and there are many guis, so it would have to be a case of the guis and the clis writing hooks to receive the generic information output by the message system.

now, this may sound pointless, but it would be a very neat feature. remember, linux is supposed to be the best! i know gnome for example gives you many error messages for many things (not meaning it's badly coded, you know what i mean) but i find that a lot of the time something has happened that i as a user should very well be made aware of, and yet nothing has apparently happened because i was given no feedback.

read/write permissions, disk busy errors, other hardware errors, driver not loaded for hardware etc. etc. could all be taken care of, that leaves the gui dev's to think about the gui errors alone, and then incorporate a way of sending the message the kernal system gives in the same manner so they all look the same.

think about it.... it would be a very good step :D
tail -f /var/log/messages

---

### Post by Choad on 2007-09-13
cool. why the **** don't these get reported to me at least once? why do i have to enter a terminal to read them? i know... the devs can't do everything at once but it would be nice. who knows maybe ill learn c and add to gnome? probably not...

---

### Post by Officer Dibble on 2007-09-13
Personally I feel it is good that these messages are tucked away somewhere for when they are needed.

Windows has something similar to what you describe as well as the 'event viewer'. But they are poorly written and can often cause more problems than the problem they are reporting.

Those error messages should only be there for those who can do something about them, someone looking behind the symptoms of a problem.

---

### Post by 23meg on 2007-09-13
> **Choad said:**
> cool. why the **** don't these get reported to me at least once? why do i have to enter a terminal to read them? i know... the devs can't do everything at once but it would be nice. who knows maybe ill learn c and add to gnome? probably not...

System / Administration / System Log

---

### Post by FuturePilot on 2007-09-13
> **23meg said:**
> System / Administration / System Log

what he said^ 

I think you could also set up conky to relay these system messages.

---

### Post by bobbocanfly on 2007-09-13
If you really are that bothered hack your own kernel or write a daemon to grab messages from the system log and create a Window with it in. Im sure it wouldnt be that difficult. Hell if you werent worried about performance get a Bash script in an infinite loop that shows Zenity windows when a new error is written to the syslog.

---

### Post by saulgoode on 2007-09-13
What you suggest is already possible. Messages can be sent to all users with 'wall' command (or to a specific user with 'write'). The message will appear on all terminals and should produce a pop-up in your GUI if you have a notification daemon running.

---

