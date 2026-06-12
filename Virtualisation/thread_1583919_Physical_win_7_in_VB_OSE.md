---
title: "Physical win 7 in VB OSE"
date: 2010-09-28
forum: Virtualisation
---

### Post by newboyo on 2010-09-28
Hi All,

I followed    [http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437) and have been able to come upto this stage (pls see screenshot) using 9.10 with legacy Grub on my Lenovo T410, but am now stuck.

would appreciate any help/guidance.

Rgds

New

---

### Post by Joe of loath on 2010-09-28
Make sure 64 bit virtualisation is enabled in virtualbox.

---

### Post by sikander3786 on 2010-09-28
Did you see this?

[http://www.virtualbox.org/manual/ch03.html](http://www.virtualbox.org/manual/ch03.html)

Is the system itself 64-bit capable? And the host OS is also 64-bit? If so, 64-bit virtualization should have been enabled by default.

---

### Post by newboyo on 2010-09-28
> **Joe of loath said:**
> Make sure 64 bit virtualisation is enabled in virtualbox.

Hi Joe,

Thanks for helping out.

When I make the windows type to Win 7 64 bit, it enables VT-x/AMD -V. On firing up the virtual machine, there is a quick flash of a message (can't read it) and the virtual machine aborts.

If i change the win type to 32 bit, then VT-x/AMD -V is disabled. upon firing up the virtual machine, i arrive at the error state mentioned in my first post.

will appreciate your inputs.

---

### Post by newboyo on 2010-09-29
> **sikander3786 said:**
> Did you see this?
 
[http://www.virtualbox.org/manual/ch03.html](http://www.virtualbox.org/manual/ch03.html)
 
Is the system itself 64-bit capable? And the host OS is also 64-bit? If so, 64-bit virtualization should have been enabled by default.
 
 
Hi Sikander,
 
I think the VM is ok on these fronts, however will recheck them and update the thread.
 
Thanks vm.

---

