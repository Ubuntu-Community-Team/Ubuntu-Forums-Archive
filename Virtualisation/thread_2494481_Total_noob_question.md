---
title: "Total noob question"
date: 2024-01-18
forum: Virtualisation
---

### Post by rluka on 2024-01-18
I am totally new to linux!!
I have installed the latest version of ubunto using [COLOR=#000000]VirtualBox on an external USB3 drive and everything works as expected.
I can't for the life of me install ComfyUI from Terminal by following the directions on the ComfyUI website.
I have a Nvidia graphics card and none of the directions on the ComfyUI website work.
When I open terminal and run from there, nothing works.
I always get an error message saying that ";" is expected after something.
Not sure where to put that ";" 
I tried running from Root and nothing works.
I created a CumfyUI folder and opened terminal from there and nothing worked.
I have a lot of learning to do and hope I can get a bit of direction here.
Your help would be greatly appreciated
Ron L


[/COLOR][COLOR=#b22222]***ADDITIONAL INFO***[/COLOR][COLOR=#000000]***:*** I used Oracle VM VirtualBox to install ubunto-22.04.3-desktop-amd64.iso. **Is this copy of ubuntu only for AMD machines? **I am using an i7/12 core computer running Win 11 Pro.
It looks like I should be learning how to do this:
[/COLOR][h=2]Manual Install (Windows, Linux)[/h][h=2]Git clone this repo.
Put your SD checkpoints (the huge ckpt/safetensors files) in: models/checkpoints
Put your VAE in: models/vae
Note: pytorch stable does not support python 3.12 yet. If you have python 3.12 you will have to use the nightly version of pytorch. If you run into issues you should try python 3.11 instead.

[I][U]
[COLOR=#b22222]Sorry for putting you all through this. I have to learn how to Git clone a repo

I have a lot to learn and thank you all for even responding
Ron L[/COLOR][/U][/I]
[/h]

---

### Post by grahammechanical on 2024-01-18
Could you please provide a link to the ComfyUI web site. We would like to see the instructions you are following. I have found this:

[https://github.com/comfyanonymous/ComfyUI#installing](https://github.com/comfyanonymous/ComfyUI#installing)

I do not see any instructions for installing on Ubuntu. The only instructions for Linux are for those with an AMD GPU.

Then there is the matter of PIP. It is not a standard Linux command.

[https://pip.pypa.io/en/stable/installation/](https://pip.pypa.io/en/stable/installation/)

> [COLOR=#000000]I always get an error message saying that ";" is expected after something.[/COLOR]

Those of us more familiar with Python might be able to help if you showed us the full error message.

Regards

---

### Post by MAFoElffen on 2024-01-18
<<This should probably be moved to the Virtualization Section>>

From what you described and hinted at... There is a more fundamental question and matter to ask previous to all that...

What is the Host OS of that you are running VirtualBox on?

RE: [https://www.udemy.com/course/advanced-stable-diffusion-with-comfyui-and-sdxl/](https://www.udemy.com/course/advanced-stable-diffusion-with-comfyui-and-sdxl/)
> 
REQUIREMENTS:
...
A PC with an Nvidia RTX Graphics card with at least 8GB of VRAM. (Students without an Nvidia GPU can run ComfyUI but will struggle with some course material.)

Though [https://github.com/comfyanonymous/ComfyUI#installing](https://github.com/comfyanonymous/ComfyUI#installing) says NVidia, AMD, or Intel ARC GPU's...

*** You realize that a VM guest, if running software that needs direct access to the hardware of an NVidia or AMD GPU video card, would need the host to pass-through that GPU's resources to the VM right? Meaning, it would not be able to use it (Being a second GPU, with the host using another GPU)...

VirtualBox, as a software-based  Virtual Host system, cannot do that. I can tell you that any host running as a guest inside VirtualBox is nto going to see your NVidia GPU. It does and cannot do not do hardware pass-throughs.

If the Host is Linux Based, you are looking at KVM or VMware Workstation. If Windows based, then Hyper-V or VMware Workstation. With either, that is going to evolve some advanced techniques and the motherboards BIOS needs to support IOMMU & vfio passthroughs.

---

### Post by ajgreeny on 2024-01-18
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

Is your nvidia card being used in VBox? If you have not specifically enabled it in the VBox settings your guest will be using the virtual graphics system. I have never had a separate graphics card, always using Intel integrated, so I can not tell you more about using a proprietary nvidia card.

---

### Post by rluka on 2024-01-18
[COLOR=#b22222]***ADDITIONAL INFO***[/COLOR][COLOR=#000000][COLOR=#000000]***:*** I used Oracle VM VirtualBox to install ubunto-22.04.3-desktop-amd64.iso. **Is this copy of ubuntu only for AMD machines? **I am using an i7/12 core computer running Win 11 Pro.
It looks like I should be learning how to do this:
[/COLOR][/COLOR][B]Manual Install (Windows, Linux)

[B]Git clone this repo.
Put your SD checkpoints (the huge ckpt/safetensors files) in: models/checkpoints
Put your VAE in: models/vae
Note: pytorch stable does not support python 3.12 yet. If you have python 3.12 you will have to use the nightly version of pytorch. If you run into issues you should try python 3.11 instead.

[I][U]
[COLOR=#b22222]Sorry for putting you all through this. I have to learn how to Git clone a repo

I have a lot to learn and thank you all for even responding
Ron L[/COLOR][/U][/I]
[/B][/B]

---

### Post by MAFoElffen on 2024-01-18
The software itself works directly with the hardware GPU Graphics chips for NVidia, AMD and Intel ARC. The best that VirtualBox can do is 3D Video Acceleration through software virtualization. That is not going to work for that software application.

If running in a VM Guest, you would have to do a hardware pass-through from the host to the VM Guest (first). That software needs to see one of those types of GPUs "directly".

Since your host is Windows, I could explain the details, but this might help: [https://superuser.com/a/1767617](https://superuser.com/a/1767617)

Please read that first and ask if you have any questions on what that says.

To be able to do that with Windows, you are going to need Windows 10 or 11, Professional Edition, to be able to enable Hyper-V... Then be comfortable with PowerShell.

I rechecked my Doc's and it will not work on Windows with VMware Workstation... It would take vSphere. And you would need to dedicate a machine for that, and that is a non-free solution.

---

### Post by grahammechanical on 2024-01-19
> [COLOR=#000000] to install ubunto-22.04.3-desktop-amd64.iso. **Is this copy of ubuntu only for AMD machines? **[/COLOR]

Not at all. The full answer to this question would require a history lesson on the development of the Personal Computer (PC) and the computer processors that have been created to make the PC what it is today.

Briefly, Intel produced the first 32 bit CPU's (Intel 80386) and so the version of Linux that run on those 32 bit CPU's was called i386. But AMD produced the first 64 bit CPU so the version of Linux that runs on 64 bit CPU's is called AMD64. 

AMD CPU's (both 32 bit and 64 bit) are instruction set compatible with Intel's 32 bit and 64 bit CPU's. 

I am running Linux AMD64 on an Intel CPU. My previous machine also had an Intel CPU and I ran Linux AMD64 on it.

By the way, The instruction set of 64 bit CPU's is backwards compatible with the instruction sets of 32 bit CPU's. Otherwise, applications designed to run on a 32 bit operating system would not work on a 64 bit operating system.

Regards

---

### Post by TheFu on 2024-01-19
> **grahammechanical said:**
>  Briefly, Intel produced the first 32 bit CPU's (Intel 80386) and so the version of Linux that run on those 32 bit CPU's was called i386. But AMD produced the first 64 bit CPU so the version of Linux that runs on 64 bit CPU's is called AMD64. 
 

.... for x86 compatible systems.  

If we ignore x86, then the 64-bit CPU history is much longer.

Cray made the first 64-bit CPU in the mid-1970s.   

DEC made their first 64-bit CPU, the DEC-Alpha running DEC OSF/1 UNIX in the early 1990s.  I had a job porting software to this platform for a few years.

A few years later, Intel made the  Itanium CPU line. That architecture really didn't get used until HP switched from PA-RISC to Itanium around 2008. I understand Itanium manufacturing was shut down in 2021.  The Linux kernel v6.7 removed Itanium support.  

Sun, HP, IBM and others all made 64-bit CPUs before AMD as well.  UltraSPARC, PA-RISC (PA-8000), SGI, and IBM-Power CPUs where all 64-bit in the mid-1990s. 

AMD released their first 64-bit x86 CPU in 2003. It was a big deal.

---

