---
title: "Upgraded 17.10 to 18.04 but the 4.16 kenel did not install"
date: 2018-03-10
forum: Ubuntu Development Version
---

### Post by wildmanne39 on 2018-03-10
Hello, I am wondering why the 4.16 kernel did not install when I upgraded to 18.04, I checked to see if the 4.15 kernel is locked but it does not appear to be, so what is the best way to upgrade the kernel to 4.16?

Edit:

I am using kernel 4.15.1+ it is a special kernel for AMD graphics, it allows my laptop to run ubuntu after over a year of trying to get it working. With this kernel I can not run virtualbox and I very much would like too.

---

### Post by kerry_s on 2018-03-10
sudo apt update && sudo apt -y full-upgrade

---

### Post by wildmanne39 on 2018-03-10
Thanks for your answer kerry_s, it looks like 18.04 is still using kernel 4.15 so I guess that is why it did not upgrade to kernel 4.16.

---

### Post by cruzer001 on 2018-03-10
Last I read (a couple weeks ago) 4.16 may not make it at all to 18.04.

---

### Post by #&amp;thj^% on 2018-03-10
> **wildmanne39 said:**
> Thanks for your answer kerry_s, it looks like 18.04 is still using kernel 4.15 so I guess that is why it did not upgrade to kernel 4.16.

Ah come on dose this mean your not going to play with the main-line kernels? :o ;)
Man what kind of tester are you?:lolflag:
This is where the **Blood** comes from in "Bleeding Edge":D
Best Regards

---

### Post by wildmanne39 on 2018-03-10
> **1fallen said:**
> Ah come on dose this mean your not going to play with the main-line kernels? :o ;)
Man what kind of tester are you?:lolflag:
This is where the **Blood** comes from in "Bleeding Edge":D
Best Regards
I installed the 4.16 mainline kernel after I posted this thread!:)

---

### Post by cruzer001 on 2018-03-11
I also installed the 4.16 kernel, but I cannot install a nvidia driver, just hangs during the install and never completes.

Edit
Downloaded the wrong header package, needed the all.deb.  Installing the 390 driver now.

---

### Post by #&amp;thj^% on 2018-03-11
> **wildmanne39 said:**
> I installed the 4.16 mainline kernel after I posted this thread!:)

Anything wonderful to report or noticed? (With your hardware specs)

---

### Post by wildmanne39 on 2018-03-11
> **1fallen said:**
> Anything wonderful to report or noticed? (With your hardware specs)
On my laptop with AMD graphics everything is working great now with the 4.16rc4 kernel even the touchpad works correctly no more cursor jumping all over the place while I am typing.:D

---

### Post by #&amp;thj^% on 2018-03-11
> **wildmanne39 said:**
> On my laptop with AMD graphics everything is working great now with the 4.16rc4 kernel even the touchpad works correctly no more cursor jumping all over the place while I am typing.:D

WOOT! I was hoping for that! :D
Thanks for updated info wildmanne39.
Best Regards

---

### Post by wildmanne39 on 2018-03-14
Just an update on the status of 18.04 using kernel 4.16rc4 after an update my touchpad has started acting up again but I can suspend and log back in successfully,  at the log in screen to be able to get my password to work I have to click on my user even though it is showing then I can enter the password and all is good if I do not click on my user then the password fails. Also the wifi resumes with no issues, for the record 17.10 I could never suspend and resume using it.

---

