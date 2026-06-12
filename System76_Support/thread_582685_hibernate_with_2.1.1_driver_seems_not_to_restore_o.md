---
title: "hibernate with 2.1.1 driver seems not to restore on gazp3"
date: 2007-10-20
forum: System76 Support
---

### Post by tedrampart on 2007-10-20
making a new thread about this because I didn't see one yet.. sorry if its been discussed..

I just updated to the newest driver, 2.1.1 in hopes that I could fix my mic issue.. but it seems like it broke restore.

I think suspend still works, but not hibernate..  when I try restoring after hibernate, it boots up like it would normally would during restore.. but instead of going to my desktop, it goes to the GDM login prompt.

anyone else experiencing this?  I'm going to try replacing the 2.1.1, with 2.1.0 with the .deb file, and see if that fixes it.

---

### Post by tedrampart on 2007-10-20
so I just got home from work, and hibernated before leaving work.. and it restored fine now that the 2.1.0 driver is installed instead of 2.1.1

nothing really to gain from 2.1.1 for the gazp3, so I'll stick to this for now..

just thought I'd share this

---

### Post by tedrampart on 2007-10-21
okay, so I seemed to have jumped the gun on this one..

restore screws up with both versions (2.1.0, 2.1.1) after I hibernate, restore, hibernate then restore again..

I also noticed that when it restores back to the GDM, and I log in, I'm on tty9, instead of tty7 like I normally would be..

---

### Post by thomasaaron on 2007-10-22
Yep. I can confirm this problem with multiple hibernations. We've had difficulty with this one in the past. I'm pretty sure there is a bug report out on it already. When we fix it for one computer, it will probably fix most of them.

---

### Post by tedrampart on 2007-10-22
okay,  hopefully its fixed soon..

do you have the address for the bug report?  I wouldn't mind taking a look to see what others are saying about it in the mean time.

thanks

---

### Post by tedrampart on 2007-10-23
okay, so I just discovered it does the same with suspending.. or atleast suspending after hibernating.. 

it also makes all the tty's completely useless as the screen just jumps around afterwards.. so I can't even go in and try killing gdm and restarting it.. 

kinda sucks for using my extra battery and maintaining a long uptime :(

---

