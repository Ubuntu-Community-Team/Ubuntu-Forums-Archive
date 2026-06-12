---
title: "Seamless/fullscreen using both screens of dual-head display?"
date: 2008-01-03
forum: Virtualisation
---

### Post by hashstat on 2008-01-03
I compiled and installed the open-source version of VirtualBox on Ubuntu Gutsy 7.10. I then created a Windows XP Pro SP2 guest and installed the open-source guest additions from code.google.com. Everything works great. But the seamless and fullscreen modes do not work as I expected.

I have identical dual-monitors connected to an ATI Radeon Mobility X600 video card using the proprietary drivers from the Ubuntu repositories with big desktop enabled. I can enter seamless mode on either display, however, the Windows windows are restricted to that display; I cannot move them to the other display. Similarly, I can enter fullscreen mode on either display, but not over the entire desktop (both displays). Does anyone know how to use VirtualBox with both displays?

Thanks.

---

### Post by |2eason on 2008-01-03
You would have to run two VMs at the same time.

ps. the source for the additions is included with the source tarball. It also downloads automatically if VB can't find the iso.

---

### Post by |2eason on 2008-01-03
No, sorry, ignore the above. I just rechecked the manual (it's been updated) and it is possible to run multiple monitors with XP as a guest. Check Chap 9.6 of the [Manual]("http://www.virtualbox.org/download/UserManual.pdf").

---

### Post by hashstat on 2008-01-03
> No, sorry, ignore the above. I just rechecked the manual (it's been updated) and it is possible to run multiple monitors with XP as a guest. Check Chap 9.6 of the Manual.

I read that earlier today.  It requires VirtualBox RDP, which is not included in the open source edition of VirtualBox.  All I want is for fullscreen and seamless modes to use my entire desktop, which happens to span two monitors.  I have read of others doing this with the NVidia drivers and Xinerama.  Could this be more of a window manager issue than a VirtualBox issue?  If so, does anyone know a way to tell the window manager to report the appropriate desktop, position, size, etc. information to VirtualBox?

---

### Post by |2eason on 2008-01-03
> **hashstat said:**
> I read that earlier today.  It requires VirtualBox RDP, which is not included in the open source edition of VirtualBox. 
Lol, switch to the binary then.

---

### Post by arjun.me on 2008-02-13
Hi I tried what the manual sais but I get hits lil confuzes.....
 "arjun@arjunLin:~$ VBoxManage modifyvm wxp -monitorcount 2
VirtualBox Command Line Management Interface Version 1.5.4
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] FAILED calling virtualBox->FindMachine(Bstr(argv[0]), machine.asOutParam()) at line 3410!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070057
[!] Text        = Could not find a registered machine named 'wxp'
[!] Component   = VirtualBox, Interface: IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
[!] Callee      = IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
arjun@arjunLin:~$ [http://ubuntuforums.org/register.php?a=act&u=503381&i=26660525](http://ubuntuforums.org/register.php?a=act&u=503381&i=26660525)

---

### Post by arjun.me on 2008-02-13
VirtualBox Command Line Management Interface Version 1.5.4
(C) 2005-2007 innotek GmbH
All rights reserved.

Name:            WXP
Guest OS:        Windows XP
UUID:            7b649e77-6556-472b-9288-ae2e0d81ec36
Config file:     /home/arjun/.VirtualBox/Machines/WXP/WXP.xml
Memory size:     509MB
VRAM size:       65MB
Boot menu mode:  message and menu
ACPI:            on
IOAPIC:          off
Time offset:     0 ms
Hardw. virt.ext: off
State:           running (since 2008-02-13T13:28:53.108000000)
Monitor count:   1
Floppy:          empty
Primary master:  /home/arjun/.VirtualBox/VDI/WXP.vdi (UUID: 9766adc7-1408-4333-b899-aa812629c197)
DVD:             Host drive /dev/hdb
NIC 1:           MAC: 080027E54EF8, Attachment: NAT, Trace: off (file: <NULL>)
NIC 2:           disabled
NIC 3:           disabled
NIC 4:           disabled
UART 1:          disabled
UART 2:          disabled
Audio:           enabled (Driver: Null)
Clipboard Mode:  Bidirectional
VRDP:            enabled (Port 3389, Authentication type: null)
Shared folders:  <none>

---

### Post by TheSimkin on 2008-06-06
There is one fix.  Although it does mean you lose some functionality on your linux desktop.

The fix is to disable Xinerama.  Then the the system will treat your two screens as one.  And then you can use both screens in seamless mode.

It works well for us!

---

### Post by Sebo on 2009-03-04
You should try

VBoxManage modifyvm "WXP" -monitorcount 2


It's case sensitive

---

### Post by Ng Oon-Ee on 2009-03-04
> **Sebo said:**
> You should try

VBoxManage modifyvm "WXP" -monitorcount 2


It's case sensitive
He states he's using OSE, so that wouldn't work I believe.

---

