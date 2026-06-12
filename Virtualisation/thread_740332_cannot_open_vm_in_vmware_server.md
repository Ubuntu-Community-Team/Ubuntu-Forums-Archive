---
title: "cannot open vm in vmware server"
date: 2008-03-30
forum: Virtualisation
---

### Post by Matt26 on 2008-03-30
i have a windows xp vm that i created in vmware workstation 6, and i have recently removed workstation and installed vmware server as an alternative.. the problem that i am having is that when i try to open the xp vm under vmware server i get an error message saying:

Configuration file was created by a VMware product with more features than this version

is there any way that i can have vmware server open this vm without any issues?

thanks.

---

### Post by fjgaude on 2008-03-30
It's a VM created for Player... ASAIK.

If it was then I've never able to open such in Server.

---

### Post by Matt26 on 2008-03-30
sorry i don't understand the first line of your response.. i created the vm in workstation and i want to open it in server if possible..

---

### Post by fjgaude on 2008-03-30
> **Matt26 said:**
> sorry i don't understand the first line of your response.. i created the vm in workstation and i want to open it in server if possible..

I know that Server doesn't have the full features of Player, and likely not that of Workstation.

If someone knows differently, please let us know. Thanks.

---

### Post by mvan83 on 2008-03-31
Can you post the vmx file? You should be able to comment out certain options to get it work under the "lesser" vmware. I might be able to help you here.

---

### Post by Matt26 on 2008-03-31
i was given a suggestion that vmware converter should be able to make my vm readable in vmware server, so i am going to try that first... i will post my vmx file here if that option doesn't work out.  thanks.

---

### Post by Matt26 on 2008-03-31
ok, so i tried the vmware converter application which gave me an error message when trying to read the vmx file for my vm- unable to determine guest operating system.. i looked up the error message and it might be related to permissions on the folder that my vm is located in, and i am accessing the vmx file in vmware converter from a separate windows xp pro PC using a mapped network drive to the folder on the ubuntu system that my vm files are in... so is there a way that i can verify that i have the full permissions necessary to complete this task?

---

### Post by prickly on 2008-05-25
I have the same issue and I am looking in to it now.

I notice that VMWare server lets you create VM's that are compatible with WorkStation 4.

I am in the process of creating a VM that is identical to the one I have in WorkStation 6 to see what is different in the .vmx file.

EDIT 

Well I managed to edit the .vmx file enough to get the VM to show up as a tab in VMWare Server but got the following error message when I tried to boot it:

> One or more of the disks used by this virtual machine was created by an unsupported version of VMware Server. To power on or upgrade the virtual machine, either remove the unsupported disk(s) or use a version of VMware Server that supports this version of disks. Below is a list of the disks and their reported versions.

Version 6  Ubuntu.vmdk

EDIT

I also downloaded VMWare converter and it was unable to identify the operating system of my virtual machine (which was Ubuntu JeOS) ... it should work for Windows OS at the very least though I would assume ...

---

### Post by Matt26 on 2008-05-25
> **prickly said:**
> I have the same issue and I am looking in to it now.

I notice that VMWare server lets you create VM's that are compatible with WorkStation 4.

I am in the process of creating a VM that is identical to the one I have in WorkStation 6 to see what is different in the .vmx file.

EDIT 

Well I managed to edit the .vmx file enough to get the VM to show up as a tab in VMWare Server but got the following error message when I tried to boot it:

EDIT

I also downloaded VMWare converter and it was unable to identify the operating system of my virtual machine (which was Ubuntu JeOS) ... it should work for Windows OS at the very least though I would assume ...

i got mine to work by reinstalling workstation 6 (latest build) on my ubuntu system and using it to convert my vm to workstation version 5 so it would be compatible with server 1.5...

---

