---
title: "Using Ubuntu for Virtualization host"
date: 2012-01-20
forum: Virtualisation
---

### Post by Nick_C on 2012-01-20
Probably a couple of years since I last tried using Ubuntu for virtual hosting so I expect the situation has changed a bit since then. Can anyone advise me of current position regarding KVM or other virtualization on a Ubuntu host, how well does this work now?  I am wondering what is the best virtualization host to use on my main development workstation.

I have installed a test server using Hyper-V and here are the items I discovered do not work as expected:
Dual screen - no support for this via Hyper-V
Audio - no audio except a half workaround using remote desktop
USB - no USB passthrough
SCSI tape streamer - no SCSI passthrough so no way of using SCSI connected tape drives from any of the virtual operating systems

This is on my main development/test workstation so is intended to be hosting various flavours of Windowz, Windowz Server and a few different Linux versions.  For my particular situation dual screen support is quite important.

What is the current situation, is Ubuntu/QEMU/KVM suitable for this purpose yet or am I likely to encounter similar problems to Hyper-V.

Thanks,
Nick

---

### Post by dcstar on 2012-01-25
> **Nick_C said:**
> Probably a couple of years since I last tried using Ubuntu for virtual hosting so I expect the situation has changed a bit since then. Can anyone advise me of current position regarding KVM or other virtualization on a Ubuntu host, how well does this work now?  I am wondering what is the best virtualization host to use on my main development workstation.

I have installed a test server using Hyper-V and here are the items I discovered do not work as expected:
Dual screen - no support for this via Hyper-V
...........

What about this for dual screen?:

[http://ubuntuforums.org/showthread.php?t=1060977](http://ubuntuforums.org/showthread.php?t=1060977)

I believe that VMware Player also supports dual monitors, but you'd have to test that.

---

### Post by japzone on 2012-01-25
I find VirtualBox the best for Desktop Virtualization,
-Supports Hardware Virtualization
-Supports Seamless Mode(Have GuestOS's Windows work alongside HostOS's)
-Supports USB 1.0 and 2.0
-Supports Mounting ISOs as CD/DVD drives
-Supports Multiple Network options
-Supports Multiple Virtual Disk Types including VMware disks
-Supports Audio
-and more...

It supports SCSI internally but I'm not sure if that would allow you to use an External TapeDrive(At this point you really should backup that Data onto a New Medium anyway, Tape doesn't last forever and once backed up you can use any needed Virtual Medium).

For Dual/Multiple Monitor Setup follow these directions(Pretty Easy and Simple):[http://superuser.com/a/207291]("http://superuser.com/a/207291")

If you're looking for VM servers, VirtualBox does have a Headless mode but you may want to look at Xen or KVM. However, since I don't use them(I have no need for that) I can't give you any details or reccomendations on them.

---

### Post by Nick_C on 2012-01-29
> **japzone said:**
> I find VirtualBox the best for Desktop Virtualization,
-Supports Hardware Virtualization
-Supports Seamless Mode(Have GuestOS's Windows work alongside HostOS's)
-Supports USB 1.0 and 2.0
-Supports Mounting ISOs as CD/DVD drives
-Supports Multiple Network options
-Supports Multiple Virtual Disk Types including VMware disks
-Supports Audio
-and more...

It supports SCSI internally but I'm not sure if that would allow you to use an External TapeDrive(At this point you really should backup that Data onto a New Medium anyway, Tape doesn't last forever and once backed up you can use any needed Virtual Medium).

For Dual/Multiple Monitor Setup follow these directions(Pretty Easy and Simple):[http://superuser.com/a/207291]("http://superuser.com/a/207291")

If you're looking for VM servers, VirtualBox does have a Headless mode but you may want to look at Hypervisors like Xen or KVM. However, since I don't use them(I have no need for that) I can't give you any details or reccomendations on them.
Maybe I will have a look at VirtualBox then, have to admit I didn't much like the idea since it is now owned by Oracle.  However as nothing else I have tried actually completely works it might be worth a try.

As a matter of interest what do you run as a host OS, Linux or Windows.

---

### Post by Paddy Landau on 2012-01-29
I have found Virtual Box to be excellent (running Ubuntu as host). Don't worry; Oracle has done a great job with it.

Of course, it doesn't work quite the same way as a hypervisor. The default for Ubuntu is KVM.
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by Nick_C on 2012-01-30
Thanks Japzone and Paddy for your thoughts, perhaps I might be best to consider VirtualBox then.  I have to admit at the moment I was trying out KVM on Fedora but really making very little progress, seems to be one problem after another.

Time for me to dowmload the latest Ubuntu and try out VirtualBox running on that.  Bearing in mind that I will be accessing a number of NTFS partitions on attached disks and other Windows machine on the network, do you think this will cause me any problems with VirtualBox.

Admittedly it was a couple of years ago now but the last time I tried out VirtualBox I gave up because I couldn't get the SCSI adapter working to allow access to the tape streamers.

Nick

---

### Post by Paddy Landau on 2012-01-30
> **Nick_C said:**
> Time for me to dowmload the latest Ubuntu and try out VirtualBox running on that.  Bearing in mind that I will be accessing a number of NTFS partitions on attached disks and other Windows machine on the network, do you think this will cause me any problems with VirtualBox.
My experience of VirtualBox is superb, so I don't believe there will be a problem. You will need to set up your virtual machine to have a bridged network (it's in the machine's settings in VB) for the network to see it as a separate machine.

Your only concern is whether or not your computer is strong enough to run both Windows and Ubuntu at the same time. (Remember, Virtual Box is a virtual machine running on a host, unlike KVM, which is a hypervisor.)

For Windows 7 + Ubuntu, I would suggest anything less than 6Gb RAM would slow down your machine. Having said that, I tested the preview version of Windows 8 using Virtual Box on my Ubuntu 11.04 with just 4Gb RAM, and it ran acceptably (certainly not fast, but within reason).

---

### Post by japzone on 2012-01-30
I'm running VirtualBox on an Intel 1.66GHz Dual-Core with 4gb RAM and Ubuntu 11.04-PAE Kernal as Host. My expirience has been good with VB. I'm able to Easily run Windows 7 on a 1gb RAM allowance and 1 core access. Enabling the Hardware Virtualization options(Intel's VT-x and AMD's AMD-v) in the "System" options of the VM is very important as this gives you much better performance also for Windows guests make sure you enable 2D and 3D video exceleration in the "Display" Options. Once the VM is running you need to install the VB Guest Additions by going to "Devices-->VirtualBox Guest Additions" this willl mount a Installation-CD in the Guest and you need to use it to install some necessary Drivers for Features like Extra Display Settings(like Higher Res and Multi-Moniters) and Networking.

---

### Post by Paddy Landau on 2012-01-31
> **japzone said:**
> ... I'm able to Easily run Windows 7 on a 1gb RAM allowance and 1 core access...
Thanks for that information. Are you running 32-bit or 64-bit (mine is 64-bit, which tends to have higher RAM requirements)?

---

### Post by japzone on 2012-01-31
> **Paddy Landau said:**
> Thanks for that information. Are you running 32-bit or 64-bit (mine is 64-bit, which tends to have higher RAM requirements)?
Yeah, I'm running 32-bit as I only have a 32-bit CPU(Hence the PAE kernal), but from what I know and other PCs I've used, running a 64-bit OS in an Emulator isn't always worth it since you give a VM limited resources anyway. If you really need a 64-bit version of Windows running(ie: for testing a 64-bit Program, or similar) then do it, but I'd reccomend running 32-bit if you can so you get the best overall performance. 64-bit programs can be more efficiant and powerful but those features hardly shine when running on Limited resources. I never like to give my VMs alot of Resources as I'm usually performing other Tasks on my Host. In the end it's up to you and whether you want to sacrifice Host performance in favor of Guest Performance, but my opinion is that if you need to have that much performance in a VM you should just consider installing a Standalone Windows install and Dual-Boot your PC.

---

### Post by Paddy Landau on 2012-01-31
OK, thanks. I run VM's only to test, so it's not a big deal for me.

---

### Post by Nick_C on 2012-01-31
> **Paddy Landau said:**
> ...
Your only concern is whether or not your computer is strong enough to run both Windows and Ubuntu at the same time. (Remember, Virtual Box is a virtual machine running on a host, unlike KVM, which is a hypervisor.)

Not sure I understand the difference here; you say unlike KVM which is a hypervisor, but surely that is similar to VirtualBox.  KVM is a virtual machine running on a (Linux) host the same as VirtualBox is a virtual machine running on a host partition, what is the conceptual difference between the two.

---

### Post by Paddy Landau on 2012-01-31
> **Nick_C said:**
> Not sure I understand the difference here; you say unlike KVM which is a hypervisor, but surely that is similar to VirtualBox.  KVM is a virtual machine running on a (Linux) host the same as VirtualBox is a virtual machine running on a host partition, what is the conceptual difference between the two.
I must apologise. On rereading my notes, I realise that I have made a mistake. KVM is indeed a supervisor, not a hypervisor.

[http://en.wikipedia.org/wiki/Hypervisor](http://en.wikipedia.org/wiki/Hypervisor)
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by josir on 2012-01-31
Hi folks, just my two cents:

I use Ubuntu with KVM on 3 production machines. 

Oracle, Samba, Apache, PHP, Django, etc. They are VERY stable and hardware is very humble. I got 50 users online every day.

BUT, I just use Ubuntu on Host AND on Guest. I never tried old systems like Windows or similar :)

Probably VirtualBox is a better option on machines with heavy GUI. But for servers, it didn't work well for me. Several times, I got high latency on Oracle and Samba.

virsh and virt-manager are good tools and they are improving every year. 

Josir.

---

### Post by |{urse on 2012-01-31
Sounds like you might benefit from synergy.

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

oh... KVM not a KVM switch.

I hate that they named it KVM, confusing.

---

### Post by mikodo on 2012-01-31
> **japzone said:**
> Yeah, I'm running 32-bit as I only have a 32-bit CPU(Hence the PAE kernal), but from what I know and other PCs I've used, running a 64-bit OS in an Emulator isn't always worth it since you give a VM limited resources anyway. If you really need a 64-bit version of Windows running(ie: for testing a 64-bit Program, or similar) then do it, but I'd reccomend running 32-bit if you can so you get the best overall performance. 64-bit programs can be more efficiant and powerful but those features hardly shine when running on Limited resources. I never like to give my VMs alot of Resources as I'm usually performing other Tasks on my Host. In the end it's up to you and whether you want to sacrifice Host performance in favor of Guest Performance, but my opinion is that if you need to have that much performance in a VM you should just consider installing a Standalone Windows install and Dual-Boot your PC.Answered another question for me. :<). I have the processing power to use 64 bit, but have also decided to stay with 32 bit and PAE Kernals'. When I tried a Windows 7-64 bit guest with it, it still ran well with 4 gigs of memory on my machine, while allotting 2.5 gigs to the windows .vdi. I did enabling the Hardware Virtualization options(Intel's VT-x and AMD's AMD-v) in the "System" options of the VM to run it. All a moot point though, I am finished with Windows, as a casual user, I have no need.

---

### Post by japzone on 2012-01-31
> **josir said:**
> Hi folks, just my two cents:

I use Ubuntu with KVM on 3 production machines. 

Oracle, Samba, Apache, PHP, Django, etc. They are VERY stable and hardware is very humble. I got 50 users online every day.

BUT, I just use Ubuntu on Host AND on Guest. I never tried old systems like Windows or similar :)

Probably VirtualBox is a better option on machines with heavy GUI. But for servers, it didn't work well for me. Several times, I got high latency on Oracle and Samba.

virsh and virt-manager are good tools and they are improving every year. 

Josir.
Yeah as I said before, for Headless(ie GUI not very important) Server installs Xen and KVM are better options but if your using Desktop OSs(ie GUI very important) then VirtualBox is a much better option.

---

### Post by Nick_C on 2012-01-31
> **Paddy Landau said:**
> I must apologise. On rereading my notes, I realise that I have made a mistake. KVM is indeed a supervisor, not a hypervisor.

[http://en.wikipedia.org/wiki/Hypervisor](http://en.wikipedia.org/wiki/Hypervisor)
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

So what is likely to be faster KVM supervisor or VirtualBox hypervisor?

---

### Post by Nick_C on 2012-01-31
> **japzone said:**
> Yeah as I said before, for Headless(ie GUI not very important) Server installs Xen and KVM are better options but if your using Desktop OSs(ie GUI very important) then VirtualBox is a much better option.

Well in my case as this is going to be all on the same physical workstation machine then VirtualBox sounds like the best option.

Only next question is which Linux distro would provide the best performance of the client OSs, but I am probably asking that question in the wrong place here ;)

---

### Post by japzone on 2012-01-31
> **Nick_C said:**
> Well in my case as this is going to be all on the same physical workstation machine then VirtualBox sounds like the best option.

Only next question is which Linux distro would provide the best performance of the client OSs, but I am probably asking that question in the wrong place here ;)

That question depends on many things. If you have a 32-bit PC(Or OS) definitly make sure you get a Distribution that has a PAE kernal available (like Ubuntu) as it comes in very handy for VM's(Some OSs require PAE or 64-bit). Other than that pretty much the only thing you'd have to worry about it is how much Glitter and FX the GUI has as that can decrease the performance of a VM. On Ubuntu I'd suggest Turning down the GUI Effects or use Unity 2D(or UbuntuClassic/Gnome2 if you're on 11.04 or below). Pretty much any Distribution should work fine, just pick whatever OS you prefer.

---

### Post by Paddy Landau on 2012-02-01
> **Nick_C said:**
> So what is likely to be faster KVM supervisor or VirtualBox hypervisor?
They're both supervisors, not hypervisors.

I honestly don't know. [post=11654625]japzone's comments[/post] indicate that you probably want VirtualBox.

The best way to find out is by trying both, I guess.

---

### Post by Nick_C on 2012-02-01
Just found an interesting article comparing KVM vs VirtualBox vs XEN

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=1)

---

### Post by Paddy Landau on 2012-02-01
> **Nick_C said:**
> Just found an interesting article comparing KVM vs VirtualBox vs XEN

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=1)
That was interesting, thank you.

---

