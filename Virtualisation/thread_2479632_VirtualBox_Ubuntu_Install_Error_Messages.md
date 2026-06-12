---
title: "VirtualBox Ubuntu Install Error Messages"
date: 2022-09-30
forum: Virtualisation
---

### Post by ebryski on 2022-09-30
I'm attempting to install Ubuntu on VirtualBox. (My PC's OS is Windows 10). After it installed, the following error messages appeared:

"mtd device must be supplied (device name is empty)"
"*ERROR* Failed to send host log message"

When I searched these messages, the general response was that they're bugs. However, it's frozen on this screen.

Does anyone have ideas on how to resolve it?

Thank you!

---

### Post by ajgreeny on 2022-10-01
Moved to **Virtualisation** which is a better fit for this question.

---

### Post by MAFoElffen on 2022-10-01
Installing Ubuntu in VirtualBox is usually a given.

That error is a bug, but (usually) does not prevent it from booting. I have 2 machines (metal) that have those error messages and still boot. The error just means that a file is not empty during boot, which then prompts that message. More of a nuisance.

What is the host machine and OS? What is the version of VirtualBox? What version of Ubuntu are you trying to install?

---

### Post by &amp;KyT$0P# on 2022-10-01
In addition to MAFoElffen's questions, do you see something more informative if you open the GRUB menu at VM startup and boot its Ubuntu without [FONT=Courier New]quiet splash[/FONT] boot parameters?

---

### Post by MAFoElffen on 2022-10-01
Meaning... If, Press <Esc> after the Bios Post messages, at the Grub2 boot menu, press the <E> key. <Arrow-down> to the line that starts with "linux". <Arrow-right> and delete the words "quiet splash". Then press <Cntrl><X> to boot...

More details on this about mid-post in my "Graphics Resolution" sticky in my signature line...

---

### Post by TheFu on 2022-10-01
> **MAFoElffen said:**
>  
What is the host machine and OS? What is the version of VirtualBox? What version of Ubuntu are you trying to install?

In the OP, he says Win10 is the hostOS. Are there different versions of that?

Don't see any mention of the vbox version or which Ubuntu release and DE/flavor.  

I put the error message into google and hit enter. Found this: [https://askubuntu.com/questions/1417618/mtd-device-must-be-supplied-device-name-is-empty](https://askubuntu.com/questions/1417618/mtd-device-must-be-supplied-device-name-is-empty)  Which says it has something to do with systemd and that it has been fixed.

For someone new, perhaps 22.04 isn't the best release. There are a number of things that are odd in it as Canonical uses the "defaults" to get more testers.

---

### Post by MAFoElffen on 2022-10-01
The error message is a sideline issue, not to be confused with not booting (which that bug report states that.)

@TheFu - I saw that bug report ([https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622)) about a couple weeks ago, when my laptop was still giving that message. The bug (in the details near the end, most recent) says it was patched for 22.10 DEV. Not backported to 22.04 (yet)...

EDIT: Don't do the "work-around" that was suggested there. It is a two edged sword. They said that you have to back off that work-around, for the new patch to work... Meaning if you did that work-around, and you get the update with that patch, that it will prevent the patch from being applied... Which I will need to back-off on one of my systems when it gets backported to 22.04 LTS....

I am part of that Bug Report. I notice that besides me, it also affects oldfred.

---

### Post by TheFu on 2022-10-01
If I'm reading that bug correctly, they are just messages and safely ignored.  In the old mainframe days, we called them "standard errors", meaning that if the error wasn't there, it was a problem.

Is this for all hypervisors or just vbox?  
Also, seems to be for 22.04, not 18.04 or 20.04.

---

### Post by ajgreeny on 2022-10-02
It's  also showing that error when I boot my VMs of Xubuntu 22.10 and 22.04, both running in KVM/QEMU, so it's not just in VBox.

---

### Post by MAFoElffen on 2022-10-02
That's what I told TheFu in PM. Both for KVM and RHEV. 

But I have an EUFI Laptop (metal) and a Legacy Boot workstation (metal) that are hypervisors that have this error. Their 22.4 & plus guests have this error...

oldfred's is on metal and is not a hypervisor... So not just hypervisor's. I've talked to him about possibly running VM's and he doesn't run any.

---

