---
title: "Ubuntu 14.04 in virtualbox guest edition with host os win 7 is responding very slow"
date: 2014-05-21
forum: Virtualisation
---

### Post by Prosanta on 2014-05-21
[COLOR=#000000]I recently install Ubuntu 14.04 in virtualbox guest edition with host os win 7. It is acting very slow now. When I type something on terminal, it is taking 2-3 sec to appear on the screen.[/COLOR]
[COLOR=#000000]my system config is core i3 cpu m330 @2.13Ghz, 3GB RAM, Win 7 OS[/COLOR]

---

### Post by Old_Grey_Wolf on 2014-05-21
How much memory did you give the VM? How much video memory did you give the VM?

---

### Post by Prosanta on 2014-05-22
512MB to VM and 128 to Video memory. enabled 3D acceleration.

---

### Post by Old_Grey_Wolf on 2014-05-22
I would increase the memory from 512MB to at lest 768MB, 1GB would be better.

---

### Post by Prosanta on 2014-05-22
I tried that also but it is not solving problem. Although VM stops working sometimes.

---

### Post by sandyd on 2014-05-22
How is the CPU usage of your host system, and how many CPUs are you allocating to the VM?

---

### Post by Prosanta on 2014-05-23
it is having quad core. Maximum CPU uses reaching 66%. 1 core is allocated to VM(default, can not be changed). PAE/NX is enable for acceleration.

---

### Post by slickymaster on 2014-05-23
Moved to the **Virtualisation** sub-forum.

---

### Post by Old_Grey_Wolf on 2014-05-23
> **Prosanta said:**
> it is having quad core...

For those trying to help, Prosanta has an i3 so it is actually a dual-core with two threads per core.

Do you have VT-x/AMD-V enabled?
Do you have Nested Paging enabled?

In another closed thread from 3 hours ago you posted > **Prosanta said:**
> VM memory is set to 512MB and for video 128MB. After Running ubuntu in VM, RAM uses keep on increasing and it crosses 2.3GB , finally crashes VM.
Did you increase the memory to 1GB or leave it at 512MB?

---

### Post by Prosanta on 2014-05-24
I enabled VT-X/AMD-V and Nested Paging, its performance is improved litte bit. I kept memory to 768MB, although VM stops working sometimes.

---

### Post by TheFu on 2014-05-24
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) - I've tested this on a Win7 hostOS with Ubuntu 14.04 Unity. It works.

---

