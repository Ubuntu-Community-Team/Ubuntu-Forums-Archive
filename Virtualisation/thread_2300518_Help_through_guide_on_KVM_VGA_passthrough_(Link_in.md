---
title: "Help through guide on KVM VGA passthrough (Link inside)"
date: 2015-10-26
forum: Virtualisation
---

### Post by LastHylian on 2015-10-26
```
Ubuntu 15.04

$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 720] (rev a1)

$ lspci -nn | grep NVIDIA 
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK208 [GeForce GT 720] [10de:1288] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GK208 HDMI/DP Audio Controller [10de:0e0f] (rev a1)

$dmidecode
Base Board Information
	Manufacturer: MSI
	Product Name: H61M-P31 (G3) (MS-7788)

$lscpu
Model name:            Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
```


[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

Following the guide mentioned above, I'm able to successfully reach Step 2: Blacklist the NVIDIA Cards. However, after editing the **/etc/initramfs-tools/modules** file to contain the IDs (10de:1288, 10de:0e0f), then executing **update-initramfs -u**, and finally rebooting, LightDM fails to load with messages stating "No discrete VGA device found". I was not able to drop back to virtual terminal either (Ctrl+Alt+F1) and had to use recovery mode to remove the lines from the file. I have verified that the intergrated graphics from my CPU are indeed working, just not when I have the NVIDIA card blacklisted. I haven't come across anyone having this issue while attempting to setup VGA passthrough and only found articles saying this is likely a bug. 

Can anyone confirm if this is indeed a bug or if I am missing something in the configuration process?

[B]**EDIT**
After reading around some more, another user suggested removing all NVIDIA related packages before proceeding. Run "sudo apt-get remove --purge nvidia*", then reboot.[/B]

---

