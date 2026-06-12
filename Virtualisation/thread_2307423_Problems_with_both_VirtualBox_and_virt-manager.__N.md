---
title: "Problems with both VirtualBox and virt-manager.  Need beginner help."
date: 2015-12-24
forum: Virtualisation
---

### Post by CelticWhisper on 2015-12-24
Hi,

I have been using Ubuntu for a long time but haven't used it as a serious virtualization host until now.  I switched my main desktop away from Windows and am trying to get some kind of reliable VM management set up.  Been running into a lot of problems though.  I'm not entirely sure which direction to go, so I apologize that this question isn't going to be terribly pointed.  Still, I will be as specific as I can.



Problems I'm having with virt-manager are primarily that I can't get it working at all.  I try to create a VM, import or create storage, and start it, but I receive various errors depending on what I've tried to get it running.  I have verified that my CPU (Opteron 1385) supports SVM and that the feature is enabled in firmware.  Somewhere along the way, GRUB added an option (as default) for "Ubuntu with Xen Hypervisor" and checking ps in a terminal shows that xend is indeed running.  However, when I try to setup a VM in virt-manager, I run into two errors.  One states "Unable to complete install: 'Cannot recv data: Connection reset by peer'" and the other states "Error polling connection 'xen:///': internal error: received hangup / error event on socket".  I'm assuming I need to better understand some client-server paradigm Xen uses but I'm not there yet and any help in just getting to the point where I can reliably create and run VMs would be a huge help to me.  It's difficult to learn past frustration and I'm hoping others here understand the feeling of just wanting the thing to work for now so you can sort out details later.

VirtualBox will run VMs but I encounter a problem where the entire host system will lock up.  I can't seem to restart lightdm and the only way to reliably get a functional system back is with a hard reset via the front panel button on the tower.  Also, VirtualBox will not start guests at all if I'm booted to the "Ubuntu with Xen Hypervisor" option in GRUB.  I suspect this is because when I do this, the entire OS environment is running as a Xen VM and so VirtualBox would be running nested, but I don't know that for a fact.

Ideally I would like to correct all of these problems so I can use any hypervisor I want, but I'd be happy with one or the other as long as I understand exactly how to run it without show-stopping problems.  Please let me know if you need me to provide screenshots, error text, logs, command output or anything else.

Thank you.

---

### Post by houstonbofh on 2015-12-31
I have the setup you seem to want, but I use KVM and not Xen...  It is much better supported on Ubuntu and just works out of the box.  There is no special grub entry needed, and it can work as a desktop add on, or as a standalone server that is headless.

Is there a reason you need Xen?

---

### Post by MAFoElffen on 2016-01-02
+1 with houstonbofh

I learn by doing. About 5 years ago I installed a Xen Hypervisor on Ubuntu Server... to learn how to do it and get some experience on it. I did not keep it in service. Now I have 2 Ubuntu Servers with KVM, 2 Win Servers with Hyper-V. and 1 Ubuntu Server with V-Shere.

The Hyper-V I just had for my MSCS Certifications, and being a student I had  a few free licenses. The V-Shere was because I had a few things I needed to learn and evaluate that were setup on V-Sphere images. 

The Ubuntu w/ KVM... is what I consolidated all my old/previous 14 Ubuntu servers and 5 test workstations, all into virtual servers and guests on 2 enterprise class servers and 2 management consoles. (I slimmed down my infrastructure.) I really enjoyed my move to KVM. I learned it and stayed with it for myself.

I still have virtualbox and vmplayer installed on a few boxes, but they don't have a job like they did previously. What I did before, I do on KVM now. I connect a few dierent ways. Theyare still good products and get the job done... but I just outgrew them.

---

### Post by MAFoElffen on 2016-01-02
With your error message, you do not seem to have a connection from libvert to xen. This could be from 3 things. The driver/config, certificates or permissions problems.

If on the last part of ./configure you do not see output that says "zen:yes" and rather says "xen:no" ... then it is a driver configuration problem. Most of the time, that is what causes that error message. After investigating that, I found this which has the scoop on diagnosing that and more:
[http://wiki.libvirt.org/page/Failed_to_connect_to_the_hypervisor](http://wiki.libvirt.org/page/Failed_to_connect_to_the_hypervisor)

Lets deal with that problem in this thread. As for VirtualBox, I would suggest that you keep a thread limited to one subject. Maybe if we cure this problem, you may or may not want to deal with the second. But if you do, we should put that in another thread... that way things don't get muddied between the two problems.

---

### Post by heiko_s on 2016-01-02
I think there is some confusion (at least I am).

1. Are you trying to run VirtualBox? I assume yes.

2. Why do you run Xen? You don't need it for VirtualBox and it WILL PREVENT you from running VirtualBox.

You have to make sure that grub boots into a regular kernel and that xend is NOT running.

Here the steps to stop this:

1. Go to /etc/default/grub.d and rename xen.cfg to xen.cfg.bak

2. Go to /etc/default and edit grub as superuser. Comment out the XEN... lines and make sure that Ubuntu boots into a regular kernel.

Here is an example /etc/default/grub file (shortened):

```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=10
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT_STYLE=countdown
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"
GRUB_CMDLINE_LINUX=""
#GRUB_CMDLINE_XEN="iommu=on dom0_mem=7G vga=mode-0x03D4"
#GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT="xen-pciback.hide=(02:00.0)(02:00.1) profile elevator=deadline nouveau.blacklist=1 quiet nomodeset"

```

Run update-grub as root:
```
sudo update-grub
```

Explanation:
When you run Xen (xend means you do) you already run a VM under Xen, namely Ubuntu. You cannot run nested VMs.

I wonder what you need virt-manager for? You certainly don't need it for VirtualBox.

In my opinion virt-manager just complicates tasks.

---

### Post by MAFoElffen on 2016-01-03
::Biting lip:: virt-manager, virt-viewer, virt-clone, and virt-installer have their uses when using hypervisors.

True, you could use other techniques for connecting to your running guests (other than virt-maganer or virt-viewer). But virt-manager is easy for a new user, such as the OP implied, to learn and use virt-manager, until he learns to use others. I use virt-manager as one of many guest tools in KMS ... but I also use VNC & SPICE clients and ssh.

True, the OP did not say what his requirements were, but...

The OP's first post said he had an Xen <> virt-manager problem ... which that error implies a connection issue from virt-manager to the Xen hypervisor. He mentioned, as sort of a sidenote, that he previously had problems with VirtualBox. True, he might not need both. But it sounded as if that was mentioned, as a note, that it might somehow be related. I asked for more info from the OP, but we just need to be patient on that...

EDIT-- One note about those tools, they are the same whether I am on Red-Hat or Ubuntu... or on Windows. They also work with various hypervisors, cloud images and virtualized containers. 

*** You did catch something, that I missed in his first post ... that he is really looking for something (virtualization) that work's
> **CelticWhisper said:**
> ....so I can use any hypervisor I want, but I'd be happy with one or the other as long as I understand exactly how to run it without show-stopping problems.
I think if he hinted to his goals, we could recommend something along those lines. As for what he tried to do, VirtualBox is a Type II hypervisor (runs alongside a host operating system), whereas Xen is a Type I hypervisor (runs on the bare metal). Depending on what he is trying to do, this may affect what he is trying to run as a Virtual Machine. VM's in type I do not necessarily need to know that they are running as a virtual, whereas type II must be able to run as knowing they are running as a virtual. (i.e. virtualized hardware API's, guest additions)... runs on top of the hosting operating system and redirects requests for resources to appropriate APIs in the host environment. Then we have hybrid hypervisors that are in between. I have run a type II in a hybrid hypervisor, just to see if it would work. It did, but was very, very slow. It was buggy.

---

### Post by MAFoElffen on 2016-01-03
So I guess if we backup:

Who's insructions did you follow when you installed Xen?

Could you confirm your installation of Xen using 
```

sudo xl list

```
Once the hypervisor is installed, including your network bridge that you will use to connect to your VM Guests, then you will install a guest VM. After installing a VM, then you start your guest, then connect to the running guest instance in some manner.  That is the summarized explanation of concepts. That is going to be the same, whether using Xen, KVM, ESXi, vSphere, EC2 Cloud images, LXC, Docker, etc...

The alternate would be using something like VirtualBox or VM Player. Install the application. Configure networking. Create / Install the VM within that app, atart/ run and connect within that app. Limted to what you could create/run in VM. You may need some virtual appliances for some things. 

Actually, both paths have pros and cons.

---

