---
title: "VMware Workstation 6.5.5 (64-bit) on Ubuntu 10.04 LTS  (64-bit)"
date: 2011-01-12
forum: Virtualisation
---

### Post by android-eve on 2011-01-12
Thanks to [a great thread in this forum]("http://ubuntuforums.org/showthread.php?p=9383204#post9383204"), I managed to successfully install VMware Workstation 6.5.5 (64-bit) on my Ubuntu 10.04 LTS  (64-bit), as outlined in the steps described in [this post]("http://www.linuxquestions.org/questions/linux-virtualization-90/vmware-workstation-6-5-5-on-ubuntu-10-04-install-freezes-854709/#post4218918").

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

### Post by Skilly on 2011-02-24
Does this help: [http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html]("http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html")?

---

