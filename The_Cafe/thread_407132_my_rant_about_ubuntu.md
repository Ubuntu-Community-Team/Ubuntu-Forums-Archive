---
title: "my rant about ubuntu"
date: 2007-04-11
forum: The Cafe
---

### Post by gsgleason on 2007-04-11
I can't believe ubuntu doesn't come with packages necessary to compile a kernel.  I installed it on a new machine with an asus p5b-e mobo, which uses an ethernet adapter that doesn't have native kernel support (yet).  no big deal as kernel modules are available for 2.6.20.  I downloaded the full kernel source as well as the necessary kernel module sources for the ethernet adapter, only to find out that ubuntu is missing a lot of the required packages to compile a kernel, some of which aren't even available on the install CD, so I had to download them, put them on a flash drive, and copy them over.

anyway that's my rant.  I think that every distro should have everything installed to compile a new kernel when necessary (which is often considering the vast array of hardware out there).

</rant>

---

### Post by rocknrolf77 on 2007-04-11
```
sudo aptitude install build-essential
```

---

### Post by zenwhen on 2007-04-11
In order to keep the distro as a one CD install, certain sacrifices have to be made. This is one of them.

---

### Post by dasunst3r on 2007-04-11
Do understand that very few people compile stuff.  To save disk space, the packages needed for compiling stuff were excluded from the mix.  Was it easy for you to get the compilers you need?

---

### Post by prizrak on 2007-04-11
> **rocknrolf77 said:**
> ```
sudo aptitude install build-essential
```

Doesn't work too well when the NIC is out of comission.

---

### Post by FoolsGold on 2007-04-11
I cannot confirm this, but I'd be surprised if the DVD version of Ubuntu didn't have the compiler stuff available to be installed from the disc. If you really need a lot of packages available on a system without a connection available, try the DVD.

---

### Post by aysiu on 2007-04-11
I share your frustration that *build-essential* isn't installed by default, and I don't agree with the developers that having it installed by default would be a security risk, but it **is** on both the Alternate CD and the Desktop CD: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by o_fortuna on 2007-04-11
> **gsgleason said:**
> I can't believe ubuntu doesn't come with packages necessary to compile a kernel.  I installed it on a new machine with an asus p5b-e mobo, which uses an ethernet adapter that doesn't have native kernel support (yet).  no big deal as kernel modules are available for 2.6.20.  I downloaded the full kernel source as well as the necessary kernel module sources for the ethernet adapter, only to find out that ubuntu is missing a lot of the required packages to compile a kernel, some of which aren't even available on the install CD, so I had to download them, put them on a flash drive, and copy them over.

anyway that's my rant.  I think that every distro should have everything installed to compile a new kernel when necessary (which is often considering the vast array of hardware out there).

</rant>
I don't really get what you're saying. I have cd images for both ubuntu 6.10 and ubuntu 7.04 and in the /pool/main/b/ directory there is the build-essential package. Also, I have heard from developers on the mailing list that Ubuntu does in fact include the necessary components to compile a kernel. I haven't actually tried -- but the tools are all there -- gcc 4.1, fakeroot, etc. It even includes ndswrapper. Again, I haven't tried looking for these on the live cd, but the cd does in fact include all of these packages.

---

### Post by aysiu on 2007-04-11
The packages are on the live CD--they're just not *installed* by default. [Read more of the discussion that preceded this decision](http://ubuntuforums.org/showthread.php?t=192840).

---

### Post by ComplexNumber on 2007-04-11
> **gsgleason said:**
> I can't believe ubuntu doesn't come with packages necessary to compile a kernel.  I installed it on a new machine with an asus p5b-e mobo, which uses an ethernet adapter that doesn't have native kernel support (yet).  no big deal as kernel modules are available for 2.6.20.  I downloaded the full kernel source as well as the necessary kernel module sources for the ethernet adapter, only to find out that ubuntu is missing a lot of the required packages to compile a kernel, some of which aren't even available on the install CD, so I had to download them, put them on a flash drive, and copy them over.

anyway that's my rant.  I think that every distro should have everything installed to compile a new kernel when necessary (which is often considering the vast array of hardware out there).

</rant>
would it put it into perspective if i told you that after 11 years(about 7-8 in total) of using linux, i've never once had to compile a kernel?

---

### Post by aysiu on 2007-04-11
Whoa. I totally missed that! This is about compiling kernels, not regular software? Whoops. So I'm assuming *build-essential* isn't adequate for the task?

---

### Post by gsgleason on 2007-04-12
> **ComplexNumber said:**
> would it put it into perspective if i told you that after 11 years(about 7-8 in total) of using linux, i've never once had to compile a kernel?

I guess you're lucky to have all of your hardware supported "out of the box" so to speak.

My first kernel compile was necessary to support my zydas zd1211 based usb wlan card, which was fine.

If it was anything but the damn NIC that wasn't supported, the "standard" debian method of kernel compile would be fine.

---

