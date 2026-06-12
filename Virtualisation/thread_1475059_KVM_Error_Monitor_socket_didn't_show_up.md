---
title: "KVM Error Monitor socket didn't show up"
date: 2010-05-06
forum: Virtualisation
---

### Post by JohnH on 2010-05-06
Hi there,

Can anyone tell me what this might mean (other than my vm won't start).

```
raceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused
```

---

### Post by JohnH on 2010-05-07
Its okay,

I've gone back to Virtual Box even though I like the Aemu/KVm way of doing things.

Aemu had graphics issues that I couldn't fix, and KVM just wouldn't boot (after a host shut down/reboot).

John

---

### Post by gunksta on 2010-05-19
I had something very similar happen. I in more places that I can remember. I finally looked in the log file associated with the VM, and noticed that virt-manager was failing to locate /dev/sr0, which is my CD-ROM drive.

Basically, virt-manager is not smart enough to accept that a drive could be empty. Thus, booting results in an error because of a missing device. If you go into the VM settings and remove that offending hardware, virt-manager will happily start your VM.

A little ridiculous, but that's what happened to me.

YMMV, of course.

---

### Post by jacques1 on 2010-07-03
The problem is more general than just the cdrom (virt-manager 0.8.2  ; 2.6.32-23-generic ; lucid/10.4) : you'll get the same message if the disk containing the image is unavailable (in my case, not mounted).

Anyway, allways have a look at /var/log/libvirt/qemu/virtual_machine_name.log before seaching further.

The problem will also araise if you move the image file and modify the name of the disk in the /etc/libvirt/qemu/virtual_machine_name.xml file accordingly: in this case, restarting the graphical virtual machine manager won't be enough. You'll have to restart the underlying service : "service libvirt-bin restart" for instance.

---

### Post by gunksta on 2010-07-06
Since turning off the CD-ROM, I haven't had any problems. I think it's silly for the system to not be smart enough to figure out if there is a CD in the cd-tray or not and to adjust accordingly, but libvirt is younger than some of the competition and it shows from time to time.

---

### Post by jetole on 2010-07-23
> **jacques1 said:**
> The problem will also araise if you move the image file and modify the name of the disk in the /etc/libvirt/qemu/virtual_machine_name.xml file accordingly: in this case, restarting the graphical virtual machine manager won't be enough. You'll have to restart the underlying service : "service libvirt-bin restart" for instance.

jacques1, editing the XML file directly should not work since, according to the docs, you should never do this. I don't use the virsh GUI that some of you have mentioned (since I run my VM on remote servers in the data center) however, from the console, to edit the configuration file, you should run "virsh edit my_host" where my_host is the name of the vm you want to edit the configuration file for. I don't believe this makes real time changes (i.e. it won't change something on a running VM) but if you reboot the host, then it should make the change. Perhaps just to be safe, I shut down the host then start the host.

Also, "virsh edit" is safer. It will only read lines it understands back into the running VM so any typos won't crash your entire VM setup.

---

### Post by sh1ny on 2010-07-23
> **JohnH said:**
> Hi there,

Can anyone tell me what this might mean (other than my vm won't start).

```
raceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused
```

Let me guess, you just upgraded from karmic -> lucid ?

In that case, open each virtual machine and look below :

```
<disk type='file' device='disk'>
```

for 

```
<driver name='qemu' type=''/>
```

If you see that, change it to :

```
<driver name='qemu' type='raw'/>
``` 

if you use raw images or to :

```
<driver name='qemu' type='qcow2'/>
```

If you use qcow2 format.

Let me know if this helps.

---

### Post by z06steve on 2010-08-19
gunksta

Just spent 2 days building 2 guests and nearly had a heart attack when after a kernel update and reboot neither guest would start. This is exactly what happened to me just now and your suggestion fixed it.

Thanks for the find and share.

---

### Post by gunksta on 2010-08-20
Glad it helped!

I do love virtual machines. I've been playing around with Minix. They just released version 3 and it's quite interesting. I don't have X installed because I want to keep it small and light but it is interesting.

And -- I find it really amusing to run Minix in a virtual machine, on top of Linux. There is a beautiful symmetry to it all.

---

### Post by kurtisj on 2010-10-26
Surprisingly, the latest version continues to have this problem. If you shut down the machine, disconnect a usb cdrom and startup the vm back up, for example, you will see the same libvirt error. Plug the device back in prior to starting the vm and it starts up ok.

---

### Post by kilmarnock on 2010-11-19
the entries are already there.

 <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>

what else can I do? I removed all end every unneeded device. 


[Fr, 19 Nov 2010 16:36:16 virt-manager 18475] DEBUG (engine:586) Starting vm 'win7'.
[Fr, 19 Nov 2010 16:36:46 virt-manager 18475] DEBUG (error:79) Uncaught Error: Error starting domain: monitor socket did not show up.: Connection refused : Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused


where is that monitor socket?

Felix

---

### Post by gunksta on 2010-11-21
Drop to a terminal, and try this. Tell me what happens. Note - You need to adjust this to fit your environment.
```
sudo kvm /var/lib/libvirt/images/WinXP.img
```

---

### Post by paulv8 on 2011-01-05
You will run into this problem as well when you have a USB drive attached to the VM that is not switched on/ plugged in.

After removing the non-existing USB drive I could boot the VM machine again

---

### Post by gunksta on 2011-01-06
Someone is going to make a lot of money selling a KVM for Dummies book. :lolflag:

I so rarely use USB keys that I haven't actually bumped into this, but it makes perfectly good sense.

---

