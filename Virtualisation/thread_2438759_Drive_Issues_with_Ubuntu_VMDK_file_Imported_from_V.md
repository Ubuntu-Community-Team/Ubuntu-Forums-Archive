---
title: "Drive Issues with Ubuntu VMDK file Imported from VirtualBox"
date: 2020-03-17
forum: Virtualisation
---

### Post by fstephane on 2020-03-17
My company distributes a local web server that runs on an Ubuntu VM. Our default deployment is to install VirtualBox on a client's physical server.
 
Some of our clients use virtual servers, so we've been trying to accommodate VMWare and Hyper-V installs. We've installed live versions on VMWare twice successfully as well as on a trial version of VMWare Workstation 15.5. So far we've done this by taking the raw VMDK file from a VirtualBox instance and adding it as a harddrive to a new VMWare instance.
 
We've run into a problem with a new client that is running VMWare ESXi 6.0 (with vSphere and vCenter). They went through a similar process to create a new VM and add the VMDK file as a hard drive, but the VM is failing in the boot sequence:

[SIZE=6][ATTACH=CONFIG]285229[/ATTACH][/SIZE]
 
My knowledge with Ubuntu and VMWare is very limited, so I'm at a bit of a loss how to proceed. The client's IT guy tried running the fsck command manually, but it kept giving us the same error for multiple devices:

 [ATTACH=CONFIG]285231[/ATTACH]

and eventually threw this:
 
[ATTACH=CONFIG]285230[/ATTACH]
 
The fact that we've got this working on three different VMWare systems leads me to believe the issue might be with the way we're adding the hard drive, or with the VM settings.
 
Has anyone else tried doing this sort of import of a VirtualBox VMDK file into VMWare? Is there a better way to do this, maybe using the VBox OVA file instead? Any relevant VM settings I can tinker with?
 
Any context or suggestions would be greatly appreciated! Please let me know if you need additional information

---

### Post by fstephane on 2020-03-22
The issue appears to be that the VMDK file is not in a valid format for VMWare ESXi 6.0

[COLOR=#666666][FONT=proxima-nova]I am able to grab the VMDK file from a VirtualBox VM and import that directly into a new VM in a trial version of VMWare Workstation 15.5. This lead me to believe the same method would work in any version of VMWare, but this is apparently not the case.[/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova] [/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova]I ended up using VMWare's OVFTool to convert the VBox OVA file to a VMX + VMDK file. I'm not sure exactly what happens to the VMDK file during this process, but the client was able to use the resulting VMDK file on their ESXi host.[/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova] [/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova]So it appears VMDK files are not directly transferable from VBox to all versions of VMWare. And VMWare OVFTool can be used to generate a valid VMDK file instead. Hope this can be helpful to others![/FONT][/COLOR]

---

