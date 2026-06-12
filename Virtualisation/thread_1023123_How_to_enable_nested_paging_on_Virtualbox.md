---
title: "How to enable nested paging on Virtualbox"
date: 2008-12-27
forum: Virtualisation
---

### Post by quad65 on 2008-12-27
Hi,

I found out that nested paging feature improves VM performance. This feature is newly added, so no gui setting is available for this one. I tried using the following command, but it was not enabled:

```
VBoxManage modifyvm "Windows XP" -nestedpaging on
```

My VM's name is Windows XP, so no problems there. I have an AMD X2 processor, AMD-V is enabled.

Can anyone help me?

Thanks in advance.

---

### Post by Dedoimedo on 2008-12-28
AMD-V is enabled in VB via Settings or in BIOS, too?
Dedoimedo

---

### Post by quad65 on 2008-12-30
It is enabled in both settings and BIOS.

---

### Post by sonofusion82 on 2009-01-01
I have Phenom X4 and nested paging works for me after enabled with the command by OP.
However, if I am not mistaken, nested paging requirest at least AMD K10 Barcelona or Phenom cores. Unfortunately, AMD Athlon X2 might not work.
After enabling it, I can see noticable performance boost. I would really recommend it if you have a newer AMD processor or Nehalem.

---

### Post by quad65 on 2009-04-19
I would like to announce that, as of VirtualBox 2.2.0, there is a checkbox to enable nested paging.

But that does not mean I was able to enable it. Although I checked it, it was disabled. So, what sonofusion82 said seems to be true.

About nested paging getting disabled at runtime, here is a bug report:

[http://www.virtualbox.de/ticket/3141](http://www.virtualbox.de/ticket/3141)

---

### Post by rJ~ on 2009-04-20
Nested paging is indeed only available for K10 (Phenom) for AMD cpus (and i7 for Intel cpus).

---

