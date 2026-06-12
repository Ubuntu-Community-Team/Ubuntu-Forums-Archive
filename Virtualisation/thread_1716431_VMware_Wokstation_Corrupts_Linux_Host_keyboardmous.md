---
title: "VMware Wokstation Corrupts Linux Host keyboard/mouse"
date: 2011-03-28
forum: Virtualisation
---

### Post by mpp123 on 2011-03-28
Hi Everyone,


I have just spent the last 3 weeks working with VMware technical support to find out why my keyboard & mouse became corrupted when I switched from a Virtual Machine (VM) back to my Linux host (HOST).


There seems to be a small bug in the way VM is passing control back to the Linux host if you use CTRL-ALT-ENTER to switch from your VM to your HOST. Moving from your HOST to your VM by using CTRL-ALT-ENTER is not affected by this bug.


The work around from using CTRL-ALT-ENTER to switch from your VM to your HOST is to use:


CTRL-ALT to remove focus from the VM

ALT-TAB to move focus to another application running on the HOST, for example your email or your Linux desktop

Then when focus has been switched to the HOST, you can MOUSE-RIGHT-CLICK on the task bar VM and select Minimize.


The above key strokes allow you to safely switch from your VM back to your HOST without loss of keyboard and mouse functionality. To get back to your VM, just click on the minimized VM in the task bar.


As well, if you are running multiple VM's, you can use ALT-LEFT ARROW or ALT-RIGHT ARROW to switch between VM's without having to go back to the HOST to select the another running VM.


I do hope this tidbit of information is helpful; it has helped me greatly as my HOST's keyboard and mouse are no longer corrupted when I switch back and forth from my VM to my HOST.


VMware technical supported has promised to place this bug on their to-do list. In the mean time, we have a viable work around.


Happy Computing,

mpp

---

### Post by K.Mandla on 2011-03-31
Moved to Virtualization.

---

### Post by ThomasMcA on 2012-01-25
I have the fubar keyboard problem, even using your "solution" to switch between my host (Kubuntu Natty 11.04) and guest (Microcrap Windoze 7) via VMWare Workstation 7.1.5. In other words, that doesn't fix the problem for everyone.

I can fix it by running setxkbmap, but I'm still trying to find a permanent fix.

---

