---
title: "Which VirtualBox version for 10.04 64-bit"
date: 2010-04-29
forum: Virtualisation
---

### Post by manco on 2010-04-29
So back in 9.10 (32 bit), I used [this guide]("http://ubuntuforums.org/showthread.php?t=1074160") to install the version of VirtualBox I wanted.

Now I'm in 10.04 64-bit, and I'd like to install the same "version" of VirtualBox.  I'm not sure if there's any special info for 64-bit of if I can just follow the above guide.

Also, if I install VirtualBox, can I install 64-bit virtual machines?

Thanks!

---

### Post by clblanchard on 2010-04-29
You can try the distro independent download from they virtualbox site.  Just make sure you have "dkms" and "build-essential" installed and use the command "sudo sh 'filename'.run" to install.  It worked like a charm for me last night.

---

### Post by manco on 2010-04-30
> **clblanchard said:**
> You can try the distro independent download from they virtualbox site.  Just make sure you have "dkms" and "build-essential" installed and use the command "sudo sh 'filename'.run" to install.  It worked like a charm for me last night.
Just to confirm, are you referring to the downloads listed [here]("http://www.virtualbox.org/wiki/Linux_Downloads")?

I downloaded the x64 version for Karmic, but I haven't installed it yet.  Is the x64 version on the above page the OSE?  I really don't want the OSE; definitely want the PUEL version.

---

### Post by GuiGuy on 2010-05-07
> **manco said:**
> 
I downloaded the x64 version for Karmic, but I haven't installed it yet.  Is the x64 version on the above page the OSE?  I really don't want the OSE; definitely want the PUEL version.

I tried the Karmic version off Sun's download site. It works under Lucid but I found running winxp out of it the CPU usage went through the roof resulting in very sluggish performance.

---

