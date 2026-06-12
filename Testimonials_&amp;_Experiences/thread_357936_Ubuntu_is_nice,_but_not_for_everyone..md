---
title: "Ubuntu is nice, but not for everyone."
date: 2007-02-10
forum: Testimonials &amp; Experiences
---

### Post by mikewhatever on 2007-02-10
This morning (Saturday) I couldn't stop myself from saying thank you many many times to good fortune, of cause.:)  Having installed the latest kernel updates, broke xserver, grub menu, wireless, and what not, but it is not the issue, although related. 
I've installed Ubuntu for the first time about two month ago, and liked it and the idea to the point, that I recommended it to my parents. They got interested, and one weekend, we almost installed it on their PC. Thanks God, that after a short discussion we didn't. We've actually decided, to postpone the installation, until my dad gets a good book on Ubuntu.
Imagining my parents having to deal with today's update issues, makes me unbelievably greatfull that they do not have Ubuntu installed. They are in their 60s, and do not like unexpected changes with their PC, but most of all, they dislike changes in the GUI. Can you imagine, what happens, when there is no GUI? 
Just in case someone does not know what I am talking about, [read hear]("http://ubuntuforums.org/showthread.php?t=356408") about the problem.

---

### Post by picpak on 2007-02-10
Was this kernel problem on Dapper or Edgy? On my mom's computer, it told her to run sudo apt-get dist-upgrade, and when I did, it installed perfectly.

If you'd like to give them Ubuntu, give them Dapper. Aside from the breakage last August, it's been stable.

---

### Post by kevinlyfellow on 2007-02-10
have the update manager check biweekly, so that if there is a problem, it would probably be resolved by the time your folks do their update.

---

### Post by mikewhatever on 2007-02-11
> **picpak said:**
> Was this kernel problem on Dapper or Edgy? On my mom's computer, it told her to run sudo apt-get dist-upgrade, and when I did, it installed perfectly.

If you'd like to give them Ubuntu, give them Dapper. Aside from the breakage last August, it's been stable.
The update affected both Dapper and Edgy users, the majority seem to be having nvidia related problems. There is no problem with installing the update. It install alright, but then you have to reboot. :) 

> have the update manager check biweekly, so that if there is a problem, it would probably be resolved by the time your folks do their update.
Thanks, that's a good idea, but would not have saved the day in view of the quote below.
> Due to an unavoidable ABI change the Ubuntu 6.06 and Ubuntu
6.10 kernel updates have been given a new version number, which
requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

---

### Post by 3rdalbum on 2007-02-11
Why not just disable the update manager? Even a non-updated Ubuntu is going to cause a script kiddie to look for easier prey, and truly malicious crackers don't usually bother with home computers.

---

### Post by argie on 2007-02-11
Or lock the version of the kernel to one version. I do that with my wine because I don't want to accidentally install a newer version that has regressions.

---

### Post by mikewhatever on 2007-02-11
> **3rdalbum said:**
> Why not just disable the update manager? Even a non-updated Ubuntu is going to cause a script kiddie to look for easier prey, and truly malicious crackers don't usually bother with home computers.
I would never expect anything of the sort to happen in the first place. Disabling the update manager would pose another problem, since they like to have their system updated and think it important. I can't tell them that updating the kernel will break their GUI, wifi, microphone and what not, can I.

---

### Post by mikewhatever on 2007-02-11
> **argie said:**
> Or lock the version of the kernel to one version. I do that with my wine because I don't want to accidentally install a newer version that has regressions.

Yes, I like that one. How do I lock it then?

---

### Post by ubuntu27 on 2007-02-11
> **mikewhatever said:**
> Yes, I like that one. How do I lock it then?

I am not in my Ubuntu, so I can't remeber well.

Open Synaptic Manager, and then search for whatever you want to lock, in this case Linux-Kernel

Right click on the one that you have installed and choose something like "Lock version" 

I am relying on my memory...
But, I am sure it is helpful in someway.

---

### Post by mikewhatever on 2007-02-12
Thanks Ubuntu27, I found the option in synaptic. I'll uninstall the newer kernel on my laptop, and then lock the working older one. I am afraid, long time will pass before I venture to update it again. As for my parents, they can have it if they want too, but personally, I would not encourage it. I'd advise them to buy a cheep second hand PC to experiment with Ubuntu. May be in time, they will get familiar enough to use it as their main system, and hopefully, Ubuntu will become a bit more reliable.

---

### Post by halfvolle melk on 2007-02-12
Mikewhatever,
Please read this and consider if you really want to lock the old kernel.
[http://www.linuxcompatible.org/USN-416-1_Linux_kernel_vulnerabilities_s81279.html](http://www.linuxcompatible.org/USN-416-1_Linux_kernel_vulnerabilities_s81279.html)

---

### Post by mikewhatever on 2007-02-13
Thanks for the link. It does look like locking the older kernel is a bad idea. It appears, that if I want to have Ubuntu uptodate, I'll have to accept the fact that every once in a while there is a kernel update and things will stop working. That is a big and unexpected drawback, but there seems to be no choice, and, as the title states, it is nice, but definitely not for everyone.

---

### Post by halfvolle melk on 2007-02-14
> **mikewhatever said:**
> if I want to have Ubuntu uptodate, I'll have to accept the fact that every once in a while there is a kernel update and things will stop working.
No not really. In order to keep the X server running, just use the nvidia-glx package from the official repositories. Like others have pointed out before, when you build the driver from 3rd party sources (such as NVIDIA-9blahblah.sh) only then you can expect it to break at every kernel update.

---

### Post by yabbadabbadont on 2007-02-14
> **halfvolle melk said:**
> No not really. In order to keep the X server running, just use the nvidia-glx package from the official repositories. Like others have pointed out before, when you build the driver from 3rd party sources (such as NVIDIA-9blahblah.sh) only then you can expect it to break at every kernel update.

Actually, it broke my dapper system too.  I'm using the plain old nvidia driver that is included in the linux-restricted-modules package.  It didn't cause me too many problems though, as I always boot to a text console.  It gave me a good excuse to try out FreeBSD.  ;)

---

### Post by uNmentaLogic on 2007-02-14
I've begun to prefer FreeBSD more than linux recently, the only thing I dont really like is the lack of native flash. I love my youtube music clips.

---

### Post by mikewhatever on 2007-02-14
> **halfvolle melk said:**
> No not really. In order to keep the X server running, just use the nvidia-glx package from the official repositories. Like others have pointed out before, when you build the driver from 3rd party sources (such as NVIDIA-9blahblah.sh) only then you can expect it to break at every kernel update.

That is incorrect, although should be theoretically. I've never used any third party driver before the kernel update. If you brows the forums, you'll find threads of people having x problems right after they installed and then updated. They could not possibly have had any propriatory stuff installed. Others have GRUB menu problems, such as Ubuntu partition number change, something the update had no business with. I think you are flatly denying the obvious problem here. I have to say, there is no need to  defend Ubuntu from me. No one forced me to use it, so I have no demands whatsoever. Sooner or later, this kernel issue would have turned up, and I am glad I know now, and more then glad my parents haven't installed it back then.

---

