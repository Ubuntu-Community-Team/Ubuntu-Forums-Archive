---
title: "Ubuntu 4.10 Virtualbox installation X server error"
date: 2021-11-21
forum: Virtualisation
---

### Post by ontpro623 on 2021-11-21
I'm trying to install Ubuntu 4.10 (yes, you heard that right, the first Ubuntu version) amd64 ISO on Virtualbox. The disk is set to IDE and installation progresses fine until the part on reboot where it tells me to select video resolutions for the X-server. I continue with the default resolutions selected without selecting anything new. But then just after that, it gives me to a terminal flickering, and seconds after that, it shows a blue screen with glitched text saying "Failed to start the X-server". I don't know what to do as my graphic setting for the Virtualbox Virtual machine is VMSVGA with 128mb Video RAM. Can anyone help with this error?

---

### Post by ActionParsnip on 2021-11-21
Old versions of Ubuntu are not supported. Please use a supported release

---

### Post by ontpro623 on 2021-11-21
I know. But I have to do this thing where I upgrade every single release of Ubuntu (from 4.10 to 21.10) in a VM for a project. I am looking for replies other than "It's too old"

---

### Post by grahammechanical on 2021-11-21
My first install of Ubuntu 07.04 and so I do not know 04.10. Do you get the option to install non-free software? If you do get that option and tick it then the installer will fail to load a proprietary video driver because video drivers for your hardware were not included in 04.10. Yes I know that this should not matter in a VM. But I think that there usually something called a bridge that connects the OS with the actual hardware.

Was 04.10 capable of give output in SVGA mode or was it limited to VGA?

Regards

---

### Post by QIII on 2021-11-21
What sort of project would include such an asinine exercise?  Homework?

I will tell you with near certainty that starting from there and trying to upgrade to 18.04 through old-releases will be virtually impossible and if you could manage it from a purely mechanical standpoint, you would end up with an OS so fractured and broken it would not operate.  if you were starting with 32-bit 4.10, you would certainly not get past the 32 to 64 bit barrier beyond 18.04 (I believe that was the last 32-bit ISO offered), since you would at some point have to re-install fresh given that there is no 32 to 64 bit upgrade path.  Ubuntu has not offered a 32-bit option for several releases now.  Even so, starting with a 64-bit version as you are, the exercise is a pointless one.

However, the general process for upgrading through old-releases can be found [here]("https://help.ubuntu.com/community/EOLUpgrades").

Please be considerate and remember that the community has much better things to do than spin their wheels on such a pointless exercise.

Moved to Virtualization.

---

### Post by MAFoElffen on 2021-11-22
I have dealt with XServer since 1988 with UNIX, then on Desktops since 2005 on Solaris. 

I am spinning up an installation of it in KVM to see... Why? Because I cannot remember back to 2004 (17 years ago) what the specific options were... LOL

In  the install, select "vesa"... That is what I did, and selected 1024x768 as the resolution. I had VGA selected in my guest hardware config.

Why? Because most all video cards back them supported VESA modes, and they still do today. (Your plan is to upgrade through the versions, so...) That was universal. And VM Host Systems and their guest's virtual video still support VESA Modes... That way you don't get stray direct hardware calls... Vesa Modes also supported higher resolutions than most standard monitors.

See the screenshots?

---

### Post by ontpro623 on 2021-11-24
in the resolution question do you select only that specific resolutions or the other default ones they give?

---

### Post by ontpro623 on 2021-11-24
I chose VBoxVGA and followed steps but the same x server thing happened same with VMSVGA it just blinks, changes resolution for 1 second, goes back to command prompt, and repeats x server error.

---

### Post by lammert-nijhof on 2021-11-25
I use Ubuntu 4.10 since a few years in Virtualbox. Currently I have 6.1.28. I use a screen resolution of 1280x800 and the VBox settings are: vmsvga; 3D acceleration is switched off and I specified 16MB of video RAM. Smaller values do not work anymore with the newer Virtualbox 6.1 releases. 

I can't find any virtualbox guest addition modules (dpkg -l), so I assume I run it without the virtualbox guest additions. I don't remember, how I installed it. 

The only minor issue I have is related to the mouse, I have to switch off the mouse integration for the default USB tablet of Virtualbox or I have to select the PS/2 mouse in the system tab. Afterwards I need to get both mouse position (Host and VM) somehow aligned and it work fine. 

I also installed 5.04 a few month ago (my first Ubuntu in 2005 on a Pentium II) and there I use vboxvga; 3D acceleration is switched off and I specified 16MB of video RAM. The screen resolution is 1024x768 and I did not install the virtualbox guest additions.

For both systems I only selected 1 core; 256MB of main memory and I used the default CPU virtualization acceleration.

I detected that you will have problems with starting the xserver, if you change the settings in Virtualbox from vmsvga (the current default setting in Virtualbox) to vboxvga. It seems you have to stick to the settings you had during the installation of Ubuntu 4.10!

If nothing helps, reinstall Ubuntu 4.10, but first set the Virtualbox values you want, to avoid any issues with the drivers.

---

### Post by MAFoElffen on 2021-11-25
> **ontpro623 said:**
> In the resolution question do you select only that specific resolutions or the other default ones they give?

I chose VBoxVGA and followed steps but the same x server thing  happened same with VMSVGA it just blinks, changes resolution for 1  second, goes back to command prompt, and repeats x server error

                                       
In the resolution question, I just chose what was available as hardware "back then"... Which 1024x768 was great and high resolution 17 years ago... You said you were going to update it through the versions/revisions... Where that hardware and it's capabilities can evolve. 

I've done things where I have Dos 6.4, Windows 2.0, OS2 2.0 and AIX installed in VM's. You need to figure out the hardware that "it ran on" when selecting your virtualized hardware for your VM Guest. This may be a challenge for VBox, as that is a software virtualization hypervisor, whihc limts just what you can virtualize as hardware choices.

I don't have VirtualBox Installed on anything here. I haven't ran VirtualBox in about 7 years, though I had to help Computer Science students to be able to install it on their own machines. In fact, of all the VM Host systems that I used to have to supports, the main one's that I have installed on metal now are KVM, Hyper-V and vSphere. Of those 3, Hyper-V is limited on what you can create as "a sandbox" to play in compared to the other two.

You can do a lot of things with a type 1 hypervisor, that you can't with a type 2 hypervisor... Some say that using those terms is hype and marketing terms... Those that  know me know It am not a marketer nor someone to use buzzwords. Having been an Educator to Computer Science students, I am meaning whether the VM Host uses hardware virtualization or that is software virtualized. You can draw lines between that. It may get some arguments going and name calling about OS whatever, but if you look at the code and functionality, But I have demonstrated that I have no BIAS. I look at the facts. Hyper-V is a hybrid hypervisor (It is somewhere in between), and is very invasive it how it does that... to the exclusive exclusion of other things, or branding. I am just referring to Virtuals here... If you install turn on Hyper-V, it exclusively takes over all hardware virtualization capabilities of that computer... Just the facts.

Beyond that... I can remember that the first few version of Ubuntu... The 32bit version, back then, was more universal and stable than its 64bit code. 17 years ago, it was a different world. And 32bit code you could install on either 64bit or 32bit hardware. That is what I had installed 17 years ago... on 64bit hardware.

Honestly, the biggest challenge to installing Ubuntu 4.04 as a KVM guest, was not the video for me, but to was guess what CPU capabilities and storage controller types to replicate.

---

