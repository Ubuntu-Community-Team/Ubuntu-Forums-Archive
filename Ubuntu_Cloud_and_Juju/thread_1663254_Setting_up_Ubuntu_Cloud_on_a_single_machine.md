---
title: "Setting up Ubuntu Cloud on a single machine"
date: 2011-01-09
forum: Ubuntu Cloud and Juju
---

### Post by itfreaksnet on 2011-01-09
Hello all.

I'm glad I've come to Ubuntu Cloud community. I'm having some initial problems though. I've only one machine available for testing phase. It has enough power for a test cloud, CPU is VT capable , has 6 cores and 16 GB of RAM. I'm using Vmware Workstation for setting up controllers. However, node controllers doesn't work all the way because of nesting and KVM demands. I'm not very familiar with Ubuntu, Xen or KVM so I'm asking a question. Can I do setup as documented but instead of KVM use Xen?

---

### Post by raymdt on 2011-01-09
Hi Itfreaksnet and welcome,
yes you kannst use Xen with uec. Just install Xen on your frontend and change the Hypervisor in /etc/eucalyptus/eucalyptus.conf (The line  HYPERVISOR = "kvm" ).

Don't you have VT extension?? Or why do you want to use xen? Do you know that you can activate the VT in VMWare??

You even can use the test-uec-cd of Dustin kirkland (this is a live cd for testing eucalyptus without installation).

You can test the VT-xtension with
```

kvm-ok
#oder 
egrep ‘(vmx|svm)’ /proc/cpuinfo

```

Try and post your results :D

---

### Post by itfreaksnet on 2011-01-09
> **raymdt said:**
> Hi Itfreaksnet and welcome,
yes you kannst use Xen with uec. Just install Xen on your frontend and change the Hypervisor in /etc/eucalyptus/eucalyptus.conf (The line  HYPERVISOR = "kvm" ).

Don't you have VT extension?? Or why do you want to use xen? Do you know that you can activate the VT in VMWare??

You even can use the test-uec-cd of Dustin kirkland (this is a live cd for testing eucalyptus without installation).

You can test the VT-xtension with
```

kvm-ok
#oder 
egrep ‘(vmx|svm)’ /proc/cpuinfo

```

Try and post your results :D

Hello, raymdt

If you don't have VT capable CPU on host running Vmware workstation you cannot install 64 bit guests. But that particular 64 bit guest won't be VT capable. You cannot nest VT capability. You can still prove me wrong and make my day :)

So, kvm-ok tells me that CPU does not support KVM extensions. 

Using Xen would solve that issues, because with Kvm node controller i cannot start instances. I'm not quite sure how to install Xen node controller. Looking for some info in that way. I would like to stick with Ubuntu 10.10 for this issue.
best regards, Stoz.

---

### Post by raymdt on 2011-01-09
> 
If you don't have VT capable CPU on host running Vmware workstation you cannot install 64 bit guests

That's right. But you wrote
 
> 
 It has enough power for a test cloud, **CPU is VT capable** , has 6 cores and 16 GB of RAM


So if your are sure that your cpu CPU Capable is, then you have to activate it in your computer's BIOS

Here is a howto about xen on ubuntu

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by itfreaksnet on 2011-01-09
Hey, raydtm,

we are talking about running controller node as a VM under Vmware workstation not on bare metal.

---

### Post by raymdt on 2011-01-09
Hi,
i understand that you're trying to run your VM Node on VMWare. And this is reason why i asked if your "Bare Metal" is VT capabe, since VT is not enabled by default under WMWare. To enable it, you just need  to  add this line  to  your *.vmx file

```

monitor_control.vt64 = TRUE
#or 32 if you use 32 Bits guest

```PS:
Graziano(one of the eucalyptus's guys ) said:

> 
we don't advice to run eucalyptus in a vm and we don't support it  directly since the configuration can be fairly complex and you may be  limited in the networking mode options you can choose. But we know of  users that managed to do just that.
[http://open.eucalyptus.com/forum/can-i-install-eucalyptus-vmware-server](http://open.eucalyptus.com/forum/can-i-install-eucalyptus-vmware-server)

But you can try it and share your experience :D.

---

### Post by itfreaksnet on 2011-01-13
> **raymdt said:**
> Hi,
i understand that you're trying to run your VM Node on VMWare. And this is reason why i asked if your "Bare Metal" is VT capabe, since VT is not enabled by default under WMWare. To enable it, you just need  to  add this line  to  your *.vmx file

```

monitor_control.vt64 = TRUE
#or 32 if you use 32 Bits guest

```PS:
Graziano(one of the eucalyptus's guys ) said:

[http://open.eucalyptus.com/forum/can-i-install-eucalyptus-vmware-server](http://open.eucalyptus.com/forum/can-i-install-eucalyptus-vmware-server)

But you can try it and share your experience :D.
Hello,

Thanks for links. However you should do homework with nesting hardware VT. best regards, Stoz

---

### Post by itfreaksnet on 2011-01-14
then again, if we look at xen 4.0.1 requirements, 
[http://wiki.xensource.com/xenwiki/Xen4.0](http://wiki.xensource.com/xenwiki/Xen4.0)

"Xen PV (paravirtualized) guests (Linux, Solaris, BSD, Netware) are supported without CPU/hardware virtualization extensions, so Xen can be used also on old hardware. Xen 32bit PV guests need to be PAE."

it looks like we could install Xen 4.0.1 inside VM. Is it possible that I make a mistake during compiling.

---

