---
title: "Native speed hardware VM?"
date: 2012-08-08
forum: Virtualisation
---

### Post by HadrianKross on 2012-08-08
After some research, I was wondering if there is a native speed, (hardware) virtualization option, that allows bios level functionality--i.e. boot from cd, affect virtual bios, or other power-on options, etc.

While there are some virtual machines that advertise native speeds, they seem to require some form of OS install before booting--so pretty much os virtualization.

If there aren't any that allow native speeds, what are the fastest, open source (GPL) solutions available on x86 hardware--specifically on an x86/linux host virtualizing any other platform/linux combination that will run the quickest? (That might actually be another question, "Which hardware platform/architecture runs what distro the quickest?") At first glance it seems that it should be an x86 VM, but given the number of variables in virtual machines available, and the number of options available to implement them, this is somewhat difficult to tell without actually testing all of them.

Be happy to benchmark a few of these if some testing is required; however, I was hoping to narrow down the number of options beforehand.

Thanks

---

### Post by CharlesA on 2012-08-10
Using a Baremetal hypervisor will get you as close to native speed as possible.

I suggest looking into KVM, but there is also ESXi, Xen and Proxmox.

---

### Post by HadrianKross on 2012-08-17
I had thought about trying Xen (mainly because there's a .deb for it), but I suppose to paraphrase, I'm looking for the quickest option that will run on x86 and still be able to boot Live CD's.  Are there any linux on linux native speed options that might allow this?

---

### Post by CharlesA on 2012-08-17
Are you trying to boot the host machine off a livecd, or the VM itself?

Is the host going to be a 32-bit machine, or 64-bit machine?

Does it support hardware virtualization extensions?

Those are the questions you need to ask before deciding on a virtualization solution.

---

### Post by HadrianKross on 2012-08-17
host == x86, 32 bit
guest == anything that will boot a livecd (even a software os solution/tweak, etc.)

whether a hardware vm or software (os) vm, the idea is the closest to native speed as possible

---

### Post by CharlesA on 2012-08-17
What CPU are you planning on using? As far as I know you would need one that supports hardware virtualzation extensions to use KVM.

See here:
[http://www.linux-kvm.org/page/FAQ#How_can_I_tell_if_I_have_Intel_VT_or_AMD-V.3F](http://www.linux-kvm.org/page/FAQ#How_can_I_tell_if_I_have_Intel_VT_or_AMD-V.3F)

For how to check.

---

### Post by HadrianKross on 2012-08-18
Probably amd 32bit, hence the need for speed

it appears my current processor does support VT, though I think it may be underclocked...

---

### Post by CharlesA on 2012-08-18
Unless you are planning on reusing an old box (which isn't a very good idea for virtalization), go with a 64-bit CPU - I haven't seen a 32-bit one in a while.

---

### Post by HadrianKross on 2012-08-19
Actually the processor does not support VT (no [FONT=monospace][/FONT]vmx or svm flag)...

I suppose that narrows down the list significantly doesn't it?

I guess 64bit would be better for this, but there's probably (hopefully) a way to get one of the native software vm's to somehow boot a live cd/live iso/etc.

Going to be swapping out multiple cd/dvd's so I would much prefer to do that in a vm or emulator--having to actually reboot multiple times for a few command line commands for each would be a waste.

--

So now that you know what I'm after in terms of a project, any more info for the original question: Are there any hardware virtual machines/baremetal hypervisors that provide very close to native speeds with a linux x86 host?

---

### Post by CharlesA on 2012-08-19
The best you can probably do is VirtualBox, unless you want to try KVM, but without hardware virtualization extensions, both would have to default to software and be slower then native.

I use Virtualbox, myself.

---

### Post by HadrianKross on 2012-08-21
Cool thanks.

Also, my current processor does support vme but not vmx or svm.

--

Anyone think of any off the wall solutions for the native software linux on linux option?

---

