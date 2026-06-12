---
title: "Ubuntu 20.04 upgrade"
date: 2021-08-16
forum: Virtualisation
---

### Post by scubasteve63 on 2021-08-16
Hi,

I am running Ubuntu 20.04 via Hypervisor on a virtual machine and have tried several times without success to make this update/upgrade. Result is a blank (black) virtual machine screen.

The revert option to a previous checkpoint also doesn't bring me back to a running Ubuntu, before I reinstall everything and choose not to upgrade does anyone have any advice please??

Kind regards,

Scubasteve63

---

### Post by QIII on 2021-08-16
Moved to Virtualisation.

Release upgrades have a set of risks entirely separate from bare metal or virtual machine installations.  If you have the time and inclination -- and you won't wreck any data you may want to keep -- you might try a fresh installation of 20.04.

You could test by spinning up a new VM and seeing how the installation goes before deciding if you want to go that route so you don't utterly destroy what you currently have.

I have 20.04 both on this bare metal machine and several flavors in several KVM VMs.  I always do fresh installs without problems.

---

### Post by monkeybrain20122 on 2021-08-16
Which VM software do you use? KVM, VMware, Virtualbox or others? I don't do "upgrade" usually, but for the heck of it I upgraded a Ubuntu16.04 KVM guest to Ubuntu20.04 with no problem (there maybe hidden problems just like "upgrading" in bare metal but certainly I can boot into it with no problem) What "previous checkpoint" are you talking about?

What is your host?

More info please.

---

### Post by MAFoElffen on 2021-08-16
> **monkeybrain20122 said:**
> 
[LIST=1]
[*]Which VM software do you use? 
[*]What is your host? 
[*]More info please. 
[/LIST]
 
Exactly. Beyond those 3 questions, based on the VM Host flavor...

4. What is the video /display configuration settings for the VM Guest? Do you have Video Acceleration / OpenGL settings enable?

---

### Post by Dennis N on 2021-08-16
For VMs, my upgrade process is:
1) clone the VM.
2) start the clone and upgrade to the new release.
3) if the upgrade is good, delete the originial VM.

---

