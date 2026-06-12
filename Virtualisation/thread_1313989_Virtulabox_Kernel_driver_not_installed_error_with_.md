---
title: "Virtulabox Kernel driver not installed error with Karmic 9.10"
date: 2009-11-04
forum: Virtualisation
---

### Post by ricardo.gloe on 2009-11-04
I have just installed Karmic 9.10, and VirtualBox 3.0 from the Sun repository. Everytime I want to run a wm the first time I'v just turned on my computer, I get this message (see attachment).

I run the command and then it works fine, but how do I fix the problem permanently? 

I've already tried uninstalling and re-installing using synaptic, I have the dkms package installed I've tried running VirtualBox from the terminal, used sudo, and still get this problem every first time I try to run a vm when I turn on the computer.

---

### Post by ricardo.gloe on 2009-11-06
I have tried most of the solutions I found on the internet, but none have solved the problem. Uninstalling and reinstalling dkms, virtualbox, tried virtualbox-ose (same problem). 

The vbox usergroup includes me and root, I'v even tried changing ownership to user instead of root, to no avail. 

The interesting things is the command to recompile the kernel works, it just isn't permanent (next boot, same problem), so does that mean dkms is not keeping track of kernel changes?

---

### Post by ricardo.gloe on 2009-11-06
Found a solution after much searching. 

included "vboxdrv" in the /etc/modules file and VB kernel is loading on boot and the error isn't happening again.

---

### Post by b0b138 on 2009-11-10
sweet... just the answer I was looking for!   :guitar:

---

### Post by nisith on 2011-03-01
Did the trick for me on Lucid as well.
You are awesome...

---

