---
title: "The Two Meanings of &quot;Hardware Support&quot;"
date: 2007-12-17
forum: The Cafe
---

### Post by matthewcraig on 2007-12-17
> **aysiu said:**
> When people complain about Linux hardware support, this is *exactly* what they're talking about. They're not talking about Linux supporting more architectures or processor types.

They're talking about buying new third-party hardware and *knowing* in advance (not risking) that it'll work with Windows. If it doesn't work with Windows with plug-and-play, the hardware vendor will almost certainly include a Windows driver CD with the product.

I have actually been thinking about this topic a lot these days, but I did not come to a conclusion until I read the above message.  When Linux people say "hardware support", they mean the Linux kernel supports the hardware.  When Windows people say "hardware support", they mean the hardware vendor supports the operating system.

While Linux supports a great many hardware devices, more than any other, it is not true more hardware manufacturers support Linux.  I just realized the conflicting definitions of the word "supports" and how it causes problems with our conversations about Ubuntu.

I am not sure what would resolve the issue, but at least I can recognize the disconnect now.  Anyone have any thoughts on the subject?  Does Ubuntu need it's own computer parts store, like the Apple Store, where people know they can buy hardware that will work with Ubuntu?  You can tell from my "sig" that I feel people should purchase hardware from companies that support Linux, but maybe there are additional ideas.  How about a website that sells products branded with Linux support?  [LinuxCompatible]("http://www.linuxcompatible.org/compatlist3.html") is great, but it doesn't offer the point-of-sale and Linux technical support.  (And, so sorry about abducting your message to a new forum, aysiu!)

---

### Post by SunnyRabbiera on 2007-12-17
well it would be a good idea if we did have a place to buy drivers and such that are indeed Linux compatible.
currently the only thing that comes close is system 76 but that has its limitations

---

### Post by matthewcraig on 2007-12-17
In the Windows-world, drivers come from the hardware vendors.  In the Linux-world, the drivers come pre-installed in the kernel.  The Linux way is better for OS stability, but it gives the vendor less control.

Look at the differences between the Ubuntu-supplied restricted-NVIDIA driver and the official NVIDIA driver, for example.  The Ubuntu-supplied is more stable for the OS, but the NVIDIA-supplied driver might have more hardware compatibility or more features.

Linux has a different way of doing things, and how does that fit into a Windows-world?

---

### Post by SunnyRabbiera on 2007-12-17
well honestly the vendors need to give us some of the source for their drivers so we can code stuff right, really is it so hard to show off the source code?
I know they are trying to protect a patent but honestly they can give us drivers without it costing them money.

---

### Post by 23meg on 2007-12-17
[QUOTE=matthewcraig]Linux has a different way of doing things, and how does that fit into a Windows-world?[/QUOTE]

It can fit very well. It depends mostly on the extent to which the manufacturer cares.

I bought an Edimax USB wireless adapter, and it came with a CD that had drivers for all major operating systems / kernels, including Linux. The fact that it had Linux support was advertised on the box as well. I didn't need the drivers, since they've already been merged into mainline. 

But they weren't at the time the product came out: the device worked without configuration in Gutsy, but not in Feisty. The manufacturer cared, provided drivers, and it would have worked with Feisty too, had I installed the driver.

---

### Post by matthewcraig on 2007-12-18
I am not sure that requesting and obtaining the drivers from the manufacter is the best option, in the "Linux-world".  Isn't getting the hardware specifications best, so that programmers can create open source drivers and get them into the kernel?  Even if the manufacturer gets you the source code for the device, it may not be under any open-source-compatible license.  The device will not be fully Linux-supported until someone reads through the code, determines the hardware APIs, and rewrites the code under the GPL so it can be put into the kernel.

---

### Post by 23meg on 2007-12-18
[QUOTE=matthewcraig]I am not sure that requesting and obtaining the drivers from the manufacter is the best option, in the "Linux-world". Isn't getting the hardware specifications best, so that programmers can create open source drivers and get them into the kernel?[/QUOTE]

It is. It too depends on how much the manufacturer cares.

---

### Post by aysiu on 2007-12-18
> **matthewcraig said:**
> Does Ubuntu need it's own computer parts store, like the Apple Store, where people know they can buy hardware that will work with Ubuntu? Yes.

Or a site that has *recommended* hardware.

Not a hardware compatibility site that lists all hardware and lists whether they work or not or what workarounds you need to get things working and "reviews" of hardware compatibility with Breezy and Hoary... i.e., not [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

A *recommended* hardware site. In other words, someone says, "I'm thinking about a laptop for Ubuntu." She goes to the site and sees the top three laptops that work for Ubuntu in terms of compatibility. Same for a webcam. Same for a music player. Same for a printer.

If you already have a peripheral, you can test it out with the live CD and see for yourself. If you are *buying* a new peripheral, however, all you want a compatible peripherals, not partially compatible peripherals or incompatible peripherals.

---

