---
title: "Why is this an important security update?"
date: 2007-11-15
forum: The Cafe
---

### Post by Thrasyllus on 2007-11-15
Usually I accept whatever upgrades Ubuntu offers when I reboot, but I keep getting bugged about this one. On the update manager it shows up like this: 
 
[I]Important security updates
 
[ ... ]
 
English_american language packet for OpenOffice.org
From version 0.5.4-0ubuntu8.1 to 0.5.4.-0ubuntu8.2[/I]
 
I don't want to use "American" (by which I suppose they mean US) English. Why is this called a security update? Is there any way I can notify whoever that, no thank you, I'm passing this one up and don't want to hear about it again? It's funny, I don't get similar offers to enhance my security with Canadian, Australian, Jamaican, or English English.

I also refused an update with time zone information because I'm afraid of undoing the arrangement I carefully set up whereby my system is always on Universal Time. So these two updates I don't want keep turning up every day... Very annoying. What to do?

---

### Post by Polygon on 2007-11-16
the ubuntu devs arnt stupid, they arnt going to release packages that break stuff (on purpose)...and it has only happened like twice and both have been with binary video drivers.

and i use the thing with the system clock always being set to UTC cuase i have windows, and timezone updates dont effect it. \

and maybe read the description on what the update fixes?

but in all honestly your paranoia on upgrades coming straight from the ubuntu devs is unfounded and unneeded. If you dont trust them, why are you using ubuntu?

---

### Post by -grubby on 2007-11-16
> **Polygon said:**
> the ubuntu devs arnt stupid, they arnt going to release packages that break stuff (on purpose)...and it has only happened like twice and both have been with binary video drivers.

and i use the thing with the system clock always being set to UTC cuase i have windows, and timezone updates dont effect it. \

and maybe read the description on what the update fixes?

but in all honestly your paranoia on upgrades coming straight from the ubuntu devs is unfounded and unneeded. If you dont trust them, why are you using ubuntu?

but how is a language pack a security update?

---

### Post by Polygon on 2007-11-16
i dont know, look in the changes to see what it fixed. It could have some massive bug that allows a exploit to go through or something....but they always changelogs for the updates...

---

### Post by Frak on 2007-11-16
> **nathangrubb said:**
> but how is a language pack a security update?
Some programs can lead access to other resources that could allow intrusion into your system. That includes the most random files.

---

### Post by Shazaam on 2007-11-16
Open Synaptic- highlight the offending update- go to "Package" (at the top)- click "Lock Version". Done. Later, if you have a change of heart, look at the list on the left side, open "Pinned" and you can go to "Package" again to undo.
I wouldn't recommend doing it for security updates though.

---

### Post by Thrasyllus on 2007-11-17
Shazaam, thanks! But I ended up downloading the two updates in question along with the three Samba updates I wanted because that had to be done through a sudo line command (see the thread on the recent 403 Forbidden snafu in this forum), and I just did it zombie-like without thinking. Ah, well. 

Polygon, I would never imagine that they would offer an update that would break anything. Where did you get that idea from my first post?

---

