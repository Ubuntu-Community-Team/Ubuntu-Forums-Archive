---
title: "Hardware help with PCIe-Passthrough/QEMU/KVM"
date: 2017-02-04
forum: Virtualisation
---

### Post by pseverino on 2017-02-04
I've been messing around with Linux, mainly Ubuntu with Cinnamon installed for a few years now but mainly use windows because I'm a gamer. I recently learned about PCIe Passthrough and am interested, but only have one GPU and want to make sure everything is compatible before I throw money at it. Can someone more knowledgeable than me tell me if this setup will work?

Current setup:
2 Displays: 1 television via HDMI and a small monitor via DVI (Monitor quality is not very important, it's mainly for Discord)
MOBO: ASRock 970A-G/3.1
GPU: 4095MB NVIDIA GeForce GTX 960 (ASUStek Computer INC)
CPU: AMD FX-8320E Vishera 32nm Technology

Here's what I'm thinking: I know one GPU needs to be dedicated to the VM. I'm thinking about buying a 1050 ti for that and using the 960 as my main GPU. I don't mind switching sources on my television, so that's no issue. I had previously tried, for proof on concept, using an old EVGA e-GeForce 8600 GT (Yeah, I know it's next to useless, I gutted it from a pc I got for free), however for whatever reason only the 8600 seemed to work in Ubuntu, as well as Win7 (UEFI issue maybe? IDK) In both instances the 960 is detected, and in Ubuntu the display hooked up to my 960 (I had my monitor hooked up to the 8600) was detected, and was receiving a signal, but it was all black. I appear to have been able to move windows and my mouse over to it as well. Installing Nvidia's driver sent me into a log-in loop that google searches were not able to fix. I wiped my HDD, did a fresh install, and same thing - black screen on my TV, installing proprietary drivers sends me into login loop. 

My gut is telling me my Mobo doesn't support this.
Any help would be greatly appreciated. I really want to get this to work. I'm planning on going to school for something in the computer field in about a year and would really like to get much more comfortable with linux, which is hard to do when 80% of my time on my PC HAS to be on windows and it's just annoying to reboot.

Edit: Could power supply be an issue? currently have 680 watts
Edit 2: Definitely feeling power supply could be an issue. Ever since I installed my 2 optical drives 2 sets of my USB ports directly on my MOBO stopped working.

---

### Post by deadflowr on 2017-02-04
*Thread moved to **Virtualisation**.*

---

### Post by pseverino on 2017-02-04
> **deadflowr said:**
> *Thread moved to **Virtualisation**.*
Sorry for the wrong section, mod. Not used to forums tbqh.

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> I've been screwing around with Linux, mainly Ubuntu with Cinnamon installed for a few years now but mainly use windows because I'm a gamer. I recently learned about PCIe Passthrough and am interested, but only have one GPU and want to make sure everything is compatible before I throw money at it. Can someone more knowledgeable than me tell me if this setup will work?

Current setup:
2 Displays: 1 television via HDMI and a small monitor via DVI (Monitor quality is not very important, it's mainly for Discord)
MOBO: ASRock 970A-G/3.1
GPU: 4095MB NVIDIA GeForce GTX 960 (ASUStek Computer INC)
CPU: AMD FX-8320E Vishera 32nm Technology

Here's what I'm thinking: I know one GPU needs to be dedicated to the VM. I'm thinking about buying a 1050 ti for that and using the 960 as my main GPU. I don't mind switching sources on my television, so that's no issue. I had previously tried, for proof on concept, using an old EVGA e-GeForce 8600 GT (Yeah, I know it's next to useless, I gutted it from a pc I got for free), however for whatever reason only the 8600 seemed to work in Ubuntu, as well as Win7 (UEFI issue maybe? IDK) In both instances the 960 is detected, and in Ubuntu the display hooked up to my 960 (I had my monitor hooked up to the 8600) was detected, and was receiving a signal, but it was all black. I appear to have been able to move windows and my mouse over to it as well. Installing Nvidia's driver sent me into a log-in loop that google searches were not able to fix. I wiped my HDD, did a fresh install, and same thing - black screen on my TV, installing proprietary drivers sends me into login loop. 

My gut is telling me my Mobo doesn't support this.
Any help would be greatly appreciated. I really want to get this to work. I'm planning on going to school for something in the computer field in about a year and would really like to get much more comfortable with linux, which is hard to do when 80% of my time on my PC HAS to be on windows and it's just annoying to reboot.

Edit: Could power supply be an issue? currently have 680 watts
Edit 2: Definitely feeling power supply could be an issue. Ever since I installed my 2 optical drives 2 sets of my USB ports directly on my MOBO stopped working.

Your cpu will work, it support iommu.
[http://www.amd.com/en-gb/products/processors/desktop/fx#]("http://www.amd.com/en-gb/products/processors/desktop/fx#")
Looks like your motherboard will work according to page 47 but there are a few tests you can do without doing anything drastic. 
[ftp://europe.asrock.com/Manual/970A-G3.1.pdf]("ftp://europe.asrock.com/Manual/970A-G3.1.pdf")

Do the pre KVM installation checks as explained in the following link after checking if AMD-V is enabled in the bios. The manual says it's on by default but just make sure.
[https://help.ubuntu.com/community/KVM/Installation]("https://help.ubuntu.com/community/KVM/Installation")

If the above comes back positive then you can move on one step.
Edit your grub file and enable IOMMU.
```
sudo nano /etc/default/grub
```
Add the IOMMU line like below
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset amd_iommu=on"
```
Save, exit and reboot.

The first link i posted just checks if iommu is possible but that doesn't mean it's enabled in the kernel so do the following check.
```
dmesg | grep AMD-Vi
```
You want to see something like this.
```
AMD-Vi: Enabling IOMMU at 0000:00:00.2 cap 0x40
AMD-Vi: Lazy IO/TLB flushing enabled
AMD-Vi: Initialized for Passthrough Mode
```

If everything above checks out then in theory passthrough will work but there are still 2 checks to be done to see what workarounds you need to do if any.

Do the following. It will list your pci devices by their iommu groups. Idealy you want to see your gpu and its HDMI sound in their own group. Sometimes if there is a PCI Bridge in the gpu group it's not an issue but any other devices in the same group will then force for you to a) also pass through those devices b) patch the kernel with an ACS override patch that will seperate all devices into their own group.
```
find /sys/kernel/iommu_groups/ -type l
```
Some reading on the subject if your are interested.
[http://vfio.blogspot.co.za/2014/08/iommu-groups-inside-and-out.html]("http://vfio.blogspot.co.za/2014/08/iommu-groups-inside-and-out.html")

The second test is if your gpu has has uefi support but since it's an asus card and 900 series i think it's safe to assume it does. Look it up below to be very sure.
[https://www.techpowerup.com/vgabios/?architecture=NVIDIA&manufacturer=&model=GTX+960&interface=PCI-E&memType=GDDR5&memSize=4096&since=]("https://www.techpowerup.com/vgabios/?architecture=NVIDIA&manufacturer=&model=GTX+960&interface=PCI-E&memType=GDDR5&memSize=4096&since=")

If you don't mind using SSH to set up the system you can go ahead and do a practical test before investing in a second gpu.

---

### Post by efflandt on 2017-02-04
I doubt if power is your issue. I cannot find how much power an 8600 GT uses, but from my PC and 22w difference between my and your CPU and GTX 960 using same 120w as my GTX 1060, I am guessing that your pc uses about 232 watt max + power use of 8600GT. But I don't know if the very old 8600 GT would work with current nvidia proprietary drivers.

---

### Post by ODTech on 2017-02-04
> **efflandt said:**
> I doubt if power is your issue. I cannot find how much power an 8600 GT uses, but from my PC and 22w difference between my and your CPU and GTX 960 using same 120w as my GTX 1060, I am guessing that your pc uses about 232 watt max + power use of 8600GT. But I don't know if the very old 8600 GT would work with current nvidia proprietary drivers.

Those old gpu's don't work in modern systems. The ubuntu installer crashes even during installation nevermind even trying to install proprietary drivers.
Source: I have several old 6000 and 7000 series nvidia cards lying around, none of them works in my new pc.

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> Your cpu will work, it support iommu.
[HTML]http://www.amd.com/en-gb/products/processors/desktop/fx#[/HTML]
Looks like your motherboard will work according to page 47 but there are a few tests you can do without doing anything drastic. 
[HTML]ftp://europe.asrock.com/Manual/970A-G3.1.pdf[/HTML]

Do the pre KVM installation checks as explained in the following link after checking if AMD-V is enabled in the bios. The manual says it's on by default but just make sure.
[HTML]https://help.ubuntu.com/community/KVM/Installation[/HTML]

If the above comes back positive then you can move on one step.
Edit your grub file and enable IOMMU.
```
sudo nano /etc/default/grub
```
Add the IOMMU line like below
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset amd_iommu=on"
```
Save, exit and reboot.

The first link i posted just checks if iommu is possible but that doesn't mean it's enabled in the kernel so do the following check.
```
dmesg | grep AMD-Vi
```
You want to see something like this.
```
AMD-Vi: Enabling IOMMU at 0000:00:00.2 cap 0x40
AMD-Vi: Lazy IO/TLB flushing enabled
AMD-Vi: Initialized for Passthrough Mode
```

If everything above checks out then in theory passthrough will work but there are still 2 checks to be done to see what workarounds you need to do if any.

Do the following. It will list your pci devices by their iommu groups. Idealy you want to see your gpu and its HDMI sound in their own group. Sometimes if there is a PCI Bridge in the gpu group it's not an issue but any other devices in the same group will then force for you to a) also pass through those devices b) patch the kernel with an ACS override patch that will seperate all devices into their own group.
```
find /sys/kernel/iommu_groups/ -type l
```
Some reading on the subject if your are interested.
[HTML]http://vfio.blogspot.co.za/2014/08/iommu-groups-inside-and-out.html[/HTML]

The second test is if your gpu has has uefi support but since it's an asus card and 900 series i think it's safe to assume it does. Look it up below to be very sure.
[HTML]https://www.techpowerup.com/vgabios/?architecture=NVIDIA&manufacturer=&model=GTX+960&interface=PCI-E&memType=GDDR5&memSize=4096&since=[/HTML]

If you don't mind using SSH to set up the system you can go ahead and do a practical test before investing in a second gpu.

Thanks for that! How would one go about testing it via ssh? My MOBO doesn't have an onboard GPU...sorry for newbiness

That makes sense, considering doesn't like windows either.

edit: regarding the power supply

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> Thanks for that! How would one go about testing it via ssh? My MOBO doesn't have an onboard GPU...sorry for newbiness

One of the first steps in setting up passthrough is blacklisting the driver for your passthrough gpu and since you only have one gpu this step will effectively block you from doing anything on the pc as you won't have any display output.

You would have to install openssh-server then from another pc or laptop on your home network connect to your pc with putty. Just make sure you give the pc a fixed ip either by specifying one in network manager or by reserving one in your router dhcp server.
```
sudo apt-get install openssh-server
```
[http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html]("http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html")

Keep in mind via ssh you will only have access to you machine via terminal but it won't matter as the whole setup is usualy done through terminal anyway unless you use virt-manager.
When you have above in place do a test run so you know it's working and once you are comfortable with it post again and i could link you to a good guide or help you through it.

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> One of the first steps in setting up passthrough is blacklisting the driver for your passthrough gpu and since you only have one gpu this step will effectively block you from doing anything on the pc as you won't have any display output.

You would have to install openssh-server then from another pc or laptop on your home network connect to your pc with putty. Just make sure you give the pc a fixed ip either by specifying one in network manager or by reserving one in your router dhcp server.
```
sudo apt-get install openssh-server
```
[http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

Keep in mind via ssh you will only have access to you machine via terminal but it won't matter as the whole setup is usualy done through terminal anyway unless you use virt-manager.
When you have above in place do a test run so you know it's working and once you are comfortable with it post again and i could link you to a good guide or help you through it.

Doing a clean install of vanilla ubuntu 16.04, will get back to you on how it works out.

> **ODTech said:**
> 
Edit your grub file and enable IOMMU.
```
sudo nano /etc/default/grub
```
Add the IOMMU line like below
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset amd_iommu=on"
```
Save, exit and reboot.

The first link i posted just checks if iommu is possible but that doesn't mean it's enabled in the kernel so do the following check.
```
dmesg | grep AMD-Vi
```
You want to see something like this.
```
AMD-Vi: Enabling IOMMU at 0000:00:00.2 cap 0x40
AMD-Vi: Lazy IO/TLB flushing enabled
AMD-Vi: Initialized for Passthrough Mode
```

 I got here. Now my main display doesn't work but my secondary via DVI does, and why I type "dmesg | grep AMD-Vi" I get no return, just another terminal prompt. Tried just grep amd-vi, terminal has been hanging for about 5 minutes,

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> I got here. Now my main display doesn't work but my secondary via DVI does, and why I type "dmesg | grep AMD-Vi" I get no return, just another terminal prompt. Tried just grep amd-vi, terminal has been hanging for about 5 minutes,

Then your motherboard does not support AMD-VI or it has been disabled. Reboot and check your bios. It's been ages since i used AMD so not sure where to look but it shouldn't be too hard to find.

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> Then your motherboard does not support AMD-VI or it has been disabled. Reboot and check your bios. It's been ages since i used AMD so not sure where to look but it shouldn't be too hard to find. Got it. Forgot to save before. Got this: ```
administrator@administrator-desktop:~$ dmesg | grep AMD-Vi[    1.346468] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    1.346469] AMD-Vi: Interrupt remapping enabled
[    1.346579] AMD-Vi: Lazy IO/TLB flushing enabled


/sys/kernel/iommu_groups/0/devices/0000:00:00.0
/sys/kernel/iommu_groups/1/devices/0000:00:04.0
/sys/kernel/iommu_groups/2/devices/0000:00:09.0
/sys/kernel/iommu_groups/3/devices/0000:00:11.0
/sys/kernel/iommu_groups/4/devices/0000:00:12.0
/sys/kernel/iommu_groups/4/devices/0000:00:12.2
/sys/kernel/iommu_groups/5/devices/0000:00:13.0
/sys/kernel/iommu_groups/5/devices/0000:00:13.2
/sys/kernel/iommu_groups/6/devices/0000:00:14.0
/sys/kernel/iommu_groups/7/devices/0000:00:14.1
/sys/kernel/iommu_groups/8/devices/0000:00:14.2
/sys/kernel/iommu_groups/9/devices/0000:00:14.3
/sys/kernel/iommu_groups/10/devices/0000:00:14.4
/sys/kernel/iommu_groups/11/devices/0000:00:14.5
/sys/kernel/iommu_groups/12/devices/0000:00:15.0
/sys/kernel/iommu_groups/12/devices/0000:00:15.2
/sys/kernel/iommu_groups/12/devices/0000:00:15.3
/sys/kernel/iommu_groups/12/devices/0000:05:00.0
/sys/kernel/iommu_groups/12/devices/0000:06:00.0
/sys/kernel/iommu_groups/13/devices/0000:00:16.0
/sys/kernel/iommu_groups/13/devices/0000:00:16.2
/sys/kernel/iommu_groups/14/devices/0000:01:00.0
/sys/kernel/iommu_groups/14/devices/0000:01:00.1
/sys/kernel/iommu_groups/15/devices/0000:02:00.0
```

So it seems my system can work - a 1050 or 1050 ti will work with this, correct?

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> So it seems my system can work - a 1050 or 1050 ti will work with this, correct?

Yes it will work it seems.

Do this command and post the result please. We can use it to cross reference the iommu groups and see if you have ideal grouping or if you have to patch the kernel.

```
lspci -nn
```

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> Yes it will work it seems.

Do this command and post the result please. We can use it to cross reference the iommu groups and see if you have ideal grouping or if you have to patch the kernel.

```
lspci -nn
```

```
administrator@administrator-desktop:~$ lspci -nn00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18]
00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
00:15.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
02:00.0 USB controller [0c03]: ASMedia Technology Inc. Device [1b21:1343]
05:00.0 USB controller [0c03]: Etron Technology, Inc. EJ188/EJ198 USB 3.0 Host Controller [1b6f:7052]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)

```

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> ```
administrator@administrator-desktop:~$ lspci -nn00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18]
00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
00:15.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
02:00.0 USB controller [0c03]: ASMedia Technology Inc. Device [1b21:1343]
05:00.0 USB controller [0c03]: Etron Technology, Inc. EJ188/EJ198 USB 3.0 Host Controller [1b6f:7052]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)

```

That's perfect. Your gpu is alone in group 14 so there shouldn't be any issues. You could try to setup through putty like i descibed earlier to confirm in practice before you get the second gpu but i doubt you will have issues.
I'd say you can go ahead and get the second card.

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> That's perfect. Your gpu is alone in group 14 so there shouldn't be any issues. You could try to setup through putty like i descibed earlier to confirm in practice before you get the second gpu but i doubt you will have issues.
I'd say you can go ahead and get the second card. Just went out and bought a 1050. Love living 2 blocks away from a microcenter. Going to plug it in now and see what happens.

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> Just went out and bought a 1050. Love living 2 blocks away from a microcenter. Going to plug it in now and see what happens.

Nice :lolflag:

I forgot to mention that you will probably need a second keyboard and mouse as the host can't use what the guest is using and vice versa. So you might want to head back to the shop.

[https://forums.linuxmint.com/viewtopic.php?t=212692](https://forums.linuxmint.com/viewtopic.php?t=212692)

Not sure if it is allowed to link to other forums but that's the most complete guide with all the pitfalls of installation. 
You can start from part 2. The first part is already done.

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> Nice :lolflag:

I forgot to mention that you will probably need a second keyboard and mouse as the host can't use what the guest is using and vice versa. So you might want to head back to the shop. I should have something laying around

Mouse and keyboard isn't an issue, however my larger display via HDMI is now not recieving a signal, I haven't even started install qemu

Before I go any further I forgot to mention I now only have one display detected by ubuntu......the small one.

Before I start installing qemu, anyone abe to help me out with that fact that my tv/main display is no longer detected by ubuntu?

My main display is no longer detected by Ubuntu, on either card. It says no signal.

---

### Post by ODTech on 2017-02-04
Did you blaclisted the nouveau driver yet?

> **pseverino said:**
> I should have something laying around

Mouse and keyboard isn't an issue, however my larger display via HDMI is now not recieving a signal, I haven't even started install qemu

Before I go any further I forgot to mention I now only have one display detected by ubuntu......the small one.

Before I start installing qemu, anyone abe to help me out with that fact that my tv/main display is no longer detected by ubuntu?

My main display is no longer detected by Ubuntu, on either card. It says no signal.

The forum went a bit wonky there for a while, some posts seems to have been rolled back.
You mentioned the primary dispaly dying shortly after turning on iommu.

Use dmesg to check for errors
```
dmesg | grep vga
```
or
```
dmesg | grep nouveau
```

Try turning off iommu to see if that is the culprit. If it does fix the HDMI issue then i'd suggest updating the gpu bios, maybe it helps.
```

sudo nano /etc/default/grub
```
remove "amd_iommu=on"
save and exit
```
sudo update-grub
```
reboot

Techpowerup hosts nvflash tools which has a linux version too so grab that and a updated bios from asus. Just make double sure to get the right bios and read the nvlash notes on how to update.
[HTML]https://www.techpowerup.com/download/nvidia-nvflash/[/HTML]

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> Did you blaclisted the nouveau driver yet? Not sure what that means. I tried installing nvidia's driver, forced my pc in low-graphics mode. Ran sudo apt-get purge nivida*, back to the same problem. HDMI works with my 1050 (not 960)  if I boot it with no DVI plugged in, but the resolution is messed up, can't be changed, and shows up as "built in display". I try booting ubuntu 16.04 lts from usb, I get an error that says "noeveua failed to load fecs_inst"

> **ODTech said:**
> The forum went a bit wonky there for a while, some posts seems to have been rolled back.
You mentioned the primary dispaly dying shortly after turning on iommu.

Use dmesg to check for errors
```
dmesg | grep vga
```
or
```
dmesg | grep nouveau
```

Try turning off iommu to see if that is the culprit. If it does fix the HDMI issue then i'd suggest updating the gpu bios, maybe it helps.
```

sudo nano /etc/default/grub
```
remove "amd_iommu=on"
save and exit
```
sudo update-grub
```
reboot

Techpowerup hosts nvflash tools which has a linux version too so grab that and a updated bios from asus. Just make double sure to get the right bios and read the nvlash notes on how to update.
[HTML]https://www.techpowerup.com/download/nvidia-nvflash/[/HTML] ```
 dmesg | grep vga 
``` returns 
```

[    0.351603] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.351605] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.351608] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.351610] vgaarb: loaded
[    0.351611] vgaarb: bridge control possible 0000:02:00.0
[    0.351612] vgaarb: bridge control possible 0000:01:00.0
[   37.572086] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[   37.572195] snd_hda_intel 0000:02:00.1: Handle vga_switcheroo audio client

```

> **ODTech said:**
> Did you blaclisted the nouveau driver yet?



The forum went a bit wonky there for a while, some posts seems to have been rolled back.
You mentioned the primary dispaly dying shortly after turning on iommu.

Use dmesg to check for errors
```
dmesg | grep vga
```
or
```
dmesg | grep nouveau
```

Try turning off iommu to see if that is the culprit. If it does fix the HDMI issue then i'd suggest updating the gpu bios, maybe it helps.
```

sudo nano /etc/default/grub
```
remove "amd_iommu=on"
save and exit
```
sudo update-grub
```
reboot

Techpowerup hosts nvflash tools which has a linux version too so grab that and a updated bios from asus. Just make double sure to get the right bios and read the nvlash notes on how to update.
[HTML]https://www.techpowerup.com/download/nvidia-nvflash/[/HTML] Disbaled iommu in grub and uefi. no difference. Display still shows up as "built in display". Hdmi works with an improper, unchangeable resolution with the same same if I boot with it in my 1050 (not 960) with no dvi anywhere. Dvi shows up as main display from either card.

i downloaded nvflash for linux but there are no notes, just an executable in a zip.....

Seems I can't edit my replies. Anyways, going to try nvflash from my windows installation on my other hdd. In windows, I have my dvi display and 2 hdmis to my tv - I effectively have 3 displays with no issue. Figuring out how to update my bios now.

---

### Post by wildmanne39 on 2017-02-04
The one's you can not edit are probably the duplicate post of your's that are in the jail that were created while the forum was acting up.:)

---

### Post by pseverino on 2017-02-04
I can't find the bios for my 1050 - i can only find the 4gb bios for the 1050 ti , not the 2gb bios for the regular evga 1050. Tried to dump my bios as well via gpu-z and it said bios reading is not supported.

Lol I'm about ready to just give up and give one of you guys ssh permissions - this is a headache. I don't see any way I can update my bios for my gpu. I'm trying something a little weird - installing ubuntu with only my gtx 1050 plugged in, took my 960 out entirely. It's installing, which is way farther than I got from booting from usb before.

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> Seems I can't edit my replies. Anyways, going to try nvflash from my windows installation on my other hdd. In windows, I have my dvi display and 2 hdmis to my tv - I effectively have 3 displays with no issue. Figuring out how to update my bios now.

Ok, i don't think updating the gpu's would have made much difference but i would definitely update the motherboard bios.

AFter that i would install the gpu that is going to be used for the host and take the guest gpu out. Install the nvidia driver for the installed gpu and blacklist the nouveau driver (the default opensource driver for nvidia cards). 
We can also try to get pcistub to claim the guest gpu but it needs to be installed again first to check the device ID. I will put the step below so you can do it afterwards. 

Install the nvidia driver with only the one gpu in the machine then reboot and check which kernel driver has claimed the gpu.
[HTML]lspci -vnn[/HTML]
If it was claimed by NVIDIA then you can continue. If it was claimed by nouveau do not continue, you will end up with no display output at all.

Edit the grub file to blacklist nouveau.. Example of the line that needs editing below.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on modprobe.blacklist=nouveau"
```
Save and exit.
```
sudo update-grub
```
Reboot

[HTML]sudo add-apt-repository ppa:jacob/virtualisation[/HTML]
[HTML]sudo apt-get update && sudo apt-get install qemu-kvm seabios qemu-utils hugepages bridge-utils ovmf[/HTML]
[HTML]sudo nano /etc/modules[/HTML]
Add the following lines to the file
```
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel

```

Save and exit
Shutdown

Put the guest gpu back and do the following to get pci-stub to claim the guest GPU. (This is part of the KVM setup)
```
lspci -nn
```
Write down the device ID for the gpu you are going to pass through and it's audio controller. It's the second last entry in each row. eg. **[10de:1189]**

```
sudo gedit /etc/initramfs-tools/modules
```
Add this line and replacing the device id's your got from lspci with those of your own hardware.
```
pci_stub ids=10de:100c,10de:0e1a
```
Save and exit
```
sudo update-initramfs -u
```
Reboot.

```
lspci -vnn
```
Check if the host gpu is still claimed by NVIDIA and the guest gpu should in theory now be claimed by pci-stub
or
[HTML]dmesg | grep pci-stub[/HTML]
You should see 2 entries as below shich means you are ready to start the VM.
12.429100] pci-stub 0000:02:00.0: claimed by stub

I've half ignored your problem about the display outputs not working because i'm about to go sleep and didn't want to leave you having incase your current reinstall is succesfull. If everything goes well from here you just need a script and a windows iso to start the vm. Maybe someone else can chip and help with a script.Here is an example script, you just need to edit it according to your needs/hardware.

```
#!/bin/bash

configfile=/etc/vfio-pci#.cfg

vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id

}

modprobe vfio-pci

cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=02:00.1,bus=root.1,addr=00.1 \
-drive file=/home/puget/windows#.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/puget/Downloads/Windows.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on

exit 0
```

Source: A much easier guide to follow than the previous ubuntu one.
[HTML]https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/[/HTML]

---

### Post by pseverino on 2017-02-04
> **ODTech said:**
> Ok, i don't think updating the gpu's would have made much difference but i would definitely update the motherboard bios.

AFter that i would install the gpu that is going to be used for the host and take the guest gpu out. Install the nvidia driver for the installed gpu and blacklist the nouveau driver (the default opensource driver for nvidia cards). 
We can also try to get pcistub to claim the guest gpu but it needs to be installed again first to check the device ID. I will put the step below so you can do it afterwards. 

Install the nvidia driver with only the one gpu in the machine then reboot and check which kernel driver has claimed the gpu.
[HTML]lspci -vnn[/HTML]
If it was claimed by NVIDIA then you can continue. If it was claimed by nouveau do not continue, you will end up with no display output at all.

Edit the grub file to blacklist nouveau.. Example of the line that needs editing below.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on modprobe.blacklist=nouveau"
```
Save and exit.
```
sudo update-grub
```
Reboot
[HTML]sudo add-apt-repository ppa:jacob/virtualisation[/HTML]
[HTML]sudo apt-get update && sudo apt-get install qemu-kvm seabios qemu-utils hugepages bridge-utils ovmf[/HTML]
[HTML]sudo nano /etc/modules[/HTML]
Add the following lines to the file
```
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel

```

Save and exit
Shutdown

Put the guest gpu back and do the following to get pci-stub to claim the guest GPU. (This is part of the KVM setup)
```
lspci -nn
```
Write down the device ID for the gpu you are going to pass through and it's audio controller. It's the second last entry in each row. eg. **[10de:1189]**

```
sudo gedit /etc/initramfs-tools/modules
```
Add this line and replacing the device id's your got from lspci with those of your own hardware.
```
pci_stub ids=10de:100c,10de:0e1a
```
Save and exit
```
sudo update-initramfs -u
```
Reboot.

```
lspci -vnn
```
Check if the host gpu is still claimed by NVIDIA and the guest gpu should in theory now be claimed by pci-stub
or
[HTML]dmesg | grep pci-stub[/HTML]
You should see 2 entries as below shich means you are ready to start the VM.
12.429100] pci-stub 0000:02:00.0: claimed by stub

I've half ignored your problem about the display outputs not working because i'm about to go sleep and didn't want to leave you having incase your current reinstall is succesfull. If everything goes well from here you just need a script and a windows iso to start the vm. Maybe someone else can chip and help with a script.Here is an example script, you just need to edit it according to your needs/hardware.

```
#!/bin/bash

configfile=/etc/vfio-pci#.cfg

vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id

}

modprobe vfio-pci

cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=02:00.1,bus=root.1,addr=00.1 \
-drive file=/home/puget/windows#.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/puget/Downloads/Windows.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on

exit 0
```

Source: A much easier guide to follow than the previous ubuntu one.
[HTML]https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/[/HTML]
Motherboard bios was updated earlier this morning via UEFI's built in updating tool. Did a clean install of ubuntu with only my 1050 in, seem to be running into the same issue. According to the "additional drivers" gui, there are no nvidia drivers available - is the 1050 supported by ubuntu? The 2gb evga 1050 - not the ti.

I updated the motherboard bios earlier via UEFI's built in updater. I don't see any nvidia drivers available to download via the gui

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> Motherboard bios was updated earlier this morning via UEFI's built in updating tool. Did a clean install of ubuntu with only my 1050 in, seem to be running into the same issue. According to the "additional drivers" gui, there are no nvidia drivers available - is the 1050 supported by ubuntu? The 2gb evga 1050 - not the ti.

Don't use the repo drivers.

```
sudo add-apt-repository ppa:graphics-drivers/ppa
```
```
sudo apt-get update && sudo apt-get install nvidia-graphics-drivers-378
```

Edit: Fixed a typo

---

### Post by pseverino on 2017-02-04
unable to locate package

---

### Post by ODTech on 2017-02-04
> **pseverino said:**
> unable to locate package

Find the package name with the following.

```
sudo apt-cache search nvidia
```

The package is probably nvidia-378 though.

---

### Post by pseverino on 2017-02-04
lscpi -vnn returned
```
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c81] (rev a1) (prog-if 00 [VGA controller])	Subsystem: eVga.com. Corp. Device [3842:6150]
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at fe000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_378_drm, nvidia_378

```

both monitors are working now. is that what i'm looking for?

> **ODTech said:**
> Find the package name with the following.

```
sudo apt-cache search nvidia
```

The package is probably nvidia-378 though. Got up to the script part without any apparent issues. I apologize, didn't notice you sleep comment before. A massive thank you! You've been a godsend, we ever run into eachother I owe you a beer or a lunch if you don't drink!

Edit: Been looking around and haven't been able to find a solution that jumps out at me - it's only claiming the audio.  No idea how to work around that.

---

### Post by ODTech on 2017-02-05
> **pseverino said:**
> Got up to the script part without any apparent issues. I apologize, didn't notice you sleep comment before. A massive thank you! You've been a godsend, we ever run into eachother I owe you a beer or a lunch if you don't drink!

Edit: Been looking around and haven't been able to find a solution that jumps out at me - it's only claiming the audio.  No idea how to work around that.

That's pretty common. It happens when nouveau doesn't get blacklisted so the card is still being claimed by the kernel and not pci-stub.

When you do **lspci -vnn** do you see both cards being claimed by nvidia or is one nvidia and the other nouveau?

---

### Post by pseverino on 2017-02-05
> **ODTech said:**
> That's pretty common. It happens when nouveau doesn't get blacklisted so the card is still being claimed by the kernel and not pci-stub.

When you do **lspci -vnn** do you see both cards being claimed by nvidia or is one nvidia and the other nouveau? ```
 Last login: Sat Feb  4 23:57:15 2017 from 192.168.1.214main@main-desktop:~$ lspci -vnn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
    Subsystem: ASRock Incorporation RD890 PCI to PCI bridge (external gfx0 port B) [1849:5a14]
    Flags: fast devsel
    Capabilities: <access denied>


00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
    Flags: fast devsel, IRQ 26
    Capabilities: <access denied>


00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fd000000-fe0fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fb000000-fc0fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000b1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fe400000-fe4fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1849:4391]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=16]
    Memory at fc10b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci


00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1849:4397]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fc10a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 USB EHCI Controller [1849:4396]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fc109000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1849:4397]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fc108000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 USB EHCI Controller [1849:4396]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fc107000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
    Subsystem: ASRock Incorporation SBx00 SMBus Controller [1849:4385]
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco


00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 IDE Controller [1849:439c]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4
    I/O ports at 0170 [size=8]
    I/O ports at 0374
    I/O ports at f000 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi


00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: ASRock Incorporation SBx00 Azalia (Intel HDA) [1849:1151]
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fc100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 LPC host controller [1849:439d]
    Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64


00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1849:4399]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fc106000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: fe300000-fe3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:15.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe200000-fe2fffff
    Prefetchable memory behind bridge: 00000000d2100000-00000000d21fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1849:4397]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fc105000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation SB7x0/SB8x0/SB9x0 USB EHCI Controller [1849:4396]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fc104000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
    Flags: fast devsel
    Capabilities: <access denied>


00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
    Flags: fast devsel


00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
    Flags: fast devsel
    Kernel modules: amd64_edac_mod


00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp


00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
    Flags: fast devsel
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power


00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
    Flags: fast devsel


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c81] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:6150]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fe000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_378_drm, nvidia_378


01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fb9] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:6150]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fe080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. GM206 [GeForce GTX 960] [1043:854d]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    [virtual] Expansion ROM at fc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_378_drm, nvidia_378


02:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:854d]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fc080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: pci-stub
    Kernel modules: snd_hda_intel


03:00.0 USB controller [0c03]: ASMedia Technology Inc. Device [1b21:1343] (prog-if 30 [XHCI])
    Subsystem: ASMedia Technology Inc. Device [1b21:1343]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at fe400000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


06:00.0 USB controller [0c03]: Etron Technology, Inc. EJ188/EJ198 USB 3.0 Host Controller [1b6f:7052] (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation EJ188/EJ198 USB 3.0 Host Controller [1849:7052]
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at fe300000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Flags: bus master, fast devsel, latency 0, IRQ 38
    I/O ports at c000 [size=256]
    Memory at fe200000 (64-bit, non-prefetchable) [size=4K]
    Memory at d2100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

pci bus 2 is my guest gpu

---

### Post by ODTech on 2017-02-05
> **pseverino said:**
> 

pci bus 2 is my guest gpu


Try doing this, it will unbind the driver for the card the card.

```
cd /sys/bus/pci/drivers/nvidia
```
```
sudo su
```
```
echo -n 0000:02:00.0 > unbind
```
```
exit
```

Now try running the script again. If you get other errors that's fine, we just want to see if pci-stub can claim the card now.

---

### Post by pseverino on 2017-02-05
what script? I never went past installation of qemu

```
 lspci -vnn
```

still says nvidia claims it

---

### Post by ODTech on 2017-02-05
So you literaly stopped after installing qemu and didn't add the pci ids to initramfs? The stuff i posted on page3.

---

### Post by pseverino on 2017-02-05
oh, yes, yes i did that,

---

### Post by ODTech on 2017-02-05
Ok. Let's see if vfio-pci can claim the passthrough gpu.
Pretty much the same as the pci-stub steps. Use lspci to get the pci id of your gpu and audio.

```
sudo nano /etc/modprobe.d/local.conf
```
Add the following, replacing the id in the example with your own.
```
options vfio-pci ids=10de:13c2,10de:0fbb
```

Go into the followng file again and delete or comment out the pci-stub line.
> sudo nano /etc/initramfs-tools/modules
Save and exit
```
sudo update-initramfs -u
```
Reboot

```
lspci -vnn 

```
You want to see this for the passthrough gpu and audio

```
Kernel driver in use: vfio-pci
```

---

### Post by pseverino on 2017-02-05
> **ODTech said:**
> Ok. Let's see if vfio-pci can claim the passthrough gpu.
Pretty much the same as the pci-stub steps. Use lspci to get the pci id of your gpu and audio.

```
sudo nano /etc/modprobe.d/local.conf
```
Add the following, replacing the id in the example with your own.
```
options vfio-pci ids=10de:13c2,10de:0fbb
```

Go into the followng file again and delete or comment out the pci-stub line.

Save and exit
```
sudo update-initramfs -u
```
Reboot

```
lspci -vnn 

```
You want to see this for the passthrough gpu and audio

```
Kernel driver in use: vfio-pci
``` Audio says vfio-pci, graphics still says nvidia

---

### Post by ODTech on 2017-02-05
OK.

Try the following.
Credit for this go to the linux mint guide i posted earlier in this thread.

```
sudo nano /etc/modprobe.d/local.conf
```
Remove or comment out the options vfio-pci line you added earlier. Add the following line to it instead.
```
install vfio-pci /sbin/vfio-pci-override-vga.sh
```
Save and exit
Create a script file as follows
```
sudo nano /etc/sbin/vfio-pci-override-vga.sh
```
Paste the following in the file.
```
#!/bin/sh

DEVS="0000:02:00.0 0000:02:00.1"

for DEV in $DEVS; do
    echo "vfio-pci" > /sys/bus/pci/devices/$DEV/driver_override
done

modprobe -i vfio-pci
```
Save and exit.
Make the script file executable.
```
sudo chmod u+x /etc/sbin/vfio-pci-override-vga.sh
```

Reboot again and check lspci.

---

### Post by pseverino on 2017-02-05
error: no such file or directory. Tried making it via mkdir, that didnt work either

edit: I found an sbin directory in root

---

### Post by ODTech on 2017-02-05
> **pseverino said:**
> error: no such file or directory. Tried making it via mkdir, that didnt work either

Ah sorry.

Change the path
```
/sbin/vfio-pci-override-vga.sh
```

to

```
/usr/vfio-pci-override-vga.sh
```

Remember to change it inside the modprobe.d file too.

---

### Post by pseverino on 2017-02-05
```
 Last login: Sun Feb  5 17:09:35 2017 from 192.168.1.214main@main-desktop:~$ sudo chmod u+x /usr/vfio-pci-override-vga.sh && sudo reboot 
``` to /usr, not /etc/usr correct?

```
 lspci -vnn 
```
returns
```
 02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. GM206 [GeForce GTX 960] [1043:854d]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at b0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at d000 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_378_drm, nvidia_378


02:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:854d]
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at fc080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

```

pci stub no longer owns audio?

---

### Post by ODTech on 2017-02-05
That is the goal but we're using vfio-pci now or trying to at least.
I might be that the vfio module is being loaded too late.

One more thing i can suggest but after that i'm pretty much stumped too. I'll be in the same boat too soon though, i have a gtx 980 on the way and i have a gtx 670 in atm.

Open  the following file and save the content somewhere then remove it from the file.
[HTML]sudo nano /etc/modules[/HTML]
Remove
```
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel 

```
Save and exit
Now past the content you removed in the following file.
```
sudo nano /etc/initramfs-tools/modules
```
Save and exit.
```
sudo update-initramfs -u
```

Reboot and check lspci once againl

It just occurred to me that in the Driver manager for Linux mint you can specify which driver your gpu uses. I don't know if it's persistent though, meaning with the nouveau driver blacklsted if it will just revert back to nvidia but it's worth a shot.

Open the Driver Manager via the Mint desktop then tell it to use the nouveau driver for your passthrough gpu.

Just make sure that the modprobe blacklist option is still in the grub file.

```
sudo nano /etc/default/grub
```
Example below.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on modprobe.blacklist=nouveau"
```

If it works then the card should be free to be claimed by pci-stub or vfio-pci.

---

### Post by pseverino on 2017-02-05
Did the instructions in your previous post, no difference. I'm not opposed to switching to mint if necessary to make this work. I would have to switch to mint in order to utilize it's driver manager, correct?

Wow I really screwed up that post. Installed manager via
```
 sudo apt-get install gdebi && wget packages.linuxmint.com/pool/main/m/mintdrivers/mintdrivers_1.1.4_all.deb && sudo gdebi mintdrivers_1.1.4_all.deb 
```
ran gui. 960 showed up, 1050 did not. Changed 960 driver to nouveau. Rebooted, back to only dvi. Opened gui, 1050 shows up as unknows with nvidia logo. Attempted to make 1050 use propritary and 960 use nouveau. rebooted. Both screens work. Opened gui, 1050 disappears again and 960 is back on nividia driver. Change 960 to neouveau, ran ```
 lspci -vnn 
``` without rebooting. Still shows up at nvidia.

I'm going to try to find someone with a comparable radeon card to do a swap, that should make it easier.

---

### Post by ODTech on 2017-02-06
Ok.

My GTX980 should be here by Wednesday, i'll let you know what i did to get it working if you havn't made the swop yet. There are people that uses two NVIDIA cards so it has to work.

---

### Post by pseverino on 2017-02-06
> **ODTech said:**
> Ok.

My GTX980 should be here by Wednesday, i'll let you know what i did to get it working if you havn't made the swop yet. There are people that uses two NVIDIA cards so it has to work.

Please do, man. I'll let you know if I find anything as well.

---

### Post by lenisko on 2017-02-10
Hello guys!

Can someone give me a hint, how can I use PCI passthrough with two nvidia cards?
I have gtx1070 and gtx1050, my goal is to use 1050 on host and 1070 on guest.
I was trying many things, but after installing nvidia-367 on host I can't bind 1070 to vfio as it's getting owned by nvidia driver.

Any hints? thanks in advance!

---

### Post by ODTech on 2017-02-10
> **lenisko said:**
> Hello guys!

Can someone give me a hint, how can I use PCI passthrough with two nvidia cards?
I have gtx1070 and gtx1050, my goal is to use 1050 on host and 1070 on guest.
I was trying many things, but after installing nvidia-367 on host I can't bind 1070 to vfio as it's getting owned by nvidia driver.

Any hints? thanks in advance!

I just got my GTX 980 earlier which i'm going to use along with my GTX 670. I'll let you know how i get along.

---

### Post by lenisko on 2017-02-10
@[**[COLOR=#000000]ODTech[/COLOR]**]("https://ubuntuforums.org/member.php?u=586385")
Thanks for reply! I have leaved you private message with question if I can get in contact with you on some IRC network.

About my issues, right now I have updated nvidia driver to nvidia-375 (used ppa), ubuntu is now recognizing 1050 Ti without problems and it's working on it. 
Still my problem is that I can't bind gtx1070 to pci-stub nor vfio-pci.
lspci is showing that device is used by nvidia driver, exception is AUDIO which is binded to vfio. No clues how can I solve that...

---

### Post by wildmanne39 on 2017-02-10
The forum is a community - using PMs for it go against the main principle of communal support.

Please keep support on the forum.

---

### Post by lenisko on 2017-02-10
I don't mind summing things up on forum after thing will get solved but exchanging message after message on forum is waste of time and space, that's why I was asking for IRC contact.

---

### Post by ODTech on 2017-02-11
> **lenisko said:**
> I don't mind summing things up on forum after thing will get solved but exchanging message after message on forum is waste of time and space, that's why I was asking for IRC contact.

Do you have an AMD or Intel system?

I added my new GTX980 to my system and it is persistantly being claimed by pci-stub even after deblacklisting nouveau and installing nvidia-376. The only thing i have to do is patch my kernel with the ACS override patch as both the gpu's now fall in the same iommu group.

---

### Post by lenisko on 2017-02-11
@[**[COLOR=#000000]ODTech[/COLOR]**]("https://ubuntuforums.org/member.php?u=586385")
I'm using Intel i5-4690k Haswell on Z97X-Gaming 5 motherboard. Both GTX 1050 and 1070 are from MSI. I had also patched my kernel with ACS override patch also enabled it. Problem is nvidia driver is claiming both cards. Have you added pci-stub to grub? or initramfs? or better, can you paste content of your:
/etc/modules
/etc/modprobe.d/ - any changes under this directory
/etc/default/grub - might be only GRUB_CMDLINE_LINUX_DEFAULT
/etc/initramfs-tools/ - any changes under this directory
I guess those are most needed changes to claim PCI device.

---

### Post by ODTech on 2017-02-11
I use Linux Mint 18.1 kernel 4.9.9 patched with ACS.
Mint is obviously fully updated.
MSI Z97A Gaming 9 board
Intel i7-4790

This is the primary guide i followed but there is a sticky on the Mint Virtualization forum with loads more info and steps.
[HTML]https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/[/HTML]

Kernel Source
[HTML]https://www.kernel.org/[/HTML]
Kernel Patch found on this thread and below it the actual patch code.
[HTML]https://ubuntuforums.org/showthread.php?t=2329053&page=3&p=13562682#post13562682[/HTML]
```
From 866f4c5de45ae13aa590de0d40819a0c38f3f682 Mon Sep 17 00:00:00 2001
From: Mark Weiman <mark.weiman@markzz.com>
Date: Sun, 23 Oct 2016 12:57:37 -0400
Subject: [PATCH] pci: Enable overrides for missing ACS capabilities (4.8+)

This an updated version of Alex Williamson's patch from:
https://lkml.org/lkml/2013/5/30/513

Original commit message follows:
---
PCIe ACS (Access Control Services) is the PCIe 2.0+ feature that
allows us to control whether transactions are allowed to be redirected
in various subnodes of a PCIe topology.  For instance, if two
endpoints are below a root port or downsteam switch port, the
downstream port may optionally redirect transactions between the
devices, bypassing upstream devices.  The same can happen internally
on multifunction devices.  The transaction may never be visible to the
upstream devices.

One upstream device that we particularly care about is the IOMMU.  If
a redirection occurs in the topology below the IOMMU, then the IOMMU
cannot provide isolation between devices.  This is why the PCIe spec
encourages topologies to include ACS support.  Without it, we have to
assume peer-to-peer DMA within a hierarchy can bypass IOMMU isolation.

Unfortunately, far too many topologies do not support ACS to make this
a steadfast requirement.  Even the latest chipsets from Intel are only
sporadically supporting ACS.  We have trouble getting interconnect
vendors to include the PCIe spec required PCIe capability, let alone
suggested features.

Therefore, we need to add some flexibility.  The pcie_acs_override=
boot option lets users opt-in specific devices or sets of devices to
assume ACS support.  The "downstream" option assumes full ACS support
on root ports and downstream switch ports.  The "multifunction"
option assumes the subset of ACS features available on multifunction
endpoints and upstream switch ports are supported.  The "id:nnnn:nnnn"
option enables ACS support on devices matching the provided vendor
and device IDs, allowing more strategic ACS overrides.  These options
may be combined in any order.  A maximum of 16 id specific overrides
are available.  It's suggested to use the most limited set of options
necessary to avoid completely disabling ACS across the topology.
Note to hardware vendors, we have facilities to permanently quirk
specific devices which enforce isolation but not provide an ACS
capability.  Please contact me to have your devices added and save
your customers the hassle of this boot option.

Signed-off-by: Mark Weiman <mark.weiman@markzz.com>
---
 Documentation/kernel-parameters.txt |   9 ++++
 drivers/pci/quirks.c                | 101 ++++++++++++++++++++++++++++++++++++
 2 files changed, 110 insertions(+)

diff --git a/Documentation/kernel-parameters.txt b/Documentation/kernel-parameters.txt
index a4f4d69..d68cfab 100644
--- a/Documentation/kernel-parameters.txt
+++ b/Documentation/kernel-parameters.txt
@@ -2928,6 +2928,15 @@ bytes respectively. Such letter suffixes can also be entirely omitted.
 		nomsi		[MSI] If the PCI_MSI kernel config parameter is
 				enabled, this kernel boot option can be used to
 				disable the use of MSI interrupts system-wide.
+		pci_acs_override =
+					[PCIE] Override missing PCIe ACS support for:
+				downstream
+					All downstream ports - full ACS capabilities
+				multfunction
+					All multifunction devices - multifunction ACS subset
+				id:nnnn:nnnn
+					Specfic device - full ACS capabilities
+					Specified as vid:did (vendor/device ID) in hex
 		noioapicquirk	[APIC] Disable all boot interrupt quirks.
 				Safety option to keep boot IRQs enabled. This
 				should never be necessary.
diff --git a/drivers/pci/quirks.c b/drivers/pci/quirks.c
index 44e0ff3..32016cb 100644
--- a/drivers/pci/quirks.c
+++ b/drivers/pci/quirks.c
@@ -3487,6 +3487,106 @@ static int __init pci_apply_final_quirks(void)
 
 fs_initcall_sync(pci_apply_final_quirks);
 
+static bool acs_on_downstream;
+static bool acs_on_multifunction;
+
+#define NUM_ACS_IDS 16
+struct acs_on_id {
+	unsigned short vendor;
+	unsigned short device;
+};
+static struct acs_on_id acs_on_ids[NUM_ACS_IDS];
+static u8 max_acs_id;
+
+static __init int pcie_acs_override_setup(char *p)
+{
+	if (!p)
+		return -EINVAL;
+
+	while (*p) {
+		if (!strncmp(p, "downstream", 10))
+			acs_on_downstream = true;
+		if (!strncmp(p, "multifunction", 13))
+			acs_on_multifunction = true;
+		if (!strncmp(p, "id:", 3)) {
+			char opt[5];
+			int ret;
+			long val;
+
+			if (max_acs_id >= NUM_ACS_IDS - 1) {
+				pr_warn("Out of PCIe ACS override slots (%d)\n",
+						NUM_ACS_IDS);
+				goto next;
+			}
+
+			p += 3;
+			snprintf(opt, 5, "%s", p);
+			ret = kstrtol(opt, 16, &val);
+			if (ret) {
+				pr_warn("PCIe ACS ID parse error %d\n", ret);
+				goto next;
+			}
+			acs_on_ids[max_acs_id].vendor = val;
+
+			p += strcspn(p, ":");
+			if (*p != ';') {
+				pr_warn("PCIe ACS invalid ID\n");
+				goto next;
+			}
+
+			p++;
+			snprintf(opt, 5, "%s", p);
+			ret = kstrtol(opt, 16, &val);
+			if (ret) {
+				pr_warn("PCIe ACS ID parse error %d\n", ret);
+				goto next;
+			}
+			acs_on_ids[max_acs_id].device = val;
+			max_acs_id++;
+		}
+next:
+		p += strcspn(p, ",");
+		if (*p == ',')
+			p++;
+	}
+
+	if (acs_on_downstream || acs_on_multifunction || max_acs_id)
+		pr_warn("Warning: PCIe ACS overrides enabled; This may allow non-IOMMU protected peer-to-peer DMA\n");
+
+	return 0;
+}
+early_param("pcie_acs_override", pcie_acs_override_setup);
+
+static int pcie_acs_overrides(struct pci_dev *dev, u16 acs_flags)
+{
+	int i;
+
+	/* Never override ACS for legacy devices or devices with ACS caps */
+	if (!pci_is_pcie(dev) ||
+		pci_find_ext_capability(dev, PCI_EXT_CAP_ID_ACS))
+			return -ENOTTY;
+
+	for (i = 0; i < max_acs_id; i++)
+		if (acs_on_ids[i].vendor == dev->vendor &&
+			acs_on_ids[i].device == dev->device)
+				return 1;
+
+	switch (pci_pcie_type(dev)) {
+	case PCI_EXP_TYPE_DOWNSTREAM:
+	case PCI_EXP_TYPE_ROOT_PORT:
+		if (acs_on_downstream)
+			return 1;
+		break;
+	case PCI_EXP_TYPE_ENDPOINT:
+	case PCI_EXP_TYPE_UPSTREAM:
+	case PCI_EXP_TYPE_LEG_END:
+	case PCI_EXP_TYPE_RC_END:
+		if (acs_on_multifunction && dev->multifunction)
+			return 1;
+	}
+
+	return -ENOTTY;
+}
 /*
  * Followings are device-specific reset methods which can be used to
  * reset a single function if other methods (e.g. FLR, PM D0->D3) are
@@ -4160,6 +4260,7 @@ static const struct pci_dev_acs_enabled {
 	{ 0x10df, 0x720, pci_quirk_mf_endpoint_acs }, /* Emulex Skyhawk-R */
 	/* Cavium ThunderX */
 	{ PCI_VENDOR_ID_CAVIUM, PCI_ANY_ID, pci_quirk_cavium_acs },
+	{ PCI_ANY_ID, PCI_ANY_ID, pcie_acs_overrides },
 	{ 0 }
 };
 
-- 
2.10.1
```

/etc/modules
```
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel
```
/etc/modprobe.d/blacklist.conf
I originaly blacklised nouveau here when i was using Intel graphics for the host but later switched to blacklisting with grub by adding "modprobe.blacklist=nouveau"

/etc/default/grub 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_acs_override=downstream intel_iommu=on"
```

/etc/initramfs-tools/modules
The first two devices is a sata and usb controller which i can actualy remove as they are only claimed by pci stub then vfio when the script is executed.
```
pci_stub ids=1b4b:9130,1912:0015,10de:13c0,10de:0fbb
```

My script
```
#!/bin/bash

configfile=/etc/vfio-pci1.cfg

vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id

}

modprobe vfio-pci

cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done

cp /usr/share/ovmf/OVMF.fd /tmp/my_vars.fd

qemu-system-x86_64 \
  -machine type=q35,accel=kvm \
  -cpu host,kvm=off \
  -smp 4,sockets=1,cores=2,threads=2 \
  -enable-kvm \
  -m 10G \
  -mem-path /run/hugepages/kvm \
  -mem-prealloc \
  -balloon none \
  -rtc clock=host,base=localtime \
  -vga none \
  -nographic \
  -serial none \
  -parallel none \
  -device vfio-pci,host=02:00.0,multifunction=on \
  -device vfio-pci,host=02:00.1 \
  -device vfio-pci,host=09:00.0 \
  -device vfio-pci,host=0c:00.0 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/ovmf/OVMF.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -boot order=dc

   exit 0
fi


```

---

### Post by lenisko on 2017-02-11
Here's mine output from few things

Dmesg output: [http://ix.io/1T7s](http://ix.io/1T7s)

```
$ lspci -nnk
...
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b81] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3302]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10f0] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3302]
    Kernel driver in use: pci-stub
    Kernel modules: snd_hda_intel
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c82] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3351]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
02:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fb9] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3351]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
...
```

```
$ cat /etc/modules
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel
```

```
$ cat /etc/initramfs-tools/modules
pci_stub ids=10de:1b81,10de:10f0
```

```
$ cat /etc/default/grub
...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_acs_override=downstream intel_iommu=on"
...
```

As you can see, 1070 is still owned by NVIDIA driver.

I was trying to run your script by hand it got stuck at last command, as I was able to see in dmesg output > [   98.050618] NVRM: Attempting to remove minor device 0 with non-zero usage count!

```
# dev=0000:01:00.0
# vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
# device=$(cat /sys/bus/pci/devices/$dev/device)
# echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
_
```

So things without answers, why nvidia is claiming this device before pci_stub?

---

### Post by ODTech on 2017-02-11
> **lenisko said:**
> Here's mine output from few things

Dmesg output: [http://ix.io/1T7s](http://ix.io/1T7s)

```
$ lspci -nnk
...
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b81] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3302]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10f0] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3302]
    Kernel driver in use: pci-stub
    Kernel modules: snd_hda_intel
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c82] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3351]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
02:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fb9] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3351]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
...
```

```
$ cat /etc/modules
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel
```

```
$ cat /etc/initramfs-tools/modules
pci_stub ids=10de:1b81,10de:10f0
```

```
$ cat /etc/default/grub
...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_acs_override=downstream intel_iommu=on"
...
```

As you can see, 1070 is still owned by NVIDIA driver.

I was trying to run your script by hand it got stuck at last command, as I was able to see in dmesg output 

```
# dev=0000:01:00.0
# vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
# device=$(cat /sys/bus/pci/devices/$dev/device)
# echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
_
```

So things without answers, why nvidia is claiming this device before pci_stub?

From what i read and if i recall correctly the kernel tries to apply possible drivers to a new device in a specific order. If you started the process with nvidia already installed i wonder if the first driver it try is maybe nvidia then nouveau and pci-stub last because it was installed last. My passthrough gpu at the moment is gtx 980 on adress 02.00.0 but before that the passthrough device was gtx670 which was also on adress 02.00.0. When i installed nvidia-378 the card at 02.00.0 was already claimed by pci-stub.

I don't know if i am right, i tried googling how to change the order in which the kernel tries to apply drivers but i didn't come up with anything. Maybe someone more knowledgeable can chip in?

Try the following
Uninstall nvidia and remove the gpu that will be used by the host.
Set your bios to boot from the onboard intel graphics.
Start up with intel graphics
Blacklist nouveau.
Now get passthrough working in the guest vm with your passthrough gpu.
Once it's working put the host gpu back but don't switch your bios back to pci-e boot yet because you still have nouveau blacklisted.
Install nvidia and check if the passthrough gpu is still being claimed by pci-stub and the primary gpu by nvidia.
If it works then just switch your startup graphics to pci-e.

Hope it helps.

---

### Post by lenisko on 2017-02-11
@[**[COLOR=#000000]ODTech[/COLOR]**]("https://ubuntuforums.org/member.php?u=586385")
Sadly no luck there.
I wasn't able to find solution to load vfio at earlier stage than nvidia module looks like that is my problem in there.

---

### Post by ODTech on 2017-02-12
> **lenisko said:**
> @[**[COLOR=#000000]ODTech[/COLOR]**]("https://ubuntuforums.org/member.php?u=586385")
Sadly no luck there.
I wasn't able to find solution to load vfio at earlier stage than nvidia module looks like that is my problem in there.

Yes that's what it comes down to.
Grub can run scripts too, i briefly looked at it in anticipation of having the issue you have because i think that's about as early as you can get.
[HTML]https://help.ubuntu.com/community/Grub2/Setup[/HTML]

---

### Post by lenisko on 2017-02-13
Neither worked for me, I asked maintainer of nvidia ppa and it looks like nvidia is injecting modules in very early stage.

I have switched to arch linux, everything is working just fine out of the box after adding modules in right places.
For now I have to figure out how get rid of Error 43.

---

### Post by heiko_s on 2017-02-14
I understand that the graphics card on 2:00.0 does not bind to the vfio-pci driver, the audio part at 2:00.1 does. I would check the following:

1. In the BIOS, make sure the correct graphics device is selected for boot: CPU internal / GPU1 / GPU2 (if available). (This is just a precaution.) It should be CPU Internal, or GPU1 (if you have two GPU).

2. Load the required modules in /etc/initramfs-tools/modules. Add the following to the file:
```
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
vhost-net
```
This should take care that the required modules - particularly vfio-pci - are included in the ramdisk and loaded at the earliest possible stage during boot.

3. Run
```
sudo update-initramfs -u
```
to create the new initramfs with the modules added above.

4. Edit /etc/default/grub and add to the following to your "GRUB_CMDLINE_LINUX_DEFAULT="quiet intel_iommu=on" line:
```
modprobe.blacklist=nouveau
```
The above only works with Nvidia cards!

5. Run
```
sudo update-grub
```
to update grub.

6. Open/create /etc/modprobe.d/local.conf and insert on a single line:
```
options vfio-pci ids=10de:13c2,10de:0fbb
```
where the vfio-pci ids are the ones of the graphics card you want to pass through: 10de = Nvidia, 13c2 = change to the id of your card, 0fbb = the audio part, which is probably the same on your card - if not, change!

The PCI IDs are determined using:
```
lspci | grep VGA
```
then taking the relevant PCI bus number, enter:
```
lspci -nn | grep 02:00.
```
You should get the PCI IDs for the specified bus number.

Note: With my CPU / motherboard bus no. 1:00.x specifies the first GPU card/slot, and 2.00.x the second GPU card/slot. My CPU has no internal graphics.

7. Open the /etc/modules file and see that there are no modules from step 2 listed. The /etc/modules file is an alternative to the /etc/initramfs-tools/modules but since /etc/modules is not part of the initramfs it's loaded at a later time.

**Note: Most tutorials will tell you to put the kernel modules (step 2) in this file. Obviously it works for many (most?).**

8. Now cross your fingers, reboot, and check:
```
lspci -k | grep -i -A 3 vga
```
You should see something like:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF106GL [Quadro 2000] (rev a1)
	Subsystem: NVIDIA Corporation GF106GL [Quadro 2000]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm
--
02:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd GM204 [GeForce GTX 970]
	Kernel driver in use: vfio-pci
	Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm

```
The second GPU on 02:00.0 is now bound to vfio-pci.

9. If you don't get the results you were hoping for, **don't despair!**

When you installed Linux, you may have installed the proprietary Nvidia driver _before_ you let vfio-pci grab the second GPU. Or something got messed up later. It happens.

Under Ubuntu, open "Additional Drivers" - see for example [http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers]("http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers") for more information.

You should see both your graphics cards listed in the GUI, together with the available drivers. For the card you want to pass through, select the **Nouveau** driver and press "Apply Changes". Exit the application.

10. Reboot once more and check again (see step 8). If all went well you should now be seeing the vfio-pci driver taking care of the graphics card under 02:00.0.

Explanation:
When installing the Nvidia driver, it will look for all Nvidia graphics cards and compile specific kernel module(s) for them. So when the PC boots, it will also load the Nvidia kernel modules at a very early boot stage.

In step 9 we told Linux to not use the proprietary Nvidia driver for graphics card at 02:00.0, but instead the opensource Nouveau driver. However, the nouveau driver has been blacklisted in step 4, preventing the opensource driver from attaching to the GPU and leaving the stage to our beloved vfio-pci driver.

Let us know if it works.


A note on choosing a Linux distribution: It's a personal decision where each one must decide how much he/she is willing to invest in making things work. I myself choose the distribution I like and make it work the way I want, even if I sometimes spend a lot of time to figure it out. Others may choose a distribution that works, even though it wasn't the first choice. In the end, what makes or breaks a distribution is not the least its support. As long as people like ODTech, redger, and many many others are on the forum here and helping out, Ubuntu and its derivatives are in a good position.

---

### Post by KillerKelvUK on 2017-02-14
So I saw that the nouveau modules could be fended off by creating a .conf file under /etc/modprobe.d/ with something like the following used...

```

# Locate this file in /etc/modprobe.d/ and update-initramfs -u


options kvm_intel nested=1
options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio-pci ids=xxxx:xxxx
softdep nouveau pre: vfio-pci

```

however if using the nvidia modules in replace of nouveau as per your post #56 ([https://ubuntuforums.org/showthread.php?t=2351497&p=13607004#post13607004](https://ubuntuforums.org/showthread.php?t=2351497&p=13607004#post13607004)) they load too early and so you need to either remove them or blacklist them via a kernal append which is as per heiko_s's post.

---

### Post by heiko_s on 2017-02-14
> **KillerKelvUK said:**
> So I saw that the nouveau modules could be fended off by creating a .conf file under /etc/modprobe.d/ with something like the following used...

```
# Locate this file in /etc/modprobe.d/ and update-initramfs -u


options kvm_intel nested=1
options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
options vfio-pci ids=xxxx:xxxx
softdep nouveau pre: vfio-pci
```

however if using the nvidia modules in replace of nouveau as per your post #56 ([https://ubuntuforums.org/showthread.php?t=2351497&p=13607004#post13607004](https://ubuntuforums.org/showthread.php?t=2351497&p=13607004#post13607004)) they load too early and so you need to either remove them or blacklist them via a kernal append which is as per heiko_s's post.

softdep nouveau pre: vfio-pci  -- this is new to me. Thanks!
I saw that unless nouveau is the culprit, nouveau should be replaced with the name of the Nvidia module that binds to the graphics card.

The other options (except the obvious vfio-pci ids=...) are:

options kvm_intel nested=1
allows nested VMs. Depends on what you want to do with the VM. If in doubt, use it.

options kvm ignore_msrs=1
ignore unimplemented MSRs instead of returning an error value. Is needed to run Passmark. Some games may crash without this option. I'd say good to have.

options allow_unsafe_assigned_interrupts=1
before you use this option, and after you tried running the VM and failed, run
```
dmesg | grep VFIO
```
and look for:
```
vfio_iommu_type1_attach_group: No interrupt remapping support. Use the module param "allow_unsafe_interrupts" to enable VFIO IOMMU support on this platform
```
Use this option only if needed.

---

### Post by heiko_s on 2017-02-14
> **lenisko said:**
> Neither worked for me, I asked maintainer of nvidia ppa and it looks like nvidia is injecting modules in very early stage.

I have switched to arch linux, everything is working just fine out of the box after adding modules in right places.
For now I have to figure out how get rid of Error 43.

You need to add the following option to your qemu-system-x86_64 command:

  -cpu host,**kvm=off** \

Explanation:
Once you install the Nvidia driver under Windows, the driver will check your graphics card model and if you are running a VM. If your graphics card is NOT one of the outrageously expensive Quadro-2000 or higher-end **professional** Nvidia graphics cards, the Nvidia driver will hit a "bug" and refuse to execute, reporting error 43.
kvm=off fools the Nvidia driver into thinking that it's not running in a VM, by turning of some hypervisor extensions. In theory this can have a negative influence on performance, but in practice I'm not convinced that you'll notice a difference.

More on that [here]("https://forums.linuxmint.com/viewtopic.php?f=231&t=229122"). **Note: I do NOT encourage patching the Nvidia driver.**

---

