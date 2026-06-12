---
title: "Ubuntu inside a VM"
date: 2009-03-10
forum: Virtualisation
---

### Post by phoda on 2009-03-10
Hi,

I'm working with an Ubuntu installation inside a VMWare Virtual Machine. It works fine, I can setup the screen resolution to 1024 x 768 but I cannot setup the refresh rate... It's always zero...

How can I fix this problem?

---

### Post by Nxion on 2009-03-10
> **phoda said:**
> Hi,

I'm working with an Ubuntu installation inside a VMWare Virtual Machine. It works fine, I can setup the screen resolution to 1024 x 768 but I cannot setup the refresh rate... It's always zero...

How can I fix this problem?

Why do you need to set it? Is your screen fuzzy? I have never needed to set the refresh rate before on a VM. I really don't think you can. Your HOST machine controls the refresh rate not the VM.

---

### Post by phoda on 2009-03-10
> **Nxion said:**
> Why do you need to set it?

When I drag a window, the moviment/refresh is slow... I think change the screen refresh rate solve this...

---

### Post by Nxion on 2009-03-10
> **phoda said:**
> When I drag a window, the moviment/refresh is slow... I think change the screen refresh rate solve this...

Have you installed the VMware Tools for Linux? This is actually what you need to fix it. The tools contain drivers to let the machine interact and respond better in a VM. That should fix the movement issue.

---

### Post by phoda on 2009-03-10
> **Nxion said:**
> Have you installed the VMware Tools for Linux?

Not yet. I'll install it to check. ;)

---

### Post by bodhi.zazen on 2009-03-10
What [Nxion]("http://ubuntuforums.org/member.php?u=205132") said :twisted:

But your guests do not directly use your hardware, thus the refresh rate of 0

---

### Post by Nxion on 2009-03-10
> **bodhi.zazen said:**
> What [Nxion]("http://ubuntuforums.org/member.php?u=205132") said :twisted:

But your guests do not directly use your hardware, thus the refresh rate of 0


You said it better :) Thats what I was trying to say :)

---

