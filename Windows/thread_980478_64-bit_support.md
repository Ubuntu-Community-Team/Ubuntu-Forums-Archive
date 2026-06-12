---
title: "64-bit support"
date: 2008-11-12
forum: Windows
---

### Post by sanmoon on 2008-11-12
Hi folks,

        I am a new guy on 64-bit platforms. I installd JDK 1.6.3 64-bit varsion in my system and I am windows xp(64-bit). I am trying to load a .dll at runtime into my application.I got the error message 
      "java.lang.UnsatisfiedLinkError: C:\WINDOWS\SysWOW64\rlmjava502.dll: Can't load IA 32-bit .dll on a AMD 64-bit platform". 
       Actually i got that dll from a third party and actually i thought it is a 32-bit dll.

       Please help to solve the problem.There is no option to get 62-bit dll. Can we work with the 32-bit dll on 64-bit machine?

---

### Post by Yellow Pasque on 2008-11-12
This subforum is for Ubuntu **Linux**.
> Can we work with the 32-bit dll on 64-bit machine?
No. The .dll you are using is 32-bit and you are apparently making a 64-bit project.

---

### Post by PartisanEntity on 2008-11-13
Moved.

---

### Post by Grant A. on 2008-11-13
64-bit computers can run 32-bit operating systems. It is not uncommon for manufacturers like HP to give you a 32-bit Windows Installation on a 64-bit platform.

---

