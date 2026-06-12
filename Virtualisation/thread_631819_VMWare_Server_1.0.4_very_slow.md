---
title: "VMWare Server 1.0.4 very slow"
date: 2007-12-04
forum: Virtualisation
---

### Post by McMonarch on 2007-12-04
I'm running Ubuntu 7.04 and I have VMWare Server. I also have Windows XP on a dualboot. I am running the existing xp install on my VMWare Server but it is very slow, much slower than natively running it.

Any suggestions?:(

---

### Post by PilotJLR on 2007-12-04
How much RAM do you have?
How much RAM have you given the guest?

---

### Post by McMonarch on 2007-12-05
I've given it 1264 mb of RAM thats the max amount of ram i can give it without memory swapping
I have 1 1/2 gb of ram on my computer

---

### Post by gumbi18 on 2007-12-05
Have you installed VMware tools within Windows itself?

---

### Post by McMonarch on 2007-12-05
yes i have

---

### Post by gumbi18 on 2007-12-05
Ok then I would suggest to even out your RAM. Assign half ram to the virtual machine. i.e. 768mb. This is  to allow VMware itself run, not to mention Ubuntu.Otherwise you're trying to run Ubuntu on only 248mb of RAM. Also are you running any desktop effects like Compiz?

---

### Post by McMonarch on 2007-12-06
Ubuntu runs fine, its XP thats slow, and yes I do have compiz

---

### Post by lenticular on 2007-12-07
In the VMware console, try changing the RAM settings for your VM.  It sounds counterintuitive, but sometimes VMware seems to run better with less RAM.  It would be interesting for you to try adjusting the RAM slider to the recommended setting (blue triangle?) then seeing how that impacts performance.

-John

---

