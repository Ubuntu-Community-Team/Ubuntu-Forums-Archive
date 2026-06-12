---
title: "karmic koala with vmware slow problem"
date: 2010-02-17
forum: Virtualisation
---

### Post by aeon.flux on 2010-02-17
hello there,
i have a problem with vmware on my ubuntu 9.10. when i run windows7 everything is so slow and laggy, the mouse stop moving for few sec. and than it goes normally, this happen every about 10 sec. i'm really angry about that, i have to do some work in CorelDraw and don't have much time, please help me somebody

i have
hp pavilion dv6000 
1.73 intel dual core (both allowed to be used by machine)
2.5GB RAM (1800MB allowed for machine)
20GB space in windows hdd image
Nvidia go 7200 GPU (has 256MB)
i use latest version of vmware player
machine is windows 7 professional
colors on machine and ubuntu are both set on 32bit
*note - when i connected notebook to external monitor (via VGA) with resolution 1280x1024 (notebook has only 1280x800) it was surprisely much better, but after few hours its again same s**t 
i have already updated vmware tools in machine with no effect
my brother use vmware on windows every day and he say what my HW and settings should be OK, but he don't know/use linux.
can somebody tell me where can be problem please?

---

### Post by fjgaude on 2010-02-17
Try using only one core for your VM. That should greatly help.

---

### Post by aeon.flux on 2010-02-17
i've just tried it few minutes ago and it's slower than before :(

---

### Post by HermanAB on 2010-02-18
Howdy,

Install VMware Tools on the Windows VM.

---

### Post by aeon.flux on 2010-02-18
read what i write please, i did it 3 times (installed, updated and again checked)

yesterday i borowed my roomates lenovo t400 with 2,4ghz dual core and did the whole work in 2 hours :D

---

### Post by HermanAB on 2010-02-18
If Vmware tools installed error free, confirm that the service is actually running using the WinXP 'net' command.

---

### Post by aeon.flux on 2010-03-03
haha! :D

the problem was, that i have my personal data and ubuntu system files on 1 disc, so running 2 operating systems from 1 disk worked so slow, because disc had to read data and write 2x, that was why i had to wait so much. i moved machine to virtual disc and now it's ok. it could be faster, but i can work with it now

---

