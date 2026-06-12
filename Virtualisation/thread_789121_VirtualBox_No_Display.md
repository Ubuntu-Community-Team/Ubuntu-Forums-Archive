---
title: "VirtualBox No Display"
date: 2008-05-10
forum: Virtualisation
---

### Post by thecorleonefamily on 2008-05-10
I am using the latest version of VirtualBox 1.6.0 and trying to run Windows XP on Ubuntu 8.04.

The problem is, there is no display in the virtualization screen. I am trying to install Windows XP and all I see is black. black. However, when I pause the machine, I can see some display -not clear but though it clearly indicates that the virtual machine is running. Even the innotek logo thingy that comes before booting any virtual machine doesn't show, which clearly means that Windows XP is not at fault. I even created a new VM and used a different ISO image but to no avail.

Can anyone please help? I desperately need to run AutoCAD. :(

---

### Post by nanog on 2008-05-10
Same thing here. 1.6 seems to not work with up to date Hardy.

---

### Post by krmolot on 2008-05-11
[http://www.virtualbox.org/ticket/1458](http://www.virtualbox.org/ticket/1458)

---

### Post by buntunub on 2008-10-18
I was having this same issue since Hardy came out and finally, [here]("http://www.virtualbox.org/ticket/2245") is the answer. In a nutshell, [download]("http://www.libsdl.org/") and compile (./configure, make, sudo make install) the latest SDL and that will fix the issue.

---

