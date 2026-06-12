---
title: "How to convert VBox machine to VMware"
date: 2008-04-28
forum: Virtualisation
---

### Post by bmwman on 2008-04-28
Does anyone know how to convert VBox virtual machine to VMware? 

I've been using Virtual box for a while and do like it, especially the seamless mode. But I was able to convert my physical system to VMware virtual(on another computer) and i think it works better and it's easier to configure. With VBox i have to setup my bridged network every time i reboot and the USB support is kinda tricky too. All that is really easy with VMware. Anyway, i have my Vbox setup with al my work applications and settings and was wondering if i can convert to Vmware and don't have to reinstall everything again.

Thank you.

---

### Post by bmwman on 2008-04-28
I did some research and found out that it could be done with QEMU. I installed and tried to do it, but couldn't figure it out. The code should be something like : qemu-img.exe convert -O vmdk hdd.vdi hdd.vmdk

Does anyone knows exactly how to complete the task? :)

---

### Post by bmwman on 2008-04-28
I figured it out!! YAY!!

 "sudo qemu-img convert /home/emil/.VirtualBox/VDI/WindowsXP.vdi  /home/emil/Desktop/XP.vmdk"

I'm not sure if need to be executed with "sudo" but that worked for me. Now I can switch to Vmware Virtual Machine from Virtual Box.

P.S. I want to close this thread but i'm not sure how :)

---

### Post by fjgaude on 2008-04-28
Go to the top of the forum and use Thread Tools menu, to use [SOLVED]. With the new forum software it shows then at the bottom, left of the posts.

Do you know if you can go the other way, .vmdk to .vdi?

---

### Post by bmwman on 2008-04-28
> **fjgaude said:**
> Go to the top of the forum and use Thread Tools menu, to use [SOLVED]. With the new forum software it shows then at the bottom, left of the posts.

Do you know if you can go the other way, .vmdk to .vdi?

I'm pretty sure it would work. Actually I had to convert to VMX instead of VMDK. It completed with no errors but when I tried to open it with VMware Workstation i get error and does not work :(

I guess I need to keep searching for solution.

---

### Post by fjgaude on 2008-04-28
Gosh, .vmx is really just a config file... I would think more would have to be converted.

Let us know if you ever succeed.

---

### Post by bmwman on 2008-04-29
Well, when you try to open the virtual machine from VMware Workstation is searching for VMX file. I assumed that is the actual virtual hdd. The qemu "converted" to .vmdk and .vmx but neither one worked.

Dunno what to do :)

---

### Post by fjgaude on 2008-04-29
It would seem that the <name>-flat.vmdk is the one that has to be converted. Likely we'll have to wait until someone who has done it shows how. <smile>

Thanks for your efforts.

---

### Post by bmwman on 2008-04-29
I did that the first time. Again the process completed with no errors and I converted my XP.vdi to XP.vmdk. But when you try to open it from VMware it's searching only for .vmx file. I guess there has to be some kind of configuration file with the XP.vmdk. I found multiple How-Tos  online to convert vmware to vbox but not the other way around :)

I'll keep searchin

---

### Post by snakerdlk on 2009-03-04
Converting from vdi to vmdk probably just converts the virtual disk(since each program, VirtualBox and VMware have diferent configuration sets, I've read that Virtualbox has a xml file somewhere whereas VMware has the vmx file.)

I suggest creating a new virtual machine on vmware(with the desired configurations and the virtual disk option, of course) and then manually switching the vmdk file from this vm.

---

### Post by Dedoimedo on 2009-03-04
> **fjgaude said:**
> It would seem that the <name>-flat.vmdk is the one that has to be converted. Likely we'll have to wait until someone who has done it shows how. <smile>

Thanks for your efforts.

Hello,

Use VMware Converter to convert the ESX pre-allocated flat file to VMware Player/Server/Workstation file and then proceed as usual with qemu.

[http://www.vmware.com/products/converter/\](http://www.vmware.com/products/converter/\)

The application works in 4 stages:
1) choose source - esx/esxi server, real machine etc
2) choose destination - vmware server, e.g. version 2.
3) choose additional options for vmx - memory size, network, control etc.
4) convert and enjoy.

BTW, tutorial on the way, already written, waiting its pipe turn :)

Cheers,
Dedoimedo

---

### Post by Kenzumi on 2009-03-08
> **bmwman said:**
> I figured it out!! YAY!!

 "sudo qemu-img convert /home/emil/.VirtualBox/VDI/WindowsXP.vdi  /home/emil/Desktop/XP.vmdk"

I'm not sure if need to be executed with "sudo" but that worked for me. Now I can switch to Vmware Virtual Machine from Virtual Box.


You forgot to tell qemu in which format you want to convert. And you don't need sudo.
The command line is the following :

```

qemu-img convert -O vmdk WindowsXP.vdi WindowsXP.vmdk

```

Don't tried yet on VMWare but with this command I had no errors in the conversion.

I hope it will help you too.

---

### Post by snakerdlk on 2009-03-10
vmware server 2.0 and esx 3.5 did not accept the converted vmdk file.
Vmware server accused the file not being a valid vmdk file.

I've read that the vditool could convert vdi to raw and then through qemu you made a vmdk form a raw file...
Still searching...

---

### Post by Dedoimedo on 2009-03-11
Use the Converter to convert the file to vmware server 2.0 format for vmware server and infrastructure format for esx.

Dedoimedo

---

### Post by calsaverini on 2009-08-13
This link have working instructions on how to do it if your VBox disk is dynamically resizable:

[http://www.liucougar.net/blog/archives/118](http://www.liucougar.net/blog/archives/118)

Should work for static size VM's too.

---

### Post by bohemius on 2010-08-25
It is very simple, at-least with the following versions


[LIST]
[*]VirtualBox  3.1.8
[*]VMWare Workstation 7.1.1
[*]Windows 7 32-bit guest
[*]Ubuntu 10 64-bit host
[/LIST]

just run the following in terminal

```
VBoxManage clonehd --format VMDK <original_disk>.vdi <new_disk>.vmdk
``` and then create a new VM in VMWare and tell it to use the VMDK file you just created by the clone operation as disk image.  My VDI was 40GB and the VMDK just 15GB.  VMWare Workstation even said the file is older VMDK version and automatically converted it.  If you get an error from VBox complaining  about disk being already registered, just move your ~/.VirtualBox directory to something like ~./VirtualBox.bak and run the command again.  Your new image will be in ~/.VirtualBox/HardDisks/.  Move it where ever you want it and then restore the original ~/.VirtualBox dir should you need it. Other than that, everything worked flawlessly.  No need for any additional tools to do this.

---

### Post by cuculus on 2010-09-21
I have the vmdk file but when I try to 'open' it using 'Create a New Virtual Machine' in Player (3.1.1) it will not accept the vmdk file in the 'Installer disc image file (IS)' box, which isn't surprising considering it tells you it wants an iso file...  

Bohemius' instructions said "and then create a new VM in VMWare and tell it to use the VMDK file you just created by the clone operation as disk image."  

Now what?

---

### Post by TheFu on 2010-09-22
I believe the different VMware virtualization tools have different internal VDMK structures.  I know that the File-->Export from VBox will create a VDMK that works in ESXi 4.x - did that just a few months ago.  To convert between the different VMware virtualization tools, I've heard about converters, but never used them.  I've also exported from ESXi and loaded those VDMK files into VirtualBox.  The main issues that I've seen were related to MS-Windows wanting to re-activate due to the underlying HW changes.

---

### Post by mdacova on 2011-05-13
> **bmwman said:**
> I figured it out!! YAY!!

 "sudo qemu-img convert /home/emil/.VirtualBox/VDI/WindowsXP.vdi  /home/emil/Desktop/XP.vmdk"

I'm not sure if need to be executed with "sudo" but that worked for me. Now I can switch to Vmware Virtual Machine from Virtual Box.

P.S. I want to close this thread but i'm not sure how :)


thanks helped me also

---

### Post by alecz20 on 2011-08-16
> **cuculus said:**
> I have the vmdk file but when I try to 'open' it using 'Create a New Virtual Machine' in Player (3.1.1) it will not accept the vmdk file in the 'Installer disc image file (IS)' box, which isn't surprising considering it tells you it wants an iso file...  

Bohemius' instructions said "and then create a new VM in VMWare and tell it to use the VMDK file you just created by the clone operation as disk image."  

Now what?

I have to admit, I had a good laugh on your post (no offense though).

The vmdk file is a Virtual Hard Disk file. You cannot install the operating system from a hard disk. Actually you don't even need to install it.

When you convert the .vdi to .vmdk you simply change the format of the virtual hard disk from Virtual Box format to VMware format.

The next stem is to create a VMware Virtual machine. (choose "install operating system later"). After the machine is created, go to "Customize Hardware" and change the hard drive with the converted one. Then boot and it should work.

I find VMware a little cumbersome because you cannot choose an existing hard drive at the time of virtual machine creation. It seems they never anticipated someone moving virtual hard drives to new virtual machines.

Anyhow, I did this  and it worked.

So again, the .vmdk file is only the hard disk file it does not have any virtual-machine related info. If you want to have those you should go to File -> Export, and export the VM in OVA/OVF then import in VMware (haven't tried this though)

EDIT: the command is:
```

vboxmanage clonehd --format VMDK <source image|uuid> <destination image>

```
If on windows, then you have to open a console (Start -> Run -> cmd) and travel to where you installed Virtual Box, and run the command from there, but replace vboxmanage with VBoxManage.exe

---

