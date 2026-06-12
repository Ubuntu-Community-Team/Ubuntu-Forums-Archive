---
title: "Qemu-kvm"
date: 2016-03-06
forum: Virtualisation
---

### Post by syednoorullah92 on 2016-03-06
hey i am new to virtualization can any one give me complete tutorial to configure libvmi and kvm on ubuntu i need detail tutorial... and one more question can i use libvmi for introspection with windows as a base OS if yes how??

---

### Post by MAFoElffen on 2016-03-06
Is this the info you are lokking for?
[An Introduction to Virtual Machine Introspection Using LibVMI]("https://www.acsac.org/2014/workshops/mmf/Bryan-Payne-An%20Introduction%20to%20Virtual%20Machione%20Introspection%20Using%20LibVMI.pdf")
[Simplifying Virtual Machine Introspection Using LibVMI]("http://prod.sandia.gov/techlib/access-control.cgi/2012/127818.pdf")

For being new to virtuslization, that is some pretty advanced subjects to be diving into, all at once. Are you doing vulnerability testing?

---

### Post by syednoorullah92 on 2016-03-06
hey its introduction to libvmi . i know about libvmi but i don't know how to configure it on ubuntu??

---

### Post by MAFoElffen on 2016-03-06
If you had said with Xen... But you said with KVM, so you have some work to do ... From the [libvmi github homepage]("https://github.com/libvmi/libvmi"):
> 
**KVM Support**
If you would like LibVMI to work on KVM VM's, you must do some additional setup. This is because KVM doesn't have much built-in capability for introspection. For KVM support you need to do the following:

Go down to the KVM Support section and it has instructions for installation and configuration...

The project used to be at Google and had since moved to [www.libvmi.com]("http://libvmi.com/docs/gcode-install.html"). (<-- Link to the installation and configuration page) 

Other than that, the only "tutorials" I've seen on libvmi have been using it with Xen as the hypervisor.

---

### Post by syednoorullah92 on 2016-03-06
Can you help with this 

[TABLE="class: cke_editor"]
[TR]
[/TR]
[TR]
[/TR]
[/TABLE]


        I am trying to create virtual machine on ubuntu using virtual machine manager i have installed kvm
        but when i use display vnc for virtual machine it shows the following error and when i use display spice it shows another error which is second one


        ERROR #1

        unable to complete install: 'internal error: process exited while connecting to monitor: 2016-03-06T10:09:29.534755Z kvm-spice: -msg timestamp=on: Unsupported machine type
        Use -machine help to list supported machines!
        '

        Traceback (most recent call last):
        File "/usr/share/virt-manager/virtManager/asyncjob.py", line 91, in cb_wrapper
        callback(asyncjob, *args, **kwargs)
        File "/usr/share/virt-manager/virtManager/create.py", line 1819, in do_install
        guest.start_install(meter=meter)
        File "/usr/share/virt-manager/virtinst/guest.py", line 403, in start_install
        noboot)
        File "/usr/share/virt-manager/virtinst/guest.py", line 467, in _create_guest
        dom = self.conn.createLinux(start_xml or final_xml, 0)
        File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3497, in createLinux
        if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
        libvirtError: internal error: process exited while connecting to monitor: 2016-03-06T10:09:29.534755Z kvm-spice: -msg timestamp=on: Unsupported machine type
        Use -machine help to list supported machines!

        ERROR # 2

        unable to complete install: 'unsupported configuration: spice graphics are not supported with this QEMU'

        Traceback (most recent call last):
        File "/usr/share/virt-manager/virtManager/asyncjob.py", line 91, in cb_wrapper
        callback(asyncjob, *args, **kwargs)
        File "/usr/share/virt-manager/virtManager/create.py", line 1819, in do_install
        guest.start_install(meter=meter)
        File "/usr/share/virt-manager/virtinst/guest.py", line 403, in start_install
        noboot)
        File "/usr/share/virt-manager/virtinst/guest.py", line 467, in _create_guest
        dom = self.conn.createLinux(start_xml or final_xml, 0)
        File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3497, in createLinux
        if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
        libvirtError: unsupported configuration: spice graphics are not supported with this QEMU

---

### Post by MAFoElffen on 2016-03-06
I ask again, what version of what OS are you trying to install as a guest? Error says:
> 
 Unsupported machine type, Use -machine help to list supported machines!

But if you look at the errors closely, both errors say you are trying to use kvm-spice. Virt-manager uses kvm-vnc as a default.*** I install all my vm's as kvm-vnc graphics. Some I say as Cirrus. Others I say as VGA or VMVGA. With those two I can set Xorg.conf files with higher resolution graphics, without having to setup a GPU passthrough to the host.

But, you know, installation options really depend on the guest OS that I am trying to install. Rare, but some, I have to tweak KVM CPU setings. The CPU settings that you can tweak, depend on the capabilities of the host's CPU. Some I have to install specific kvm virtio drivers.

Your errors are asking you to look at the supported OS list, which better would to look at the [KVM Guest Support]("http://www.linux-kvm.org/page/Guest_Support_Status") page.

One tip on posting here. Go back to your posts where you posted output. Select Edit. Go to Advance edit. Select/Highlight the output text... and press the "[SIZE=5]**#**[/SIZE]" icon. (code tags). That is how we post commands and output here. Just trying to keep you from getting a warning from the staff. In reality, if saves space, is easier to read, and keeps characters from being mistakenly translate by the forums software.

Note *** To use kvm-spice you actually have to install additional pieces to the kvm hypervisor and confgure it, and then the install pieces and configure into VM Guest to use Spice. But kvm-vnc works with virt-manager out-of-the-box.

---

### Post by syednoorullah92 on 2016-03-06
**i am using ubuntu-15.10 as host and trying install both win 7 and ubuntu-15.10 as guest but showing the errors already mentioned  above**
> Hypervisor Detail on VM Manger
Hypervisor: kvm
emulator:/usr/bin/kvm-spice
firmware: default
architecture: x86_64

---

### Post by MAFoElffen on 2016-03-07
Refer back to your other thread, I am only going to answer the original thread, with the original problem, The second thread got closed for being a duplicate. This is #3 on the same thing right?:
[http://ubuntuforums.org/showthread.php?t=2316211](http://ubuntuforums.org/showthread.php?t=2316211)

---

