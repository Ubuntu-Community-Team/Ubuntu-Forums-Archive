---
title: "Get Virtual box to connect to internet"
date: 2007-12-04
forum: Virtualisation
---

### Post by Dapman01 on 2007-12-04
I just installed windows vista to my virtual box and I have two questions
1.  Is it possible for it to connect to the internet if so how
2. How do I get Vista to mount usb devices

---

### Post by mozetti on 2007-12-04
I'm at work, but when I get home (10-12 hours) I'll try to find the info I used. To answer your question, yes you can get Vista to connect to the internet. I used the VirtualBox help files (i'm pretty sure) and it discussed multiple ways to configure virtual network adapters. Give it a go, or wait for me to let you know which method I used later on today.

Regarding USB devices - have you installed the (forget the exact name) Virtualbox Helper Tools, or something like that? There's info in the help files on installing that, too.

---

### Post by Dapman01 on 2007-12-04
I think I'll wait for you, thanks

---

### Post by daengbo on 2007-12-04
Dapman01,

New VirtualBox machines are set up by default to use NAT, which means that the guest OS will get an IP (10.x.x.x) through DHCP and should connect automatically. Is your problem with VirtualBox or with Vista?

---

### Post by Dapman01 on 2007-12-04
How can I tell?
Also How do I get an existing Vista partition to run in Virtualbox

---

### Post by Dapman01 on 2007-12-04
bump

---

### Post by maybeway36 on 2007-12-04
Install the Guest Additions, it includes a network driver for Vista.

---

### Post by Dapman01 on 2007-12-04
How do I do that in kubuntu

Also I am having a problem starting/deleting/editing that partition after messing with the settings in the virtual machine
For deleting

Assertion failed: [VBOX_SUCCESS (vrc)] at '/build/buildd/virtualbox-ose-1.5.0-dfsg2/src/VBox/Main/MachineImpl.cpp' (4681) in nsresult Machine::openConfigLoader(CfgLoader**, bool).
VERR_OPEN_FAILED (-101) - File/Device open failed..
Please contact the product vendor!.


Result Code: 
0x80004005
Component: 
Machine
Interface: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}


For Starting

Unknown error creating VM (VERR_GENERAL_FAILURE).
VBox status code: -1 (VERR_GENERAL_FAILURE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
For editing settings

Assertion failed: [VBOX_SUCCESS (vrc)] at '/build/buildd/virtualbox-ose-1.5.0-dfsg2/src/VBox/Main/MachineImpl.cpp' (4681) in nsresult Machine::openConfigLoader(CfgLoader**, bool).
VERR_OPEN_FAILED (-101) - File/Device open failed..
Please contact the product vendor!.


Result Code: 
0x80004005
Component: 
Machine
Interface: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}



I don't mind deleting the VM and starting a new one, but it won't even let me delete it

---

### Post by christina_svats on 2007-12-04
I don't know if it helps but i followed these instructions and had no problem with network connection in Windows (check out step2 for configuring the network):

[http://ubuntuforums.org/showthread.php?t=433359&highlight=canon](http://ubuntuforums.org/showthread.php?t=433359&highlight=canon)

If you want to mount usb devices you should not use the open source edition, which is offered in Add/Remove, since it does not support usb devices.

---

### Post by markharding557 on 2007-12-04
guest additions is run from the menu in virtualbox
ms disabled networking in vista on vms to make it more difficult,see link below
> Windows Vista guests ¶

    * There is no networking in Windows Vista guests initially because, unfortunately, with Vista, Microsoft dropped driver support for the virtual AMD PCnet card that we are providing. See "Troubleshooting" -> "Windows guests" in the User Manual for a solution. The VirtualBox Guest Additions contain the AMD PCnet driver. 



---

### Post by Dapman01 on 2007-12-04
> **markharding557 said:**
> guest additions is run from the menu in virtualbox
ms disabled networking in vista on vms to make it more difficult,see link below

Where in the menu do I run guest additons

So if I'm reading this right, is it impossible to get internet in Vista
can anyone tell me how to get vista to detect usb harddrives

also

---

### Post by Dapman01 on 2007-12-04
:confused:

---

### Post by Dapman01 on 2007-12-05
bump

---

### Post by RedMist on 2007-12-05
To get guest additions, boot up your VM and under the "Devices" tab, there is a "install guest additions" tab. Hit that and follow the onscreen prompts.

For internet, you need to install the driver from guest additions. Bring up the hardware wizard in the Vista VM and locate the ethernet driver. Select update driver, click that you have it on file and navigate to the Guest additions cd which should be already virtually mounted. Inside the cd there is a directory "AMD_PCnet".
This is the driver.

Unfortunatly you wont be able to have shared folders in Vista yet, only internet with this driver. Hope this helps.

---

### Post by mozetti on 2007-12-06
Also, here is some info I posted in the event you want your Vist VM to get it's own IP address on the LAN (192.168...) versus the default guest IP the VM gets from the hose (10....)

---

### Post by Dapman01 on 2007-12-07
> **RedMist said:**
> To get guest additions, boot up your VM and under the "Devices" tab, there is a "install guest additions" tab. Hit that and follow the onscreen prompts.

For internet, you need to install the driver from guest additions. Bring up the hardware wizard in the Vista VM and locate the ethernet driver. Select update driver, click that you have it on file and navigate to the Guest additions cd which should be already virtually mounted. Inside the cd there is a directory "AMD_PCnet".
This is the driver.

Unfortunatly you wont be able to have shared folders in Vista yet, only internet with this driver. Hope this helps.

When I clicked on the install guesst additions tab, nothing happened.  Is it because Vista is running?

---

### Post by Dapman01 on 2007-12-07
> **Dapman01 said:**
> When I clicked on the install guesst additions tab, nothing happened.  Is it because Vista is running?

Nevermind, Now I just got to get the USB working, Does anyone know how to do that

---

### Post by Dapman01 on 2007-12-07
bump

---

### Post by christina_svats on 2007-12-07
which version of virtualbox do you use? Are you sure it's the one that supports usb devices?

---

### Post by conner on 2008-02-23
Hi this is my first posting in english, may be I've found the solution for this case 

**Bring Vista And Network To Work In A VirtualBox** 
[ http://www.bolm24.de/content/view/28/9 ]("http://www.bolm24.de/content/view/28/9/lang,english/") 


Greetz Conner
:guitar:

---

### Post by Claude Renaud on 2008-02-23
I found a lot of answers to my questions in the 182 page User manual:
see [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by jimbosheep101 on 2008-06-01
ok look mate but its almost impossible to get virtual box working with usb

u can in windows and os x but not linux

for some reason in the old version of virtual box (for linux ) it had a usb option but u had to change a lot of ur sorcecode to make it work, but in the new version they have removed the usb option on the linux version, so now i am afraid to say that u wont be able to use ur pen drive with virtual box...... sorry mate!!

---

