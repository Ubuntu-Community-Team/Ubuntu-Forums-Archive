---
title: "Graphics card"
date: 2010-04-03
forum: Virtualisation
---

### Post by mumuyazzer13 on 2010-04-03
Hi i have a graphics card an i dont know what it is i think its nvidia but  how do i figure out what it is an what version because i want to install Drivers or somthin from the website):P

---

### Post by howefield on 2010-04-03
Is this post in the Virtualization forum because you are referring to a virtualised installation ?

If so, it won't matter what your graphics card is as the virtual machine will supply the graphic driver.

---

### Post by mumuyazzer13 on 2010-04-03
no i  just wanna find out what graphics card i have plz:)

---

### Post by howefield on 2010-04-03
In terminal type

```
lspci | grep VGA
```

---

### Post by mumuyazzer13 on 2010-04-03
thax ill see if it works :D

---

### Post by mumuyazzer13 on 2010-04-03
VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]


not what i was lookin for im like expecting NVidia GeForce 300 series Blahblahbh like dat

---

### Post by howefield on 2010-04-03
> **mumuyazzer13 said:**
> VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]


not what i was lookin for im like expecting NVidia GeForce 300 series Blahblahbh like dat

Finding a Radeon when you were expecting an Nvidia, now that is bad luck... ;)

---

### Post by mumuyazzer13 on 2010-04-03
No i have a nvidia dats 1 thing ik

---

### Post by howefield on 2010-04-03
Have you got Ubuntu running in a virtual machine, like Virtualbox ?

---

### Post by mumuyazzer13 on 2010-04-03
yh i got 10.04  :D

---

### Post by howefield on 2010-04-03
> **mumuyazzer13 said:**
> yh i got 10.04  :D

What I mean is have you installed 10.04 in Virtualbox or similar ?(by the way, it isn't 10.04 until it is released on the 29th April, until then, it is a development release known as Lucid Lynx).

Reason I am asking is that you have posted in the Virtualization forum. Virtual machines do not see the real hardware they are running on, only what the Virtual machine manager tells them to see, including the graphics card.

---

### Post by JustinR on 2010-04-03
VirtualBox emulates all hardware for your Ubuntu 10.04 installation - this means that it supplies its own graphics card driver for Ubuntu, not the one natively installed on your system.

---

