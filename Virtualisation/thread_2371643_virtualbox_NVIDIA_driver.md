---
title: "virtualbox NVIDIA driver"
date: 2017-09-16
forum: Virtualisation
---

### Post by o20021106 on 2017-09-16
I am trying to install NVIDIA driver on a guest ubuntu on windows host( to install gpu supported tensorflow). Is it possible to do this?

I am using NVIDIA GEFORECE 849M

I downloaded the driver from NVIDIA and installed it with 

sudo service lightdm stop
sudo init 3
sudo sh NVIDIA-Linux-x86_64-364.69.run

then I get and warning like the following

```
WARNING: You do not appear to have an NVIDIA GPU supported by the 384.69 NVIDIA Linux graphics driver installed in this system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at www.nvidia.com.
-> License accepted.
-> Installing NVIDIA driver version 384.69.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Are you sure you want to continue? (Answer: Abort installation)
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

---

### Post by wildmanne39 on 2017-09-16
If you are running Ubuntu in a guest you will not install the nividia driver it is not needed, virtual environments use there own drivers.

---

### Post by wildmanne39 on 2017-09-16
*Thread moved to **Virtualisation for better support**.*

---

### Post by o20021106 on 2017-09-16
But I purge and uninstalled all nvidia related files now. What should I do?

---

### Post by wildmanne39 on 2017-09-16
If you are running ubuntu in virtualbox you do not need to ever install the nvidia driver, virtualbox uses its own driver, you do not need to do anything virtualbox driver works great. I have used virtualbox for 8 years or more, never had to install the nvidia driver for my nvidia card.

If you are running ubuntu as a host then you do need to install nvidia driver but that is not what you say you are doing.

Edit:

[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

---

### Post by deadflowr on 2017-09-17
> I am trying to install NVIDIA driver on a guest ubuntu on windows host( to install gpu supported tensorflow). Is it possible to do this?

No, not possible.
You can only run the cpu supported version in a vm.
If you want to set up and use the gpu supported version you'll need to do a real hardware install of Ubuntu.

Virtualbox creates fake hardware attributes for the running system.
Among these hardware specs are fake or generic graphics cards.
(By design virtualization makes system highly portable, as in you can setup a vm in one machine and reload it in another completely different machine with little to no performance loss. As long as you can allocate the same set of resources, memory, cpu cores, etc)


A possible method of running real hardware is through a virtual machine setup that can do gpu passthrough such as kvm.
But kvm is not available on Windows, since it's a linux kernel module (kvm as in kernel-based virtual machine)
So moot here, really.
It's also a really complex thing to setup usually requiring a patch or two along with specific hardware specs.
(it also goes without saying that this method is not (as) portable, since it requires a specific hardware layout to run.)

---

### Post by lammert-nijhof on 2017-09-19
What you could do to get the best performance is, to give the Guest 128MB of video memory in the display section and to enable 3D acceleration. For a Windows Guest you can specify 256MB of video memory and enable 2D and 3D acceleration. The installation of the Guest additions in Windows should be (re)done in safe mode for 3D support. In the Host and Guest Internet Browsers you should check, whether they use 'hardware acceleration when available'. The combination of the two allows to run e.g. YouTube HD video in the Guest at slightly higher loads than in the Host. For  a random selected 720p video displayed by Firefox the difference for CPU (4-core Phenom II B97) and GPU (1GB GeForce 8400GS, edition 3) is: 
2010 Host CPU load during: Host Video 50%, Guest Video 65%
2010 Host GPU load during: Host Video 25%, Guest Video 33%

The Firefox browser has an hidden, disabled option to invoke Host Xorg? APIs directly, but that has strange side effects in many distros, but the CPU load goes down to 50% for the Guest too. So there are some improvements possible in the future. I have no clue what the effect of the introduction of Wayland would be. For the moment Ubuntu 17.10 gets into a Login loop, when 3D is enabled for the Guest.

---

### Post by deadflowr on 2017-09-19
> **lammert-nijhof said:**
> What you could do to get the best performance is, to give the Guest 128MB of video memory in the display section and to enable 3D acceleration. For a Windows Guest you can specify 256MB of video memory and enable 2D and 3D acceleration. The installation of the Guest additions in Windows should be (re)done in safe mode for 3D support. In the Host and Guest Internet Browsers you should check, whether they use 'hardware acceleration when available'. The combination of the two allows to run e.g. YouTube HD video in the Guest at slightly higher loads than in the Host. For  a random selected 720p video displayed by Firefox the difference for CPU (4-core Phenom II B97) and GPU (1GB GeForce 8400GS, edition 3) is: 
2010 Host CPU load during: Host Video 50%, Guest Video 65%
2010 Host GPU load during: Host Video 25%, Guest Video 33%

The Firefox browser has an hidden, disabled option to invoke Host Xorg? APIs directly, but that has strange side effects in many distros, but the CPU load goes down to 50% for the Guest too. So there are some improvements possible in the future. I have no clue what the effect of the introduction of Wayland would be. For the moment Ubuntu 17.10 gets into a Login loop, when 3D is enabled for the Guest.

All well and done, but that still won't allow the OP to use the nvidia drivers in the vm, which is what they need to run tensorflow through the gpu.
[https://www.tensorflow.org/install/install_linux]("https://www.tensorflow.org/install/install_linux")

---

### Post by lammert-nijhof on 2017-09-19
I don't expect that many persons have experience with setting up Tensorflow in an Ubuntu Guest in Virtualbox. In my quick search, I could not find any story about a successful GPU pass-through to an Ubuntu Guest using Virtualbox. There are GPU pass-throughs for gaming to Windows Guests and there are stories about using KVM. You are on the bleeding edge of virtualization, so google a lot, have a lot of patience and good luck, because you will need it. Maybe you should consider to dual boot and use the real HW to run Tensorflow. I hope somebody else here can help you with your problem. Sorry.

---

