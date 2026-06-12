---
title: "Problem installing Pop-OS on Virtualbox and Vmware"
date: 2021-07-03
forum: System76 Support
---

### Post by sergemenardmaynard on 2021-07-03
Hi! How are You? Me having big headaches, been worming all day installing the new and exciting Pop-OS 21.04, but with no avail with both Virtualbox and VMware, it goes well, and I see the beautiful desktop and the installer shows up and all of a sudden after twenty seconds or so, the system reboots again, and it is say there is a job running and when all that page is finished, there is the cursor blinking, and it says "Finished running utmp(or something like that), then the system and Pop-OS is dead, there is nothing going, I tried with both the Intel and NVIDIA, all the same thing and I installed VMware and thought it would do the trick, but with no avail. What is the problem and is there something that I can do, or let's say We can do, I am using Windows 7 as my main computer and very basic drivers like Realtek and all, and I did a sfc scanow on Windows 7 to try to fix bugs and still did nothing. Please help me, because I am starting to lose my mind. Thank You for Your Attention and Collaboration and Patience with all this. Take good care and have a nice day and keep up the good work and vocation. My Computer is a Lenovo ThinkStation from 9 years ago(around there), it was an industrial computer used to control a saw mill.

---

### Post by TheFu on 2021-07-04
Support for Win7 ended over a year ago.  Don't expect VMware Workstation/player or Virtualbox to support it.  You might be able to find an older release of those tools will work, but don't expect them to work with newer Linux releases (any after the hypervisor release time).

BTW, never have more than 1 hypervisor installed on a system at the same time, unless you are an expert.

Have you considered swapping the OSes?  Running Ubuntu/PopOS on the physical hardware and putting Windows-whatever into a virtual machine?  Then you can use KVM + libvirt + virt-manager.  FLOSS hypervisors aren't nearly as picky as closed source non-GPL hypervisors, so newer/older OSes usually work.  Of course, this is a big decision.

These days, the only uses for a Windows7 system is to freeze time (never add/remove anything) or to have a hacking testbed available.

---

