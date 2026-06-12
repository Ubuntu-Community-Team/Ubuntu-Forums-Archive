---
title: "virtualbox"
date: 2014-01-13
forum: Virtualisation
---

### Post by ML7rcEx on 2014-01-13
I have been told that it is safer to run a Linux distro in VirtualBox rather than installing to the harddrive? Is this true?

---

### Post by TheFu on 2014-01-13
It depends.

It depends on your skill with boot records, boot management, partitioning, virtualization, and whether the PC running virtualization has enough CPU, RAM, networking, is setup efficiently, and on the specific workload run on it. Virtualization can suck.

OTOH, virtualization will hide unsupported hardware so it may be a great solution on brand new laptops with unsupported devices like wifi chips and other proprietary hardware.

So ... it depends is the only answer.

**Update:**  Reading the above response doesn't convey my love of virtualization.  To clarify, if you do have the right CPU, RAM, disk resources, virtualized OSes can be **fantastic**. I've been running my primary desktop inside a VM for about 6 yrs with my desktop residing in a private cloud the last 2 yrs. It runs under KVM and I use NX to connect with it from anywhere in the world or 2 feet away. It isn't perfect - video and audio playback aren't very useful, but when there are many other reasons for doing it that more than make up for the slight inconvenience. 

Virtualization ROCKS - desktops are good, but for servers is it GREAT!

---

### Post by andrew.46 on 2014-01-14
> **ML7rcEx said:**
> I have been told that it is safer to run a Linux distro in VirtualBox rather than installing to the harddrive? Is this true?

Perhaps safer but it is a good idea to have plenty of resources to throw at your virtual machine otherwise the experience can be a little suboptimal...

---

### Post by deadflowr on 2014-01-14
> **ML7rcEx said:**
> I have been told that it is safer to run a Linux distro in VirtualBox rather than installing to the harddrive? Is this true?

No. It's more convenient.
Running a distro through virtualbox, or any other vm, makes it easier to quickly shutdown, without affecting your main systems functionality.
So even if a problem happens on the vm it shouldn't overtly affect your main stuff.
You can exit or even delete a distro in a vm without problems on the host system.

---

### Post by newbie-user on 2014-01-15
It really depends on what you mean by "safer". For me, I like the convenience of not having to worry about hardware. If my vm host goes down due to hardware failure, I just build a new one and transfer the VMs there. Easy peasy. The VMs don't care what hardware is being used for the host.

---

### Post by punkboy22 on 2014-01-15
i agree with you guys VM's are alot more convenent for running a distro especially if you dont know how it will react with what your going to be tossing its way. this way if it does go to poo you just delete and start new just take notes on what you did to make it die so you dont do it again had that happen alot.. i right now currently use a windows computer at work but have mostly linux servers so i have a VM of Fedora 19 and Ubuntu 13.04 to test our open view assignments.

---

