---
title: "Can't share folders on 22.10?"
date: 2022-09-26
forum: Ubuntu Development Version
---

### Post by leillo1975 on 2022-09-26
A few days ago I installed the daily build of Kinetic Kudu , and I quite like everything I found, but I can't share folders. If I right click on one of them I can't find the "Local Network Share" which is usually there. Has that function been moved somewhere else or is it not implemented yet?

---

### Post by corradoventu on 2022-09-26
I see the same problem, so i opened a bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1990841](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1990841)

---

### Post by leillo1975 on 2022-09-26
Thanks for creating the bug on launchpad. I put myself in the affected list.

---

### Post by leillo1975 on 2022-09-30
As **Jeremy Bicha** said in the launchpad bug, it seems that "nautilus-share" is not compatible with the new version of nautilus, and has been deleted. Hopefully they will include the new version quickly. This is in my case a critical problem.

---

### Post by corradoventu on 2022-09-30
Jeremy Bicha is not a simple user, jbicha is a main developer on Debian and Ubuntu!

---

### Post by leillo1975 on 2022-09-30
Upppss! Sorry....
I will edit it

---

### Post by Claus7 on 2022-10-03
Hello,

today I tapped the reload button in synaptic package manager and there were some new packages proposed: one of them was nautilus-share. I suppose that this is the one the OP was looking for. After installation, I opened nautilus (Files) and right clicked a folder. There appeared the option: Sharing Options. 

Regards!

---

### Post by leillo1975 on 2022-10-04
Thanks a lot for the tip. Supposedly it will install itself at some point when I update or will we have to install it by hand?

---

### Post by Claus7 on 2022-10-04
Hello,

> **leillo1975 said:**
> Thanks a lot for the tip. Supposedly it will install itself at some point when I update or will we have to install it by hand?

Nice that you found it handy. When it appeared, I installed it right away. I guess that since it is not installed already and that it is a separate package, I would go by hand. After all, if you need it right now, this is the way to install it: go to synaptic package manager -> type nautilus share -> click it and install it with its required dependencies.

Regards!

---

