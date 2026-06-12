---
title: "Simultaneous use of VT-x"
date: 2009-03-20
forum: Virtualisation
---

### Post by cfree220 on 2009-03-20
Hi, I mostly use Ubuntu these days, but schoolwork sometimes requires that I have access to a Vista computer. I'm currently beta testing Windows 7 in a virtual machine. For comparison, I also created a Vista Ultimate VM. I have VT-x enabled on only one of the machines, however I still get a warning message:

An active VM already uses software virtualization. It is not allowed to simultaneously use VT-x or AMD-V, therefore this VM will be run using software virtualization as well.
.
My two questions are:
1. Is it a problem that I am getting this message even if I have VT-x disable on one

and

2. On what planet does that error message make sense?

---

### Post by bodhi.zazen on 2009-03-20
What virtualization are you running ? are you mixing virtualbox and KVM ? KVM and VMWare ? Other ???

---

### Post by cfree220 on 2009-03-20
Just virtualbox

---

### Post by simplified on 2009-03-29
Hey There

The problem that you have here is that the settings for VT-x and AMD-V off. Go into the settings for each machine and under the 'General' section click on the 'Advanced' tab and then ensure that the option 'Enable VT-x/AMD-V' is ticked. Worked for me!

Cheers, OL

---

### Post by cfree220 on 2009-03-30
Yeah, that worked for me too... It just doesn't make sense that it would...

---

