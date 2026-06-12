---
title: "Xen"
date: 2009-11-11
forum: Virtualisation
---

### Post by Pink October on 2009-11-11
I was looking at this page [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

It seems a nice guide on how I would go about installing xen. I have a slight problem though.  I don't have a wired connection. Now I now know how to get my wireless adaptor reporting as eth0, but  don't have much of a clue how to get a virtual machine connecting to the wireless connection.

I think I need to use an internal network bridge with NAT, or use routed setup. The thing is I really don't fully understand these. Does anyone here have a clue about how I could set this up?

I know I could use vmware, but I was thinking about having more than 1 vm, for testing purposes. I'd also like some experience setting xen up. So if anyone has any ideas on how I could go about setting this up I would be grateful. 

Thanks:)

---

### Post by bodhi.zazen on 2009-11-11
Moved to Virtualization.

If you have the hardware, I advise you go with KVM.

Virtualbox is next easiest to run, followed by VMWare.

You may run multiple guests with KVM, VBox, or VMWare.

The Xen and Openvz kernel patches are supported in Ubuntu 8.04, but not 8.10, 9.04, or 9.10. You can run Ubuntu as a guest in OpenVZ or Xen.

---

### Post by Pink October on 2009-11-11
Thanks, not heard of kvm before, but it does say this on the documentation page.

**Warning:** Network bridging will not work when the physcial network device (eg eth1, ath0) used for bridging is a wireless device (eg ipw3945), [as most wireless device drivers do not support bridging]("http://www.linuxfoundation.org/en/Net:Bridge#It_doesn.27t_work_with_my_Wireless_card.21")!

So how are you meant to get past this?

---

### Post by bodhi.zazen on 2009-11-11
> **Pink October said:**
> Thanks, not heard of kvm before, but it does say this on the documentation page.

**Warning:** Network bridging will not work when the physcial network device (eg eth1, ath0) used for bridging is a wireless device (eg ipw3945), [as most wireless device drivers do not support bridging]("http://www.linuxfoundation.org/en/Net:Bridge#It_doesn.27t_work_with_my_Wireless_card.21")!

So how are you meant to get past this?

Funny you should ask :twisted:

[http://blog.bodhizazen.net/linux/bridge-wireless-cards/](http://blog.bodhizazen.net/linux/bridge-wireless-cards/)

There are other KVM tutorials you may find helpful on my blog as well.

---

### Post by tapas_mishra on 2009-11-12
What you said is correct  I am not clear on a few things 
1) what is Dom0 
2) Many a times a kernel is compiled for Dom0 what is that
like doing    	 	 	 	 	 	  compiling pv_ops dom0 kernel: make menuconfig && make bzImage && make modules && make modules_install && cp -a arch/x86/boot/bzImage /boot/vmlinuz-version && create initrd for the dom0 kernel
 Why do we need to compile a kernel for Dom0 is it different from the one shipped with xen packages 
3) There was an option told by some one that    	 	 	 	 	 	  no need to build the default linux-2.6.18-xen.hg kernels that ship with xen 3.4.2
   	 	 	 	 	 	  installing xen: tar zxvf xen-3.4.2.tar.gz && cd xen-3.4.2 && make xen && make tools && make stubdom
  kernel work
    	 	 	 	 	 	  and you have the stuff in dist/install/     	 	 	 	 	 	  then you need to install the hypervisor
   	 	 	 	 	 	  and xen tools    	 	 	 	 	 	  and configure grub bootloader
 
 
   	 	 	 	 	 	  to boot xen hypervisor     	 	 	 	 	 	  and load dom0 kernel
What is all the above described and where can I find more information

---

### Post by bodhi.zazen on 2009-11-12
You will have ot read the Xen documentation.

Dom0 is the host OS.
DomU are the guests.

Ubuntu 8.04 supports Dom0 , ubuntu 8.10, 9.04, and 9.10 do NOT.

DomU (Ubuntu as a Xen guest) is supported on all versions of Ubuntu.

So if you want to install Xen , you need to use a supported host, see the Xen site for details.

---

### Post by tapas_mishra on 2009-11-12
> **bodhi.zazen said:**
> You will have ot read the Xen documentation.

Dom0 is the host OS.
DomU are the guests.

Ubuntu 8.04 supports Dom0 , ubuntu 8.10, 9.04, and 9.10 do NOT.

DomU (Ubuntu as a Xen guest) is supported on all versions of Ubuntu.

So if you want to install Xen , you need to use a supported host, see the Xen site for details.

Thanks a lot for the reply ,I had been googling since I was getting a lot of errors as I had tried to install Xen or say compile a Dom0 kernel on it from jeremy repository on the unsupported OS,
and since from my post it is absolutely clear that I am a novice as far as Xen is concerned 
I came across a good book about XEN 
A hands on guide to the art of virtualization Jeanna Mathews
[http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3](http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3)

I am posting the above link so that if some one  like me is searching for a lot of basic questions among documentations etc does not get confused by the blogs on internet everything available for free does not leads to the right solution.But still it has a lot of support on the community and a good place to ask questionbs is [http://gmane.org](http://gmane.org) the mailing list about xen users it is here 
[http://lists.xensource.com/xen-users](http://lists.xensource.com/xen-users)
I hope this helps to a lot of people like me.

---

