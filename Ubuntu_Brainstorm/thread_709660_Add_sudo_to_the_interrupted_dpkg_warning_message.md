---
title: "Add sudo to the interrupted dpkg warning message"
date: 2008-02-27
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2008-02-27
How many times have you seen a new user post that they received an error message and don't know what to do? The error message is ```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
``` and then a few veteran users swoop in and say to type or paste in ```
sudo dpkg --configure -a
``` Wouldn't it help if the error message told you in the beginning to use *sudo* instead of having you look online to know to add that first bit?

---

### Post by 23meg on 2008-02-27
[QUOTE=aysiu]Wouldn't it help if the error message told you in the beginning to use sudo instead of having you look online to know to add that first bit?[/QUOTE]

It would, but another question would be whether this is good to do policy-wise. Would you assert that the same should be done for every command that needs to be run as root? And if not, why should this be an exception?

---

### Post by aysiu on 2008-02-27
> **23meg said:**
> It would, but another question would be whether this is good to do policy-wise. Would you assert that the same should be done for every command that needs to be run as root? And if not, why should this be an exception?
I would, actually, assert that it should be done for every command that requires root access and appears in an error message.

This one, however, seems to be the most common.

---

### Post by aysiu on 2008-07-31
In case anyone cares, I've added this to Brainstorm:
[Idea #11690: Include proper instructions if dpkg is interrupted](http://brainstorm.ubuntu.com/idea/11690/)

I like [Idea #2298: Automatic reparation of interrupted dpkg](http://brainstorm.ubuntu.com/idea/2298/) better, but my proposal is a bit easier to fix, so I'm hoping it'll be implemented before an automatic reparation is.

---

