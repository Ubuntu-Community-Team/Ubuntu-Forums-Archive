---
title: "Is it possible to turn off the automaximize feature in Unity 2d?"
date: 2012-01-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by JRV on 2012-01-30
It's easy in 3d, but I have not been able to find a way to do it in 2d.

I'm running Ubuntu 12.04 64 bit.

---

### Post by mc4man on 2012-01-30
Don't use 2d atm but how about here in gconf-editor?

---

### Post by JRV on 2012-01-30
Thankyou mc4man

I thought gconf-editor had to be run as root, and found the option unchecked.
When I ran it as my user it worked.
I guess I need to learn a bit more about gconf-editor. 
It looks like a very handy utility.

Thread marked solved.

---

### Post by mc4man on 2012-01-30
You should keep in mind that things like gconf, dconf, gsettings,  can set preferences, options,  ect, for root as well as a user.
(they all can & generally should be run as a user

There are a few things that can be advantageous to set as/for root though  best to leave most  at the defaults.

Edit: right now there are settings available  in both gsettings (dconf-editor), & gconf (gconf-editor 

In some cases there can be an overlap , usually then gsettings is the means to set/edit & the similar/same in gconf may not do anything

---

