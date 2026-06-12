---
title: "Ubuntu Freezes with AMD-V enabled in VirtualBox"
date: 2009-11-26
forum: Virtualisation
---

### Post by xtjacob on 2009-11-26
Hello all, I have ubuntu 9.10 64-bit on a Acer Aspire 4530, and if I enable AMD-V in VirtualBox and run it it completely freezes the system and I have to do a cold restart. It works fine if I turn it off. I have done some research, and tried adding nohz=off to the end of my kernel list in menu.lst, and it still freezes. Please help!

---

### Post by AlejandroDelLoco on 2009-12-28
Hi! I am having the same problem on an Acer aspire 5517! Is there any way to run a 64 bit guest system or should I just run it 32 and use the software virtualization?

---

### Post by xtjacob on 2009-12-28
On my install Ubuntu freezes if I enable software virtualization regardless of whether the guest is 32-bit or 64-bit. The weird thing though is it only does it with certain guests. For example, Vista freezes it, but Windows server 2008 R2 Standard does not. Also I am running the latest version and it still does it.

---

### Post by xtjacob on 2009-12-31
Nothing seems to be helping this... :( Does anyone know how to fix this? :confused:

---

### Post by xtjacob on 2010-01-02
This is no longer Virtualbox, but also with VmWare. It seems no matter wha it freezes.

---

### Post by fernandoch on 2010-03-28
Did you find a solution for virtualbox?

It seems I have the same problem, every 10 seconds or so, the guest freezes and then gets back to normal. Impossible to work like that...

I am having the same problem with vmware :(

---

### Post by xtjacob on 2010-03-29
Nope, I have yet to find a solution. Hope it will be fixed in Lucid, or a new version of Virtualbox.

---

### Post by fernandoch on 2010-03-29
Can you tell me what kernel are you using?

uname -a ????

---

### Post by xtjacob on 2010-03-29
Currently running 2.6.31-20 going to upgrade to 2.6.31-21, would custom compiling 2.6.33.1 fix it?

---

### Post by fernandoch on 2010-03-29
can u do the uname -a?

---

### Post by xtjacob on 2010-03-29
```
Linux jacob-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

---

### Post by fernandoch on 2010-03-30
I had a PAE kernel in the host, and had a lot of problems. I changed the PAE by the generic kernel and all my problems were gone.

Why don't you then try the PAE kernel? It might work for you...

---

### Post by xtjacob on 2010-03-30
Ok, I'll let you know whether it works.

---

