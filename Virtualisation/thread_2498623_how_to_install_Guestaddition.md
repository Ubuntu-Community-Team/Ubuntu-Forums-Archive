---
title: "how to install Guestaddition"
date: 2024-06-22
forum: Virtualisation
---

### Post by satimis on 2024-06-22
Hi all,

VirtualBox V7.0
Host	Ubuntu 22.04
Guests	Ubuntu 22.04/Windows 10/Windows 11/Linuxmint etc.

I haven't run it for quite long time.  All VMs are unable to start.  Finally I have to reinstall VirtualBox on repo (previously it was installed on the package download on Oracle VirtualBox website).

Please advise how to install GuestAddition?  Thanks

Regards

---

### Post by nicolasdentremont on 2024-06-22
In the top menu of your VM, go to Devices > Insert Guest Additions Image

---

### Post by TheFu on 2024-06-22
[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html) answers all questions related to guest additions.

---

### Post by satimis on 2024-06-23
> **nicolasdentremont said:**
> In the top menu of your VM, go to Devices > Insert Guest Additions Image
Hi@nicolasdentremont,

Thanks for your advice.

I have to explain more about this VirtualBox V7.0, running on my PC, which was installed on the VirtualBox package download on Oracle VirtualBox websites more than 5 years ago.  It was not installed on Ubuntu repo.

I only use the VMs of the VirtualBox for retaining copies of my live websites running on Internet, but not for production.  They are not open to public.  Seldomly I ran VirtualBox.

2 days before I found unable to start the VMs.  Then I reinstalled the VirtualBox on Ubuntu repo.  Now the VMs can be started.  I need to reinstall/update GuestAddition.  But there is no GuestAddition on Ubuntu repo.

Can I download the GuestAddition from Oracle VirtualBox website and install it for use?

Please advise.  Thanks.

Regards

---

### Post by nicolasdentremont on 2024-06-23
They have them here also 

[https://download.virtualbox.org/virtualbox](https://download.virtualbox.org/virtualbox)

---

### Post by satimis on 2024-06-23
> **nicolasdentremont said:**
> They have them here also 

[https://download.virtualbox.org/virtualbox](https://download.virtualbox.org/virtualbox)
Hi,

Thanks.

I suppose I need;
7.0.0  10-Oct-2022 16:17
Version
?

Regards

---

### Post by nicolasdentremont on 2024-06-23
> **satimis said:**
> Hi,

Thanks.

I suppose I need;
7.0.0  10-Oct-2022 16:17
Version
?

Regards

I would think so. Whatever version of virtual box that you're using.

---

### Post by satimis on 2024-06-23
Hi all,

I have more than 20 VMs running.  It would be time consuming to install GuestAddition on each VM.

Now I have VBoxGuestAdditions_7.0.0.iso download on the host.

Can I run following command on host to install GuestAddition instead;```

$ sudo apt install VBoxGuestAdditions_7.0.0.iso

```

If YES, please advise on which folder to retain the ISO ?

Thanks

Regards

---

### Post by satimis on 2024-06-23
> **nicolasdentremont said:**
> I would think so. Whatever version of virtual box that you're using.
V7.0

Regards

---

### Post by TheFu on 2024-06-23
> **satimis said:**
> Hi all,

I have more than 20 VMs running.  It would be time consuming to install GuestAddition on each VM.

Now I have VBoxGuestAdditions_7.0.0.iso download on the host.

Can I run following command on host to install GuestAddition instead;```

$ sudo apt install VBoxGuestAdditions_7.0.0.iso

```

If YES, please advise on which folder to retain the ISO ?

Thanks

Regards



    [https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html) answers all questions related to guest additions.

---

### Post by satimis on 2024-06-23
> **TheFu said:**
> [https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html) answers all questions related to guest additions.
Thanks

I have checked it before.  It is a lengthy document.  Unfortunately I couldn't find the search function.

I'm searching for how to install GuestAddition globally, instead of installing it on each VM, one by one.

Regards

---

### Post by satimis on 2024-06-23
Hi all,

My current running VirtualBox version was reinstalled on Ubuntu repo

On Host terminal running;
$ apt policy virtualbox-guest-additions-iso```

virtualbox-guest-additions-iso:
  Installed: (none)
  Candidate: 7.0.16-1
  Version table:
     7.0.16-1 500
        500 http://hk.archive.ubuntu.com/ubuntu noble/multiverse amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu noble/multiverse i386 Packages
N: Ignoring file 'ubuntu.sources_20240621' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```
The GuestAddition is on repo.  Can I install it instead of downloading it on Oracle VirtualBox website?

The more I read and more search made on Internet the more confusing I'm

Regards

---

### Post by ajgreeny on 2024-06-23
> **satimis said:**
> Thanks

I have checked it before.  It is a lengthy document.  Unfortunately I couldn't find the search function.

I'm searching for how to install GuestAddition globally, instead of installing it on each VM, one by one.

Regards
Sorry, but you can't install guest-additions globally to all of your VMs in a single action; the additions are, as seems perfectly normal to me, installed in each guest, not in the host so you have to boot each VM and then install GA one by one.

I gave up on VBox some time ago in favour of KVM/QEMU which you may wish to investigate as it's much better than VBox in my opinion.

---

### Post by TheFu on 2024-06-23
> **satimis said:**
> Thanks

I have checked it before.  It is a lengthy document.  Unfortunately I couldn't find the search function. Uh ... use the browser "search" ... often <cntl>-f?
> **satimis said:**
> 
I'm searching for how to install GuestAddition globally, instead of installing it on each VM, one by one.

Regards

Well, 
a) guest additions aren't mandated. They are optional. They are only necessary if you want the non-GPL, non-free, stuff that Oracle sneaks into the total solution.  

b) Guest Additions are per-kernel extensions, so each guest kernel OS needs to be re-linked, for the specific guest extensions to be installed.  That means it cannot be installed from outside a running guest.  Further, each guest needs to provide the required software tools and dependencies required to support the re-link of kernel modules.  They are probably all different inside each guest, unless you happen to run exactly the same guest OSes inside each guest VM.

c) There are other hypervisors that can be used.  Some of them only use normal GPL licensed software, which means updating them doesn't need to be point-n-click. It can be automated much easier.  Alas, you chose to run Virtualbox.  It isn't a terrible tool, but it does have limitations.

d) When searching for solutions, always start with the documentation for the tool first.  If there isn't any mention of the capability you seek, asking for help is fine, but it is best if you've already tried finding the answer yourself and state what you've tried already.  
In the linked URL, is says in the installation section:
> the Guest Additions are designed to be installed inside a virtual machine after the guest operating system has been installed.
....
The Oracle VM VirtualBox Guest Additions for all supported guest operating systems are provided as a single CD-ROM image file which is called VBoxGuestAdditions.iso. This image file is located in the installation directory of Oracle VM VirtualBox. To install the Guest Additions for a particular VM, you mount this ISO file in your VM as a virtual CD-ROM and install from there. 

That's pretty clear.  Your Vbox host computer already has the correct .iso installed.  Just mount it and run the installer from inside each guest VM.  That is also clear.

---

### Post by satimis on 2024-06-23
> **ajgreeny said:**
> Sorry, but you can't install guest-additions globally to all of your VMs in a single action; the additions are, as seems perfectly normal to me, installed in each guest, not in the host so you have to boot each VM and then install GA one by one.

I gave up on VBox some time ago in favour of KVM/QEMU which you may wish to investigate as it's much better than VBox in my opinion.
Hi@ajgreeny and all,

Thanks for your advice.

Problem solved, easy and simple.  It is NOT necessary to download GuestAddition package on Internet.

Performed following steps:
1) On Host terminal run;```

$ sudo apt install virtualbox-guest-additions-iso

```
(to install GuestAdditions on Ubuntu repo)

Start VirtualBox VM
-> Devices -> Insert Guest Additions CD Image ...

Click VBox_CAs_V7.0.16 Icon
-> VBoxLinuxAdditions.run

Wait until it finishes.

Restart VM  (that is all)

My problem is I have to repeat the same steps on each VM. I have >20 VMs and it'll take me some time to complete.

I don't know WHY it would happen.  VirtualBox has been running on this PC, say PC1, sometimes before without problem.

**[COLOR="#FF0000"]I have another Ubuntu 22.04 PC, say PC2.  It has exactly the same problem.  I don't know WHY? [/COLOR]** I'll fix it when I have time.

I have run KVM/QEMU and Docker for some time in the past, only for testing NOT for production.  Docker is for sharing software and VirtualBox for hardware.

Today hardware is not expensive.  If I need to run an additional OS, I just buy a new SSD adding it to the PC and run the additional OS on bare metal. 

The advantage of virtual machine is able running several OSs on the same PC simultaneously.

Thanks and Regards

---

### Post by TheFu on 2024-06-24
Installing the guest additions into the VBox host computer was a waste of time. It didn't do anything useful.

---

### Post by satimis on 2024-06-25
> **TheFu said:**
> Installing the guest additions into the VBox host computer was a waste of time. It didn't do anything useful.
I have been running VirtaulBox on Ubuntu PC for prolonged time without problem, tracing back to Ubuntu 20.04 and Ubuntu 22.04 -> now 24.04.

I have VirtualBox running on this Ubuntu 22.04 PC, a daily working PC (say PC-1) and my another Ubuntu 22.04 PC (say PC-2) for prolonged time without any problem.  A day before I also found similar problem on VirtualBox of PC-2, unable to start VMs.  It is exactly the same problem as on PC-1.  All VMs are unable to start.

I don't run VirtualBox daily on both PCs.  It is because I have problem running OpenShot Video Editor on Ubuntu 22.04 and Ubuntu 24.04 (already posted on another thread).  I have LinuxMint VM installed on VirtualBox of both PCs.  I want to test OpenShot Video Editor on LinuxMint to check whether it is NOW OpenShot Video Editor having problem running on Linux?  OpenShot Video Editor has been running on my PC-1 and PC-2 for prolonged time in the past without any problem.

OpenShot Video Editor is working seamlessly on MS Windows 10.  I have another drive on PC-1, running MS Windows 10.  There is no problem running OpenShot Video Editor on Window 10.

I suspected whether those problems mentioned above coming from the Linux kernel?

Regards

**[COLOR="#FF0000"]Remark:[/COLOR]**
A side question.  I didn't receive email advice on replies to my posting.  I have to check it frequently on Ubuntu forum website.

---

### Post by satimis on 2024-06-26
Hi all,

I have solved the problem of starting VMs on my PC-2 VirtualBox.

VirtualBox on my PCs, unable to start all VMs, this problem is caused by Ubuntu upgrading the kernel to "6.5.0-41-generic"

Steps performed as follows;
On Host Terminal of PC-2 run```

$ sudo apt install --reinstall virtualbox-dkms && sudo apt install libelf-dev

```

On VM
-> Settings -> USB
select "USB 1.1 (OHCI) Controller" -> OK  (not USB 3.0)

Now all VMs (>30 VMs on this PC, PC-2) can be started without problem.

I have to find time sorting out upgrading "GuestAddition", on REPO of Ubuntu?  Or download on VirtualBox website?

I have been running VirtaulBox for prolonged time without problem, long before VirtualBox acquired by Oracle, only for testing.

I only ran VirtualBox on my PC ONCE for production as server of my websites, >40 WordPress websites, when I subscribed hosting service on "Godaddy" and static IP, about 6 years ago.

It was a wonderful setup.  When my server was down visitors browing my websites on Godaddy server.  When my local server was up, visitors browing my websites on my local server.  The switching was fully automatic and visitors didn't notice this change.

Regards

---

