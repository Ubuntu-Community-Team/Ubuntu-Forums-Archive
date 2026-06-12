---
title: "synaptic"
date: 2009-04-15
forum: The Cafe
---

### Post by davo11 on 2009-04-15
just wondering, does anyone find it annoying how only one synaptic process can run at a time? this is one of my only issues with ubuntu even though it is not vital.
is there a way to get >1 process working at a time?
and if not will a way be created in a later release?

---

### Post by Skripka on 2009-04-15
> **davo11 said:**
> just wondering, does anyone find it annoying how only one synaptic process can run at a time? this is one of my only issues with ubuntu even though it is not vital.
is there a way to get >1 process working at a time?
and if not will a way be created in a later release?

What would be the point in running more than one?

---

### Post by swoll1980 on 2009-04-15
> **Skripka said:**
> What would be the point in running more than one?

Yeah that's a mystery for me to too. Some people complain for the sake of it I think. Apt locks when you run synaptic. If you were able to run 2 at a time it could become corrupted.

---

### Post by SunnyRabbiera on 2009-04-15
Its more of an issue with apt, then synaptic.

---

### Post by davo11 on 2009-04-15
well no, what i'm getting at, is wanting to eg - run updates and get new apps. it's not a big thing just would be useful

---

### Post by Ozor Mox on 2009-04-15
If apt let you do that the packages would probably get pretty messed up. Surely it is just easier to let one action complete before you run the next?

---

### Post by Skripka on 2009-04-15
> **davo11 said:**
> well no, what i'm getting at, is wanting to eg - run updates and get new apps. it's not a big thing just would be useful

With dependencies as they are-it is a bad idea...also, unless you're paying lots of $$$$ for bandwidth, odds are you'll max out your internet connection with your 1st insance of Synaptic...so you won't gain anything with a second instance.


On Arch, there's a manner of bypassing the lock on Pacman, and permitting more simultaneous instances....don't know if there is a way for Apt though.

---

### Post by spupy on 2009-04-15
> **Skripka said:**
> What would be the point in running more than one?

An easy way to mess up your packages database. Or to get conflicts while installing packages. Or else.

Strange thing is, Gentoo's package manager - portage, allows simultaneous installations. Although I've never tried it.

---

### Post by skymera on 2009-04-15
I like the fact it locks.
You know EXACTLY what apt is doing.

It's similar to Windows, you can;t run 2 Windows installer packages at the same time.

---

### Post by FuturePilot on 2009-04-15
Like others have said, I'm not sure what the point would be of running 2 instances of the package manager. But it's not a [s]problem[/s] feature of just Synaptic. It works this way with any package manager whether it be APT, YUM, Zypper etc. Even on Windows you can't install 2 things at once that use the same installer.

---

### Post by dragos240 on 2009-04-15
It never really bugged me, I always felt content to wait, although yeah, it would be annoying if I was installing many programs.

---

### Post by CraigPaleo on 2009-04-15
It doesn't really bother me. I just check off everything I need and do it all in one session.

---

