---
title: "virtualbox intel VT-x dis-able in 4.1.8"
date: 2012-02-05
forum: Virtualisation
---

### Post by jao_madn on 2012-02-05
hi,

 Does anyone knows or suffer the hardware Virtualization (INTEL VT-x) dis-able, i already enable it in the bios and still in the VirtualBox is dis-able all my guest operating system, i wonder if this is in the software because since version 3 the VT-X is enabled,

If someone knows about this problem or somewat point me to the right direction.

---

### Post by CharlesA on 2012-02-06
Never heard of that problem.

I'm running a Intel CPU on my VM box and I haven't run into anything that says I cannot enable hardware virtualization.

Are you getting any error messages? What kind of guest is it? 64-bit or 32-bit?

---

### Post by Rafterman414 on 2012-02-06
The only time that I ran into that was after upgrading my BIOS the setting of Intel VT-x changed to the BIOS default of Disabled but after changing it back to Enabled and checking it to Enabled in the VM Guest Settings everything seemed to work just fine after that. I am running VirtualBox 4.1.8.

Here is something that I just read that might help in determining if Virtualization Technology is enabled/supported for your processor:
[http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/](http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/)

---

### Post by jao_madn on 2012-02-06
> **CharlesA said:**
> Never heard of that problem.

I'm running a Intel CPU on my VM box and I haven't run into anything that says I cannot enable hardware virtualization.

Are you getting any error messages? What kind of guest is it? 64-bit or 32-bit?

Actually theres no error msg saying the VT-X is disable, i just notice this problem lately when i did something on my VM guest after i check all of my VM has the same problem, I already check my bios and its enabled. i had linux windows and solaris VM guest and in the bottom icon of the Vt-x is disables the same with the nested page...In the settings acceleration the VT-x is enable and the nested paging.

---

### Post by jao_madn on 2012-02-06
> **Rafterman414 said:**
> The only time that I ran into that was after upgrading my BIOS the setting of Intel VT-x changed to the BIOS default of Disabled but after changing it back to Enabled and checking it to Enabled in the VM Guest Settings everything seemed to work just fine after that. I am running VirtualBox 4.1.8.

Here is something that I just read that might help in determining if Virtualization Technology is enabled/supported for your processor:
[http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/](http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/)

Rafterman414: Hi i have an intel VT-x system i already using it since version 3.**. i just notice this problem when i did something in the VM guess lately..

---

### Post by xyzzyman on 2012-02-06
You might want to check your dmesg log to see if one of the kernel modules for virtualbox is failing. forums.virtualbox.org doesn't seem to have anyone complaining of this issue. My 4.1.8 install is reporting that VX-T is on (My Core 2 Duo doesn't support nested paging though.)

---

### Post by CharlesA on 2012-02-06
> **jao_madn said:**
> Rafterman414: Hi i have an intel VT-x system i already using it since version 3.**. i just notice this problem when i did something in the VM guess lately..
Odd. I just checked my VM host on a random VM and it said this: Hardw. virt.ext: on

```
vboxmanage showvminfo vmname
```

---

### Post by japzone on 2012-02-06
Have you tried Reinstalling VirtualBox? That may resolve the issue. If not keep the info coming.

---

### Post by jao_madn on 2012-02-07
> **xyzzyman said:**
> You might want to check your dmesg log to see if one of the kernel modules for virtualbox is failing. forums.virtualbox.org doesn't seem to have anyone complaining of this issue. My 4.1.8 install is reporting that VX-T is on (My Core 2 Duo doesn't support nested paging though.)

my dmesg only show this one related to virtualbox
```

warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
```

this are the modules loaded on my system

```
user@user-linux:~$ !lsmod
lsmod | grep vbox
vboxpci                14531  0 
vboxnetadp              6808  0 
vboxnetflt             16652  0 
vboxdrv               250437  3 vboxpci,vboxnetadp,vboxnetflt

```

---

### Post by jao_madn on 2012-02-07
> **CharlesA said:**
> Odd. I just checked my VM host on a random VM and it said this: Hardw. virt.ext: on

```
vboxmanage showvminfo vmname
```

Hi i also check my random VM and found this one info i think is useful

```
Hardw. virt.ext: on
Hardw. virt.ext exclusive: on
Nested Paging:   on
Large Pages:     off
VT-x VPID:       on

```

But why is it in the vbox gui the intel VT-x is grayed or dis-able if i point my mouse to it..

---

### Post by jao_madn on 2012-02-07
In addtiion i check in the session information in the random guess vm. that in 
Details the VT-x/AMD-v and nested paging is enable but in runtime is dis-able..

---

### Post by CharlesA on 2012-02-07
Was that random VM powered on?

The one I checked was running.

---

### Post by jao_madn on 2012-02-07
> **CharlesA said:**
> Was that random VM powered on?

The one I checked was running.

Yup the VM i check i power on..All of my VM guest had the same problem..

---

### Post by CharlesA on 2012-02-07
I don't think you can modify that setting with the machine running. Does it let you check it if the machine is powered off?

---

### Post by jao_madn on 2012-02-07
> **CharlesA said:**
> I don't think you can modify that setting with the machine running. Does it let you check it if the machine is powered off?

@ CharlesA: please clarify?

When machine is poweroff and check SETTINGS>SYSTEM>ACCELERATION the hardware virtualization is check/enable also the nested paging.

When the VM is running go to top menu in MACHINE>SESSION INFORMATION
there are two tab display for information details ralated to the VM and in runtime. In the details it display that the VT-x/AMD-V and nested paging is enable while if we check in the runtime tab menu it display that the two is disable.

Thanks for the responce..

---

### Post by CharlesA on 2012-02-07
Does it look similar to this?

In order to change those options, you need to have the VM powered off. They are locked from changes with the VM running.

---

### Post by jao_madn on 2012-02-09
> **CharlesA said:**
> Does it look similar to this?

In order to change those options, you need to have the VM powered off. They are locked from changes with the VM running.

@CharlesA: thanks for the responce, as i mention in my early post, when i check all of my VM all of there  SETTINGS>SYSTEM>ACCELERATION the VT-x/AMD-v and nested paging is enable or check  out but during running the VT-X/AMV-v is disabled or grayed out.

---

### Post by CharlesA on 2012-02-09
That is because you cannot change those settings when the VM is running.

---

### Post by jao_madn on 2012-02-09
> **CharlesA said:**
> That is because you cannot change those settings when the VM is running.

Thanks for the responce..Yup your very right, but i dont have any plan to change it when my VM is running..I believe you mis understand me..My problem is all of my VM is set to hardware virtualization or VT-x and nested paging is enable and my hardware support it. But when i check any of the VM when running the VT-x is disable or grayed out.

---

### Post by CharlesA on 2012-02-09
Can you post a screenshot of what it looks like, please.

---

### Post by jao_madn on 2012-02-09
> **CharlesA said:**
> Can you post a screenshot of what it looks like, please.

Thanks for responce again attach is screenshots.

---

### Post by CharlesA on 2012-02-09
Interesting.

Try purging and reinstalling Virtualbox.

```
sudo apt-get purge virtualbox-4.1 && sudo apt-get install virtualbox-4.1
```

If it's still not working, you might want to try posting over on the virtualbox forums: [https://forums.virtualbox.org/](https://forums.virtualbox.org/)

EDIT: Make sure all running VMs are powered off before removing virtualbox. :)

---

### Post by jao_madn on 2012-02-10
> **CharlesA said:**
> Interesting.

Try purging and reinstalling Virtualbox.

```
sudo apt-get purge virtualbox-4.1 && sudo apt-get install virtualbox-4.1
```If it's still not working, you might want to try posting over on the virtualbox forums: [https://forums.virtualbox.org/](https://forums.virtualbox.org/)

EDIT: Make sure all running VMs are powered off before removing virtualbox. :)

I had some additional question. Does uninstalling specially using PURGE will remove my VM settings, or individual VM settings, how about the VM HD?

---

### Post by CharlesA on 2012-02-10
Uninstalling virtualbox keeps all the VMs you have created. :)

---

### Post by jao_madn on 2012-02-19
> **CharlesA said:**
> Uninstalling virtualbox keeps all the VMs you have created. :)

 Update: 
@ CharlesA: Uninstalling oracle virtualbox using purge parameters doesn't help. Maybe this is related to system configuration when i installed something or upgrade some packages. My last suspicion is the laptop bios but since im planning to migrate to 64bit. I already installed the 64bit when i try the oracle virtualbox 64bit the Hardware IntelVT-x is working fine so therefore the bios is ok..

Im planning to migrate to 64 bit to used my extra memory and planning to upgrade to 8Gb therefore i may not touch this problem anymore..

Thanks everyone for the input..

---

### Post by jao_madn on 2012-03-21
Hi Everybody,

I had some good news, I finally solve this problem:

As i mention in my last post i migrate to 64bit and my virtualbox Intel VT-X(hardware virtualization) working fine, lately i encounter again the problem and decide to hunt down the root cause.

The root cause was the qemu virtualization package which is the FF and its dependencies:
"bridge-utils libaio1 qemu-common qemu-kvm seabios vgabios" I got this package when i installed the MULTISYSTEM package for usb multipass.. I installed also this on my 32 bit system..

After confirm and further checking, the main cause is the services name /etc/init.d/qemu-kvm which is a upstart-job that runs in startup. By stoping this servies i had access to VIRTUALBOX HARDWARE VIRTUALIZATION VT-x but if you let this service  you dont have access to virtualbox hardware virtualization. 

I guess only one can access hardware virtualization.

---

### Post by CharlesA on 2012-03-21
Virtualbox and KVM conflict with each other.

You can however run virtualbox on a KVM guest.

---

