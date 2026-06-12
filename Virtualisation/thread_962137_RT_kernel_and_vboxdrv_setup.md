---
title: "RT kernel and vboxdrv setup"
date: 2008-10-29
forum: Virtualisation
---

### Post by JKyleOKC on 2008-10-29
My most recent updates to 8.04.1 added the RT kernel to my list of choices, but when I installed VirtualBox 1.6 from Sun I was running the generic kernel and that's what vboxdrv created the driver module for.

Now if I boot into the RT kernel and run VirtualBox, I get the "no driver" message that tells me to run vboxdrv setup again.

However when I do, it finishes almost immediately and tells me to check the install.log file to find out what went wrong. The log says that the program was unable to find the kernel sources.

So I installed the sources, via synaptic, and tried again.

Same error message. I have two questions: first, why did the initial vboxdrv setup (run during installation) work without any error, and second, how can I tell the program where to find the sources it's complaining about?

Aside from this problem, I'm finding 1.6 to be quite suitable for my needs. USB and networking both seem to be fully functional; once I work out all the kinks, my plan is to do away with double-booting and use VMs for all my Windows support work, eventually reducing the number of physical systems in my home office and thus trimming back my electric bill...

Additional info: Re-installing VirtualBox 1.6 under the RT kernel gives the same error, but then re-installing under the generic kernel works. Could this be a bug in the RT kernel (both are 2.6.24.21)? Or could it be simply that there's a conflict with something that the vboxdrv script doesn't recognize?

---

### Post by just_mcateer on 2008-11-10
I'm having pretty much the same issue with the Server kernel. I am using VirtualBox 2.0.4.

The error message I find in the compile log produced by vboxdrv setup says that you can set the directory manually by providing a value for KERNEL_DIR. However, that did not seem to work for me.

I looked in the make file and the default directory where it is looking for kernel source is /usr/src/linux, so I make a link from there to the source (which I had to un-tar after installing package 'linux-source'). Then the log puked out a bunch of 'make' errors complaining about the kernel source not being configured, etc.

I am still working through this, so if anyone has any info, please let me know.

Thanks,
Justin

---

