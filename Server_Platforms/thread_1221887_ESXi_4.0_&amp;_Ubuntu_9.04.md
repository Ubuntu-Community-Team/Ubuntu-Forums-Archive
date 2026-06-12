---
title: "ESXi 4.0 &amp; Ubuntu 9.04"
date: 2009-07-24
forum: Server Platforms
---

### Post by archmage258 on 2009-07-24
When I try to install 9.04 (x64) on a VM I get an error message that "This kernel requires an x86-64 CPU, but only detected an i686 CPU.  Unable to boot - please use a kernel appropriate for your CPU." 
 
I can install the x86 versions of both 8.04 and 9.04 just fine.  I am using a Dell 2950 with 2 Xeon processors (for those wondering if I actually DO have an i686).

On an unrelated note, does anybody have a VMware image for ESXi of server 9.04?:o

---

### Post by Vegan on 2009-07-24
Which processors are you using, check them on Intel's page to see what they support.

---

### Post by dragos2 on 2009-07-24
Clarify this first:

1. You are trying to run ESXi on top of Ubuntu ?

2. Did you enabled the CPU virtualization features from BIOS ?

My guess is that you installed a 32 bit OS and you want to virtualize
64 machines. Not all virtualization solutions can do that.

---

### Post by windependence on 2009-07-25
Dragos, ESXi is a bare metal hypervisor. It doesn't run on top of anything. 

To the OP, make sure you selected the correct OS when you created the VM. 

For the appliance, here ya go:

[http://www.vmware.com/appliances/directory/229803](http://www.vmware.com/appliances/directory/229803)

Here is 8.04 LTS Server also:

[http://www.vmware.com/appliances/directory/128633](http://www.vmware.com/appliances/directory/128633)

-Tim

---

### Post by bacil on 2009-07-25
Some clarification needed.

ESX is linux kernel with hypervisor libraries compiled to it. what ever EMC (VMware) says. Usual line goes like this : "Yes management console is linux, but hypervisor is not" thats true except hypervisor will not run withut console and if you analyze kernel properly you see hypervisor libraries loaded.

ESX have problems emulating 64bit hw even tho you have got Xeon 5000 you have to have enabled Intel Virtualization Technology, Intel Hyper-Threading Technology, Enhanced Intel Speedstep Technology and Execute Disable Bit. then in vm setup you have to select 64bit to tell to esx to bypas its standard 32bit instruction set

---

### Post by windependence on 2009-07-25
Look, if you want to quote this crap in every thread about ESXi that's fine, but you're not answering the Op's question. Do you do this every day for a living like I do? Are you a VMware Partner? We can argue all day about whether it's a Linux kernel or runs on true bare metal. No body cares. My clients don't care. I don't care.

What I do know is ESX is a different product than ESXi, yes even different binaries. It works just fine with a 64 bit OS if it's set up properly. I'm trying to find out how he has it set up so I can help him overcome the error because I KNOW it works. AFAIK, there is no place in the VSphere client to bypass the standard 32 bit instruction set. If you choose the correct OS and have your BIOS set right, there should be no problems. I have done tons of these installs with little or no problems.

-Tim

---

### Post by PilotJLR on 2009-07-27
OP, sounds like (as others have already said), you need to enable VT in the BIOS. On many occasions, this requires enabling VT, then shutting the server off! I mean powered down, not a warm reboot. And then restart, and you should be able to support 64 bit guests.

As for the linux kernel stuff, I'm just going to give up on that. I've responded to several threads here on this subject (as have you, Tim), but no one believes it. People see an anaconda based install, and they see GRUB and a CentOS COS, and they assume it's linux through and through. In reality, the hypervisor is not a linux kernel, though the COS can see it as a process. You'd think ESXi would really drive home the fact that VMkernel is not linux, but I guess not.

---

### Post by JimmyJam4PHP on 2009-08-13
Just to clarify to folks finding this later, the phrase "set VT in the BOIS"  means that you need to reboot the physical server that ESXi is loaded on and look for a setting, under "CPU Configuration" or similar that says "Virtualization Technology" and change it from disabled to enabled.

---

