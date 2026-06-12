---
title: "Virtualbox install"
date: 2016-02-14
forum: Virtualisation
---

### Post by dave157 on 2016-02-14
I am thinking of using virtualbox to install windows 7 on kubuntu. I just wanted to know if this system has enough power. My system is 

[http://support.hp.com/us-en/document/c01911652](http://support.hp.com/us-en/document/c01911652)

my system is 
CPU Q9400Y
6GB Ram 
GPU nvidia HD 760

I have a program dvd profiler that only works on windows only. any help will be great 

thanks
Dave

---

### Post by QIII on 2016-02-14
You should be fine.

[This]("http://ark.intel.com/products/35365/Intel-Core2-Quad-Processor-Q9400-6M-Cache-2_66-GHz-1333-MHz-FSB") indicates that your processor supports VT-x, which will allow you to create a virtual machine.

You have plenty of RAM.

---

### Post by dave157 on 2016-02-14
Thanks I did not even know that the the CPU had to have VT in order to use virtual machine.

---

### Post by MAFoElffen on 2016-02-16
If it did not. It would just mean that would be limited to installing 32 bit operating systems.

---

### Post by dave157 on 2016-02-17
I see I am so new at this.

---

### Post by MAFoElffen on 2016-02-17
Since you are new... When you start your PC and go to your Bios Setup, look for the Security Menu:
[IMG]http://psg.i.lithium.com/t5/image/serverpage/image-id/68473iA6F59016F87CFB73/image-size/original?v=mpbl-1&px=-1[/IMG]
Most PC's have that VT-x option in General or Advanced menus... HP hides this option on their PC's BIOS under Security > System Security > Virtualization Technology... The default setting is disabled. Change the setting to enabled.

---

