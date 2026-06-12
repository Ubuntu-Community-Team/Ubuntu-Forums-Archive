---
title: "VirtualBox on Ubunto"
date: 2015-02-13
forum: Virtualisation
---

### Post by bulldog2 on 2015-02-13
Hope I have posted this in the right place.
 I have installed virtualbox, but when I  start  I get the following error message.
 Failed to open a session for the virtual machine **XP Home**.
 VT-x is disabled in the BIOS. (VERR_VMX_MSR_VMXON_DISABLED).
 [TABLE="width: 100%"]
 	 	 	[TR]
 		[TD="width: 20%"] 			Result Code:  			
 		[/TD]
 		[TD="width: 80%"] 			NS_ERROR_FAILURE (0x80004005)
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 20%"] 			Component:  			
 		[/TD]
 		[TD="width: 80%"] 			Console
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 20%"] 			Interface:  			
 		[/TD]
 		[TD="width: 80%"] 			IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}
 		[/TD]
 	[/TR]
 [/TABLE]
 


 I am new to Linux and ubuntu, so would appreciate any help.

---

### Post by slickymaster on 2015-02-13
Moved to the **Virtualisation** sub-forum.

Hi bulldog2, welcome to the forums.

> **bulldog2 said:**
> <---snip--->
 Failed to open a session for the virtual machine **XP Home**.
 VT-x is disabled in the BIOS. (VERR_VMX_MSR_VMXON_DISABLED).<---snip--->
This means you need to enable VT-X in your host machine's BIOS. After enabling VT-x in the BIOS you should shut-down your PC rather than reboot. A quirk in many BIOS's result in the setting change not taking hold unless the system shuts down for a short time.

---

### Post by TheFu on 2015-02-15
Virtualbox should work fine without VT-x enabled. It does on a Windows host, but I haven't tried it on a Linux host in many years - since VT-x became mostly standard.  Also, changing other VM options related to the motherboard will freak out Windows and require a reinstall.

At this point, running XP should only be performed in a VM and only without any networking enabled.

So - I googled that error: [https://www.virtualbox.org/ticket/12424](https://www.virtualbox.org/ticket/12424) - explains to turn off logmode.

---

### Post by SeijiSensei on 2015-02-15
You need to enable VT-x to run 64-bit guests on 64-bit hosts.  OP, look in the BIOS and turn on VT-x.  Sometimes it's called "Intel Virtualization" or some similar name.

---

