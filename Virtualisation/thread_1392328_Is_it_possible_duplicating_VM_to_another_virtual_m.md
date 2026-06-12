---
title: "Is it possible duplicating VM to another virtual machine"
date: 2010-01-28
forum: Virtualisation
---

### Post by satimis on 2010-01-28
Hi folks,

host – Fedora 12 64bit
KVM – virtualization software

I have 8 VMs on this virtual machine running different OS. Can VMs be moved/copied to another PC of similar hardware config running Fedora 12 (64bit) as host and KVM

If Yes, whether copying following files,

e.g. copying following files and paste them on the same /path/to/directory

[root@fedora12 satimis]# ls -l /etc/libvirt/qemu/```

total 52
...
-rw------- 1 root root 1293 2010-01-14 22:48 vm01.xml
-rw------- 1 root root 1293 2010-01-11 17:19 vm02.xml
-rw------- 1 root root 1302 2010-01-11 19:11 vm03_ub9164.xml
-rw------- 1 root root 1273 2010-01-12 02:09 vm04_f1264.xml
-rw------- 1 root root 1193 2010-01-23 02:21 vm05_wser08.xml
-rw------- 1 root root 1368 2010-01-25 22:44 vm06_wser08.xml
-rw------- 1 root root 1389 2010-01-27 11:04 vm07_wser0832.xml
-rw------- 1 root root 1370 2010-01-27 22:23 vm08_vista32.xml
...

```


[root@fedora12 satimis]# ls -l /home/satimis/ | grep vm```

-rwxr-xr-x 1 root root 12884901888 2010-01-22 07:56 vm03_9164.qcow2

```


[root@fedora12 satimis]# ls -l /home/satimis/VM/ | grep vm```

-rwxr-xr-x 1 root root 12884901888 2010-01-23 08:19 vm01.qcow2
-rwxr-xr-x 1 root root 12884901888 2010-01-23 08:16 vm02.qcow2
-rwxr-xr-x 1 root root 12884901888 2010-01-26 22:33 vm04_f1264.qcow2

```


[root@fedora12 satimis]# ls -l /home/satimis/VM/VMWIN/ | grep vm```

-rwxr-xr-x 1 root root 32212254720 2010-01-23 06:55 vm05_wser08.qcow2
-rwxr-xr-x 1 root root 32212254720 2010-01-27 23:07 vm06_wser08.qcow2
-rwxr-xr-x 1 root root 32212254720 2010-01-27 12:45 vm07_wser0832.qcow2
-rwxr-xr-x 1 root root 32212254720 2010-01-28 00:14 vm08_vista32.qcow2

```


What about if the host is running different OS, say Debian etc. can it also work?

TIA

B.R.
satimis

---

### Post by HermanAB on 2010-01-30
Typically, you just shut the virtual system down, then make a tar ball of the whole VM subdirectory and copy it to another machine.  That is the beauty of VMs.

---

### Post by satimis on 2010-01-30
> **HermanAB said:**
> Typically, you just shut the virtual system down, then make a tar ball of the whole VM subdirectory and copy it to another machine.  That is the beauty of VMs.

Hi

Thanks for your advice.

The host OS has bugs.  I am going to reinstall it.  To save time I need to retain the VM

B.R.
satimis

---

### Post by HermanAB on 2010-02-01
With some effort, you can usually even copy a VM to a completely different virtualizer, e.g. VMware to Vbox or KVM, but the conversions don't always work.

---

### Post by satimis on 2010-02-01
> **HermanAB said:**
> With some effort, you can usually even copy a VM to a completely different virtualizer, e.g. VMware to Vbox or KVM, but the conversions don't always work.

Hi HermanAB,

Pointer would be appreciated.  Thanks

Tried coping VM to same virtualizer, KVM, with host running different OS without problem.

B.R.
satimis

---

### Post by HermanAB on 2010-02-03
Here you go:
```
http://www.google.com/search?q=convert+vmware+to+vbox&ie=utf-8&oe=utf-8&aq=t&rls=com.mandriva:en-US:unofficial&client=firefox-a
```

---

### Post by satimis on 2010-02-03
> **HermanAB said:**
> Here you go:
```
http://www.google.com/search?q=convert+vmware+to+vbox&ie=utf-8&oe=utf-8&aq=t&rls=com.mandriva:en-US:unofficial&client=firefox-a
```

Hi HermanAB,

Thanks for your link.

I need converting KVM (qcow2) to VirtualBox (vdi) from one PC to another PC.  Google didn't find many threads concerned, instead the other way around.  However it found only one;

How to Convert a KVM to a VDI
[http://www.ehow.com/how_5856610_convert-kvm-vdi.html](http://www.ehow.com/how_5856610_convert-kvm-vdi.html)

If I read the article correctly it seems both KVM and VirtualBox are running on the same PC, VirtualBox running on KVM.  Do you have any idea/suggestion where can I find relevant documentation?  TIA.


B.R.
satimis

---

