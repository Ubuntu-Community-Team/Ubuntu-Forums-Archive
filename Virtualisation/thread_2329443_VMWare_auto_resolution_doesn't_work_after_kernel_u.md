---
title: "VMWare auto resolution doesn't work after kernel upgrade."
date: 2016-07-01
forum: Virtualisation
---

### Post by Dustin Wyatt on 2016-07-01
I cannot say for sure that getting latest kernel from apt-get was the cause of this issue because the VM hasn't been shut down in awhile, but anyway...

I can no longer click the full screen button and have the VM go to full screen.  It just stays at 1360x768 in the middle of the screen.

I tried uninstalling VMWare Tools, rebooting, installing open-vm-tools along with open-vm-tools-desktop, rebooting.  The problem persists.

Any suggestions?

14.04 Desktop
VMWare Workstation 12

---

### Post by MAFoElffen on 2016-07-02
Now you are talking about an update on your Ubuntu Host or on your VM?

if on your host, for a test (if it was from a kernel update), on boot, just past the BIOS messages, press the <left-shift>t key intermittently. When the Grub boot menu shows, press the <down-arrow> key to get to the second menu option... Select it to show an older kernel and boot from that. If successful, then that confirms.

I know from experience at Launchpad... The next step if you report the problem to launchpad, they would ask you to go to the kernel mainline ppa and install a mainline kernel (linux kernel with any modification done to it by the Ubuntu Kernel team) of the same version. If that has the same problem, then they can report an upstream bug to kernel.org. If a mainline kernel does not have that same problem, then the Ubuntu Kernel Team knows there was some kind of problem that they are responsible for fixing.

In my way of thinking, if it is a kernel bug, then it would help all of us if you can go through the effort to report it to launchpad as such. It may help to catch further bugs with future kernels.

---

