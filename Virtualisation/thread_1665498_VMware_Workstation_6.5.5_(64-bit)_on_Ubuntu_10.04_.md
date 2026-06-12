---
title: "VMware Workstation 6.5.5 (64-bit) on Ubuntu 10.04 LTS  (64-bit)"
date: 2011-01-12
forum: Virtualisation
---

### Post by android-eve on 2011-01-12
Thanks to a great thread in this forum, I managed to successfully install VMware Workstation 6.5.5 (64-bit) on my Ubuntu 10.04 LTS  (64-bit).

It works *almost* perfectly, except for an annoying problem, impacting usability:

When the guest VM is Microsoft Windows (2K, XP), the mouse cursor  turn from an arrow to a hand when it hovers over the Task Bar. When the  mouse moves, this hand cursor blinks and the system doesn't respond to  mouse clicks. When the hand cursor blinks, the Num Lock LED on my  keyboard blinks as well.
  

When I move the mouse cursor back to the desktop area, it functions normally.
  

That is, the problem exists only in the Task Bar area.
  

Obviously, this makes it very difficult (read: impossible) for me to use the Start Menu, SysTray and the rest of the Task Bar.
  

My workaround for now is to launch programs via their Desktop shortcuts or via the keyboard.
  

Note: The same exact VMWare Workstation 6.5.5 (64-bit) on Ubuntu 8.04 (64-bit) doesn't exhibit this problem.
  

I am using the so called "Console View", not RDP, and I am interested in solving the problem in Console View.

 
Anyone seen this problem before? Do you know of a solution (or better workaround) to this problem?


Thanks.

---

### Post by Tony.Anderson on 2011-01-12
I am facing the same problem. Can anyone help?

---

### Post by android-eve on 2011-01-12
> **Tony.Anderson said:**
> I am facing the same problem. Can anyone help?
Interesting to see that I am not the only one experiencing this.

In the meanwhile, I discovered another symptom that may help getting a clue as to where the problem lies:

I don't know know what I did exactly (I think I just invoked System > Preferences > Keyboard Shortcuts, but didn't change anything there, then closed it) but now everything seems to **work fine**!

Is the system healing itself or what? :)

I know this problem will return as soon as I reboot the system, but this inconsistent behavior may help in troubleshooting this.

---

### Post by android-eve on 2011-01-20
Hmmm... the problem didn't return after reboot in the 2K guest (I really don't know what happened in that 2K guest that made it "heal itself"), but it does exist in all other guests, especially the XP ones, with a new twist/observation:

The problem is not limited to the Task Bar area but rather to an arbitrary margin on the outer side of the desktop. This margin can be as wide as 1/8 of the guest's desktop.

Getting weirder by the second... Can anyone solve this?

---

### Post by android-eve on 2011-01-20
.

---

### Post by android-eve on 2011-01-20
.

---

### Post by android-eve on 2011-01-20
.

---

### Post by android-eve on 2011-08-17
Update: regretfully, the celebration then was too early: The problem did return and till this day I haven't been able to fix it.

---

