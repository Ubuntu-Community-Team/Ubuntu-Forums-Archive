---
title: "VM: amd64 or i386"
date: 2010-04-25
forum: Virtualisation
---

### Post by ariek on 2010-04-25
Hi,

Because I want to go for the best performance in my vSphere environment, I would like to know which OS-version to use for Ubuntu server 10.04. amd64, without paravirtualization (not possible, unfortunately) or i386 with paravirtualization. The application, or server function used is mainly LAMP.
I have tested 10.04 for a bit, but again I am impressed. Each version seems to go faster.
Are there any official recommendations or figures?

---

### Post by stephanhughson on 2010-05-08
I've also looked in to this before, as I have to run Ubuntu under VMware at work. I'd recommend reading this: [http://blogs.vmware.com/guestosguide/2009/09/vmi-retirement.html](http://blogs.vmware.com/guestosguide/2009/09/vmi-retirement.html)

When I hear paravirtualisation, I think of paravirtualised disk and networking, primarily. The VMware "vmi" thing isn't quite the same, I think and they're phasing it out, so it's probably best to avoid it at the moment.

So overall I would say, go with the 64 bit install. That way you'll have more flexibility in future as you'll be able to use large amounts of ram more effectively if you ever need to.

You can also go for Ubuntu JeOS which is a very minimal installation of Ubuntu especially for virtual machines. You should get good performance, although I'm not sure how much faster it would actually be (if at all). It's definitely smaller than a normal install though if nothing else.

---

### Post by ariek on 2010-05-09
> **stephanhughson said:**
> I've also looked in to this before, as I have to run Ubuntu under VMware at work. I'd recommend reading this: [http://blogs.vmware.com/guestosguide/2009/09/vmi-retirement.html](http://blogs.vmware.com/guestosguide/2009/09/vmi-retirement.html)

When I hear paravirtualisation, I think of paravirtualised disk and networking, primarily. The VMware "vmi" thing isn't quite the same, I think and they're phasing it out, so it's probably best to avoid it at the moment.

So overall I would say, go with the 64 bit install. That way you'll have more flexibility in future as you'll be able to use large amounts of ram more effectively if you ever need to.

You can also go for Ubuntu JeOS which is a very minimal installation of Ubuntu especially for virtual machines. You should get good performance, although I'm not sure how much faster it would actually be (if at all). It's definitely smaller than a normal install though if nothing else.
Hi Stephan,

Thanks for your reply. I have been running Ubuntu on ESX for a while, and was wondering how others were thinking about it. To my experience the best performance for Ubuntu server is with using the jeos option, and 32 bit with paravirtualisation. Memory is no issue anymore, because since Ubuntu 8.10, there's no limit for 32 bit systems.
Also, I find the paravirtualised systems responding a lot snappier than its 64 colleague, which I do find a little odd.

---

### Post by dcstar on 2010-05-09
> **ariek said:**
> Hi Stephan,

Thanks for your reply. I have been running Ubuntu on ESX for a while, and was wondering how others were thinking about it. To my experience the best performance for Ubuntu server is with using the jeos option, and 32 bit with paravirtualisation. Memory is no issue anymore, because since Ubuntu 8.10, there's no limit for 32 bit systems.
Also, I find the paravirtualised systems responding a lot snappier than its 64 colleague, which I do find a little odd.

One assumes you are using the Virtual kernels in your Ubuntu VMs.

---

### Post by stephanhughson on 2010-05-09
You mentioned that there's no limit for memory on 32 bit Ubuntu.

If you are using a 32 bit kernel, Support for large amounts of memory (above 4 GB) will come from PAE being enabled in the kernel. [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension) . PAE isn't as efficient as accessing the extra memory normally, so 64 bit wins there, but only if you are accessing more than 4GB of RAM.

As 64 bit binaries are bigger and take up slightly more space both in RAM and on the disk, in theory 32 bit binaries are faster, but there's really not much in it. This guy has done benchmarks for both: [http://www.osnews.com/story/5768](http://www.osnews.com/story/5768) and the difference is tiny.

Overall, having the flexibility to upgrade to more than 4GB without any performance decrease is the reason I choose 64 bit for all of my VMs.
If you are a Windows user too, Microsoft also seem to be going the 64 bit route, with Windows 2008 R2 only being available for 64 bit, for example. It's just the way forward I reckon :P

---

### Post by ariek on 2010-05-09
Thanks for the extra information. Of course in a couple of years time 64 bit will be the standard, just as 32 bit over 16 bit, years back.

The article you pointed out is interesting, specifically the conclusion:

*In the end it's the library and compiling issues that are the most compelling reasons to stay with 32-bit binaries, and not so much performance or size.  I think it's safe to say that you're not missing out by going with the simpler-to-manage 32-bit binaries, unless your application can specifically benefit from 64-bit.   *

Another thing about the article is that it is based on the UltraSPARC platform for Solaris 9, hardware.
One of the major differences in my assumption is the fact of paravirtualisation, which is only available for the 32 bit platform. Check it yourself, and test 2 VM's with the Virtual Machine (kernel) option, with VMware tools, and the option for paravirtualisation for the i386 VM.

---

### Post by stephanhughson on 2010-05-09
VMware say that paravirtualisation is "no longer required" for 64 bit.

I think they are talking about the whole operating system being paravirtualised, not just drivers for disk, networking etc.

I don't know .... :guitar:

I like the way I've got it now though, 64 bit host, 64 bit VMs, with paravirtualised networking for better performance. Paravirtualised disk (supposed to be better performance) and parts of the memory from the vms which is the same being shared, so less RAM is used overall.

Pretty cool considering it costs nothing!

---

