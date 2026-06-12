---
title: "How to enable desktop composition on VMware Workstation?"
date: 2010-11-08
forum: Virtualisation
---

### Post by max404s on 2010-11-08
I have installed Ubuntu 10.10 on VMware Workstation and desktop composition is not enabled.
 
How do I enable it?
 
Thanks.

---

### Post by HermanAB on 2010-11-09
It is a Windows feature as far as I know.  Best left off, else your VM will be slow.

---

### Post by max404s on 2010-11-09
Thanks for your answer Herman, but what I am talking about is desktop composition in Ubuntu, which allows the desktop effects and so allows things like Docky and Compiz to work.  I am only getting the basic plain GUI.
 
I cannot get them working through VMware Workstation.  Is it even possible?  VMware Workstation is supposed to allow the virtual machines to access the hardware acceleration of the real physical graphics card.

---

### Post by HermanAB on 2010-11-10
Graphics capability is limited on a VM.

---

### Post by max404s on 2010-11-10
Yes, it is usually, but VMware Workstation allows the VM to access the graphics card directly and not use a virtualised graphics card.
 
Does this not work with Linux then?  Only Windows?  I have the integration tools installed, but I am not sure if I have done it properly.

---

### Post by dcstar on 2010-11-13
> **max404s said:**
> I have installed Ubuntu 10.10 on VMware Workstation and desktop composition is not enabled.
 
How do I enable it?
 
Thanks.

Go into the VM's settings Display options and turn on the Accelerate 3D Graphics.

---

### Post by applegate on 2010-11-14
I Enable 3D acceleration in VM Ware and still no Desktop Effects could be activated.
 
Whats the solution?
 
 
Virtual Machine Ubuntu 10.10 x64
 
Use VM Ware Workstation 7.1.2 on host Windows 7 ULT x64 , Nvidia GeForce 9600 GT, 6 GB memory and Intel quad core Q8300 with Intel VT).

---

### Post by applegate on 2010-11-14
I try Virtualbox right now instead of VM Ware.
 
The first one should be able to do the job.
 
If it works I will let you all know.

---

### Post by applegate on 2010-11-17
I do not get the Desktop Effects working in both the latest versions of VMWare and Virtualbox.
 
Help needed?
 
Thanks in advance.
For more info see post in this thread

---

