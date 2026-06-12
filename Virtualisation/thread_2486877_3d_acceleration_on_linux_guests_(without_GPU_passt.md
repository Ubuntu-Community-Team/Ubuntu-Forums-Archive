---
title: "3d acceleration on linux guests (without GPU passthrough)"
date: 2023-05-15
forum: Virtualisation
---

### Post by demonenero84 on 2023-05-15
Greetings ):P
Is there anyone that has managed to create linux vms with 3d acceleration without resorting to GPU passthrough ?, specifically with KVM/QEMU, I am not familiar with virtualbox, vmplayer, and other virtualization software.
I took a look and found two projects:

[https://docs.mesa3d.org/drivers/virgl.html](https://docs.mesa3d.org/drivers/virgl.html)

[https://arccompute.com/blog/libvfio-commodity-gpu-multiplexing/](https://arccompute.com/blog/libvfio-commodity-gpu-multiplexing/)

This is my hardware and os
OS: Kubuntu 22.04.2 LTS x86_64
CPU: Intel i5-7400 (4) @ 3.500GHz
GPU: NVIDIA GeForce GTX 1050 
Right now I am using a GTX1050 with proprietary drivers but I plan to buy an AMD GPU so I can use open source drivers

Thanks a lot in advance

---

### Post by MAFoElffen on 2023-05-15
Yes. Sort of...

Run locally from the host, I can get VirGL to work:
With Video Set to 'virtio' with video acceleration 3D graphics selected. Graphics set to Spice with none selected as the listener. Then with OpenGL Selected, and set to the GPU PCI setting to the GPU...

But if I try to run remotely, then I get an error saying:
> 
Error connecting to graphical console:
Guest is on a remote host, but is only configured to allow local file descriptor connections.

I've tried to do several things to get around that. Not gotten there yet for remote viewing.

Then since I have nVidia and Intel graphics and Comet Lake CPU (gen 10)... For the i915, I do GVT-G... But is complex, and not for the casual user. Involves using QEMU VM hooks, loading extra modules loaded at the VM pre-load. adding virtual GPU devices after load, then removing them on VM shutdown (all using QEMu hooks). This only works with Intel GPU, and only on certain generations of those... So is not straight forward to get working, but is possible.

I used these two guides:
[https://wiki.archlinux.org/title/Intel_GVT-g](https://wiki.archlinux.org/title/Intel_GVT-g)
[https://blog.tmm.cx/2020/05/15/passing-an-intel-gpu-to-a-linux-kvm-virtual-machine/](https://blog.tmm.cx/2020/05/15/passing-an-intel-gpu-to-a-linux-kvm-virtual-machine/)

* NOTE that now, with current Linux kernel, the name of the mdev module is 'mdev'. 'vfio-mdev' was deprecated at Linux kernel 5.15.

Things are getting better, and easier. though is still some work involved.

---

### Post by demonenero84 on 2023-05-15
> **MAFoElffen said:**
> Yes. Sort of...
Run locally from the host, I can get VirGL to work:
With Video Set to 'virtio' with video acceleration 3D graphics selected. Graphics set to Spice with none selected as the listener. Then with OpenGL Selected, and set to the GPU PCI setting to the GPU...

Interesting, I am going to try these settings, let's see if it works for me (I use proprietary nvidia drivers).  Since I run my vms locally I should not have that "Error connecting to graphical console"
> **MAFoElffen said:**
> Then since I have nVidia and Intel graphics and Comet Lake CPU (gen  10)... For the i915, I do GVT-G... But is complex, and not for the  casual user.
I see, unfortunately my knowledge of KVM/QEMU is rather limited so I take the easy option (VirGL) 
thanks a lot for the reply, I will do my test and post the results

---

### Post by demonenero84 on 2023-05-16
Ok after a quick test (I set video to Virtio with 3d acceleration and display spice set to spice server, listen type set to none, opengl enabled and set to my GTX1050) I get this error
```
Unable to complete install: 'internal error: process exited while connecting to monitor: 2023-05-16T14:38:11.500089Z qemu-system-x86_64: egl: eglInitialize failed
2023-05-16T14:38:11.500182Z qemu-system-x86_64: Failed to initialize EGL render node for SPICE GL'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 72, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/createvm.py", line 2008, in _do_async_install
```
Now I use proprietary drivers, I will test the same settings while using nouveau drivers to see if it works.
Any suggestions?
thanks a lot in advance

EDIT:
As usual (I had a similar problem with LXD containers) nouveau drivers solve the issue :P. With open source drivers it works, SuperTuxKart set at lowest graphic detail, resolution 1920x1080 runs at 38 fps
> **MAFoElffen said:**
> But if I try to run remotely, then I get an error saying:

I've tried to do several things to get around that. Not gotten there yet for remote viewing
So no way to get x forwarding to work :( or did I misunderstand "remote viewing" ?
I will mark this thread as solved, if anyone wishes to add any suggestions I will be glad to accept them

---

### Post by MAFoElffen on 2023-05-16
I have nVidia on two of my KVM Hosts, and both of them have their respective nVidia drivers installed. Yes, nouuveau driver works better. It also seems to work better, if the host's CPU is Intel, instead of AMD (fr some reason). 

Also, you might try this: [https://www.reddit.com/r/VFIO/comments/pmqvwf/some_tips_on_using_virtiogpu_and_nvidia_drivers/](https://www.reddit.com/r/VFIO/comments/pmqvwf/some_tips_on_using_virtiogpu_and_nvidia_drivers/)

---

### Post by demonenero84 on 2023-05-17
thanks

---

### Post by TheFu on 2023-05-17
> **demonenero84 said:**
> So no way to get x forwarding to work :( or did I misunderstand "remote viewing" ?
I will mark this thread as solved, if anyone wishes to add any suggestions I will be glad to accept them

I'm just lurking ... remote X11 isn't what this virtgl solution is about.  It is about using **virt-viewer** as a client from a remote computer and still having excellent, near local, performance.

**ssh -X** will work regardless of KVM.  It has nothing to do with 3D acceleration.  Obviously, a local X/Server is required for the remote X/Client to connect.  I have no idea how or if Wayland works or doesn't.  I suspect it does work for most normal uses via xwayland, but don't know.

---

### Post by MAFoElffen on 2023-05-18
> **TheFu said:**
> It is about using **virt-viewer** as a client from a remote computer and still having excellent, near local, performance.

On that note (above)... I am satisfied with using Display=Spice and Video=QXL. That works very well with most anything you throw at it. Good performance and quality. Is a lot of work to do vGPU's and Pass-Throughs. Most of my VM's are for testing and don't have a long shelf-life. I have a few long-term guests that i keep around, and tweak them to how i want them.

Before this newer server, with Intel... I had my workstation with AMD CPU and nVidia Graphics. Sometimes,  I was very frustrated with the support (for virtual hosts) for both. I could do things, but it was a struggle. I looked into [nVidia vGPU]("https://www.nvidia.com/en-us/data-center/resources/vgpu-evaluation/")... and after seeing the cost for licensing and their licensing structure... that is just crazy.

I am happy with what I can do for free.

---

### Post by TheFu on 2023-05-18
> **MAFoElffen said:**
> On that note (above)... I am satisfied with using Display=Spice and Video=QXL. That works very well with most anything you throw at it. Good performance and quality. 

I use remote X daily, constantly.  Actually, this browser window is running on another system over an **ssh -X** tunnel.

Every once in a while, while at home, I'll want a full desktop experience into a VM.  Then I'll use spice+qxl. Works well, but a full desktop gets in the way of efficient workflow for me.

When I'm traveling and need to access systems over the internet, if text ssh isn't sufficient, I'll use x2go, which uses NX which tunnels an efficient remote desktop over ssh.  NX is a highly efficient, compressed, optimized, remote desktop, but uses ssh for the tunnel and authentication.  It is 2-3x faster than free options and much more secure, thanks to ssh, than VNC.  A key aspect of x2go is that no sensitive data needs to leave the remote system at all, so if your local device gets lost, stolen, or copied by anyone (say border customs at any country), then there isn't any sensitive data on the device.  Something to consider if you travel internationally.  It is surprising which countries have laws to mandate decryption, completely removing any efforts we have to protect corporate/private data.

None of these are great for running games remotely, but they all work for handling email, doing spreadsheets, and coding.

---

### Post by demonenero84 on 2023-05-18
> **TheFu said:**
> I'm just lurking ... remote X11 isn't what this virtgl solution is about.  It is about using **virt-viewer** as a client from a remote computer and still having excellent, near local, performance.

**ssh -X** will work regardless of KVM.  It has nothing to  do with 3D acceleration.  Obviously, a local X/Server is required for  the remote X/Client to connect.  I have no idea how or if Wayland works  or doesn't.  I suspect it does work for most normal uses via xwayland,  but don't know.
I see, thanks for the explanation 
> **TheFu said:**
> I use remote X daily, constantly.  Actually, this browser window is running on another system over an **ssh -X** tunnel.
Interesting, this question is off topic :roll: but how do you "forward" pulse audio? I tried a few things but none of them work:(
thanks a lot

---

### Post by TheFu on 2023-05-18
> **demonenero84 said:**
>  Interesting, this question is off topic :roll: but how do you "forward" pulse audio? I tried a few things but none of them work:(

I don't want audio/video from my browsers, so it has never been an issue to me.  I suppose pulse can be configured in a client/server mode to send the audio between systems.

BTW, my desktop VMs don't usually have any audio devices connected.  Just isn't the way I work.

---

### Post by demonenero84 on 2023-05-18
Ok thanks

---

