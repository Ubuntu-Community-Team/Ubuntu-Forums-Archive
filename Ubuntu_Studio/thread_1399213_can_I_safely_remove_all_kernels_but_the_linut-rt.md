---
title: "can I safely remove all kernels but the linut-rt??"
date: 2010-02-05
forum: Ubuntu Studio
---

### Post by extendedping on 2010-02-05
I am running the rt kernel on both my laptop and my home computer now to learn ardour hydrogen etc. I am getting sick of seeing all the clutter on my grub screen. on ununtu 9.10 can I go into synaptic and remove the old kernels? or will that break something. all i need is the kernel-rt I trust it :)

---

### Post by ZO5lFLll on 2010-02-05
If you trust your rt-kernel and it's well tested you may remove all others, though in my opinion the few MB of 'saved' disk space don't outweigh the advantage of having another kernel to boot into as a fallback, just in case... 
I always leave the current stock kernel installed.

---

### Post by cchhrriiss121212 on 2010-02-05
If you just want to remove the clutter then download startup manager. You can choose which kernels you want to display or bypass the grub screen altogether.

---

### Post by trulan on 2010-02-05
You should be able to safely remove the generic kernels.  Then run sudo update-grub and the clutter will be gone.  Some packages will pull a generic kernel as a dependency (even though they don't actually need it), so make sure it isn't removing any other packages.

Personally, I like to keep one generic kernel around on my desktop, but it mostly gets used for playing games as the RT kernel is pretty poor for 3D graphics on my machine.  

If I'm testing an Alpha or Beta I'll keep two of each kernel, but in a stable release there's no need for more than one.

Lastly, if you ever decide to re-install the generic kernel, I'll bet you know how to do it.

---

### Post by extendedping on 2010-02-06
thanks, I did install the startup-manager but there are no options as to what to show just which to make the default. I went ahead and got rid of all other kernels and so far no issues. now...can I remove the kernel headers too? my update manager keeps popping up with headers for the kernels that I don't have anymore...

---

### Post by AutoStatic on 2010-02-06
You can remove the headers too, since you don't use the non-rt kernels anymore.

---

### Post by extendedping on 2010-02-06
thanks its just me and rt now...

---

### Post by kvarley on 2010-02-06
Ubuntu Tweak will do this for you amoungst other things and it has a nice GUI.

---

