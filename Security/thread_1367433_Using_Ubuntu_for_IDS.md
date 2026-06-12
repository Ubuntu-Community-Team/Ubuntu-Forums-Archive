---
title: "Using Ubuntu for IDS"
date: 2009-12-29
forum: Security
---

### Post by Hopping_Ubu on 2009-12-29
I have just completed doing a test configuration in a virtual environment using Ubuntu 9.10 workstation as the IDS sensor for Snort. I was wondering when I set it up in a live environment if I should use Ubuntu 9.10 Server instead of the workstation OS. It looks like it will be more than I really need, but at the same time more robust.

This will be set up in a virtual environment just as I have configured in my test environment.

Thanks everyone.

---

### Post by 0x414141 on 2009-12-30
Your choice of OS should not change anything. Snort is snort no matter where you install it. But i would be very careful with virtualisation. Keep in mind that the host may modify the packets (either through Nat or Pat) and this may affect the performance of Snort.

I hope it helps.

---

### Post by Hopping_Ubu on 2009-12-30
Thanks, I will keep that in mind. What I would like to do is keep the current server as the IDS.

---

### Post by bodhi.zazen on 2009-12-31
If you are going to set up a dedicated box for snort, use a minimal install and add only what you need.

Less applications == less opportunity for crackeres , and this is IMO a critical concern when deploying an IDS.

So, go ahead an play with snort on a desktop or a VM, but once your are ready to deploy, go for a minimal install =)

---

### Post by Hopping_Ubu on 2009-12-31
> **bodhi.zazen said:**
> If you are going to set up a dedicated box for snort, use a minimal install and add only what you need.

Less applications == less opportunity for crackeres , and this is IMO a critical concern when deploying an IDS.

So, go ahead an play with snort on a desktop or a VM, but once your are ready to deploy, go for a minimal install =)

Thanks bodi.zazen. The test environment I currently have it running in is a minimal installation. I run it in a virtual environment on Ubuntu 9.10 desktop. :)

---

