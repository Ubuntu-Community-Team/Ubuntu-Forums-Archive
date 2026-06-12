---
title: "Curious about 64-bit compatibility"
date: 2012-02-09
forum: System76 Support
---

### Post by aariel on 2012-02-09
The time has come for a new laptop, and one of the machines I'm considering is the Serval Pro. At work I need to be able to simulate some of our live servers in my local environment, so being able to use a 64-bit OS is a big requirement for me.

I'm curious to know:

1) Do System76 laptops ship with 64-bit or 32-bit Ubuntu?
2) Has anyone experienced any gotchas while running 64-bit Ubuntu on any System76 laptops that required them to switch back to 32-bit?

Thanks!

---

### Post by runny6play on 2012-02-09
The computers sell with 64 bit and therefore all of the system 76 specfics are available for such... you would only need to switch back to 32 bit in the instance that there is a program you need not written for the amd_64 / 86_64 archatechures

---

### Post by isantop on 2012-02-10
> **runny6play said:**
> The computers sell with 64 bit and therefore all of the system 76 specfics are available for such... you would only need to switch back to 32 bit in the instance that there is a program you need not written for the amd_64 / 86_64 archatechures

This isn't strictly true. The 64-bit Ubuntu kernel is fully capable of running 32-bit code (due in large part to the fact that AMD64 is simply an extension of the old, 32-bit i686 architecture). You only run into problems when a 32-bit program requires capabilities that the 64-bit libraries can't provide. In 99% of these cases, you can install the 32-bit version of the library by installing the ia32-libs package, which includes 32-bit versions of many common library files. This allows nearly all 32-bit programs to run flawlessly in 64-bit Ubuntu.

It's also worth noting that the Ubuntu repositories automatically create 64-bit packages for almost all of the software in the repositories, so if the application in question can be installed from the repositories, Ubuntu will automatically get you the 64-bit version by default.

---

