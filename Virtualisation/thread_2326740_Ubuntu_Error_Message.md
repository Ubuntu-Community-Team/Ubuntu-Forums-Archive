---
title: "Ubuntu Error Message"
date: 2016-06-04
forum: Virtualisation
---

### Post by michael_oconnor2 on 2016-06-04
Hello, I am trying to use Ubunto 14.04.4 on my Windows 10 computer via Virtual Box.

However, I get this message upon loading it up.  I am still able to eventually get to the screen where I input my username and password.  However, after that I am sent to the main Ubunto desktop page BUT it is simply a blank-mauve screen with no icons or desktop features of any sort.  

[ATTACH=CONFIG]269428[/ATTACH]

---

### Post by oldrocker99 on 2016-06-04
Try removing that virtual directory and reinstalling.

---

### Post by michael_oconnor2 on 2016-06-04
I honestly have no idea how to remove a virtual directory.  
I have been at this quite some time, and I was just looking into something regarding "Hyper-V" which may be causing a problem.  
Not sure if that is related, but hyper-v didnt seem to exist on my computer, but was evidently found in the logs for my virtual machine.

---

### Post by cariboo on 2016-06-04
It looks like you used LVM when you installed Ubuntu. You don't really need it in a vm, unless you are experimenting with it. It's probably quicker to do an install without LVM then it is for you to fix the problem. I'd suggest doing a standard installation, then take a snapshot. After doing this, you can experiment all you want, and when you get to a point where you can't fix the vm, you can use the snapshot to start all over again.

---

### Post by howefield on 2016-06-07
Thread moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2016-06-07
Sidenote to answer post #5-- I use LVM in a lot of my VM's. Easy to add a disk image size and expand the logical image footprint on the fly... instead of using an ever dynamic disk that you forget about how much it can expand to... filling your physical disk and crashing your system. Or run out of fixed sized disk and have to recreate as a larger image (offline).

Virtual hosts are like physical's. Up-time is important.

Answering the OP, Hyper-V and VirtualBox do not play well together. In fact, Hyper-V does not play well with "any" other hypervisor. It binds to the OS and will shield the CPU vierualization away from any other hypervsior, resulting in the other hypervsiors seeing it as not vt-x capable. (it takes over.)

---

