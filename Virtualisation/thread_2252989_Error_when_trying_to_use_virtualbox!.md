---
title: "Error when trying to use virtualbox!"
date: 2014-11-16
forum: Virtualisation
---

### Post by bio2 on 2014-11-16
I tried using virtualbox to emulate windows 7 and it gave me this error. 

Failed to open a session for the virtual machine Win 7.
VT-x is disabled in the BIOS. (VERR_VMX_MSR_VMXON_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}



I then gave up! Soon after I thought it was just cuz of the specific OS I was trying to emulate so I downloaded the Anonymous OS
.iso file. I followed a step by step tutorial and i get the same dreaded error!

Failed to open a session for the virtual machine Anonymous.

VT-x is disabled in the BIOS. (VERR_VMX_MSR_VMXON_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}

---

### Post by bashiergui on 2014-11-16
That is telling you that your computer is able to do virtualization, but it is not enabled in the BIOS. 

If you don't know how to change the setting in the BIOS then Google "VT-x is disabled in the BIOS" along with the make and model of your computer. I'm sure you'll find a detailed tutorial showing you how to enable virtualization in the BIOS.

---

### Post by firegrim on 2015-05-02
I have tried enabling it and disabling it many times, as well as restarting the whole system. Nothing seems to help with this problem. And nobody seems to know how to actually fix it...

---

