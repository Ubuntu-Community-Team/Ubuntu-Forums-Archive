---
title: "Computer won't start up"
date: 2009-01-20
forum: The Cafe
---

### Post by NintendoTogepi on 2009-01-20
I posted this in General Help but no responses.

Okay, so I was using my older testing computer, and I was setting up another installation of Ubuntu mini. I finish it up, etc. 

Now the computer won't start up, it just takes me to a screen saying
```

GRUB Loading stage1.5.

GRUB Loading, please wait...

Error 22
```

Any idea what the problem is or if it is fixable?

I don't care if this computer becomes permanently unusable as it's an old computer of mine that I mainly use for Linux and testing.

Right now I'm using the "broken" computer - running on a DSL Live CD. 

So, if anyone knows, I'd appreciate it. Once again, no urgency. If I am told "It is unfixable", my reaction is "Oh well, I'll have to pick up a new testing computer. Can you tell me why it broke so I can avoid the mistake again? :)"

---

### Post by OutOfReach on 2009-01-20
Yes it is fixable from a LiveCD.

I am positive that Error 22 is when GRUB cannot find one of the partitions listed in the menu. (correct if I'm wrong).

---

### Post by smartboyathome on 2009-01-20
You need to install GRUB again. It says that because it can't find itself anymore. I don't know if this works in DSL, but try it anyway.
```
grub
root (hd*a*,*b*)
setup (hd*a*)
```
Replace a with 0, 1, etc depending on where your hard disk is (if it is sda, it would be 0, sdb, 1, etc). Replace b with partition number (sda1 is 0, sda2 is 1, etc)

---

