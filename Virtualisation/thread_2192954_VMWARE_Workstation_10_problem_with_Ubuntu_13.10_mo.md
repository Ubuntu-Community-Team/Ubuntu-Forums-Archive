---
title: "VMWARE Workstation 10 problem with Ubuntu 13.10 mouse and keyboard"
date: 2013-12-10
forum: Virtualisation
---

### Post by wrtell99 on 2013-12-10
Hi,

I am evaluating VMware Workstation 10 versus Virtual Box. When I install  Ubuntu  13.10 VM  under VMware , the mouse and keyboard do  not work.
I can make the keyboard work by enabling the  VMmare option for  an extended keyboard but the mouse will not function. I have to directly attach a mouse to the Ubuntu   Virtual Machine via a modification to the VMware VM  initialization parameters  in order  to have  access to it..

Ideas  on how I can resolve this or what  I need to provide in order to fix it would be appreciated.
 
Thanks

---

### Post by drmrgd on 2013-12-10
I usually use VWware Player instead of Workstation, so there may be some differences.  But, I wonder did you install the VMware tools after you set up the Ubuntu VM?  I can't imagine why it should affect your mouse, but I have seen some strange things get fixed by installing the VMware Tools.

---

### Post by electrohandyman501 on 2013-12-10
Yea, I had to install the VMWare tools as well to get things to work right. I also had to disable the option 'Accelerate 3D Graphics'.

Also on your VM setup screen, options tab, general settings, look for the drop down option box for enhanced keyboard. Mine is off, but there are other options(us if available, or required). Maybe try a different setting there.

I also am using VMWare Player 5.0.2 instead of workstation.

---

### Post by wrtell99 on 2013-12-13
Hi,

First, thank you for  the replies to my thread. 
In answer to the question
"Did I install the VMware tools?" Yes, I did so. In fact ,more than once<Smile>. The problem persisted.

I tested the VM with  3D acceleration enabled and disabled. It made no difference. 
 
Because of the cost of VMware 10 workstation  and the significance of poor keyboard and mouse support in
Ubuntu , I moved back to Virtualbox. However with my upgrade to Windows 8.1 Pro on this machine, the V4.3.x  level of VB has problems.
VB 4.2 works fine and I use  VB 4.2.20. 

I am in the process of upgrading another of my PCS,  that I do not use, to Windows 8.1 Pro. I will install VMWARE on it. Determine if the this issue persists and if so gather more diagnostic information. 



Once again than you for the  feedback and any further ideas  will be appreciated.

---

