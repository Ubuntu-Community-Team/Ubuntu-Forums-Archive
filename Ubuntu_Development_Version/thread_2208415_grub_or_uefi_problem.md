---
title: "grub or uefi problem?"
date: 2014-02-28
forum: Ubuntu Development Version
---

### Post by yCAxYRA on 2014-02-28
i just installed kubuntu and i see that drive as two bootable devices. Any ideas why that is?

---

### Post by ventrical on 2014-02-28
> **yCAxYRA said:**
> i just installed kubuntu and i see that drive as two bootable devices. Any ideas why that is?


 I think perhaps because it is set in Boot Override and you are getting a dup from BIOS. The other idea is that it could be a partioner bug. Try to boot, then:

```


sudo update-grub


```

then restart and see whats up.

---

### Post by yCAxYRA on 2014-02-28
No luck with update-grub. I cant see how boot override could affect it? I thought that maybe it has something to do with prior windows 7 install, some residue in GPT? If thats ridiculous then dont laugh :) .

---

### Post by oldfred on 2014-02-28
Is one grub and the other shim? 
Or perhaps Boot?

This should show details.
 # from live CD and use efibootmgr
sudo efibootmgr -v

 
UEFI reads .efi files in the efi folder and adds entries into NVRAM. Even if you remove from efi partition an old install you may have to manually delete frm NVRAM. 
And Windows may complicated it more as it also caches NVRAM entries in BCD and may resync again.

What model Samsung?
And it shows Ubuntu in UEFI without issues? Some vendors modify UEFI to only show/boot Windows.

---

### Post by grahammechanical on 2014-02-28
Did you use a USB memory stick to install Kubuntu from?

On my old BIOS system USB memory sticks with a Ubuntu installed get listed as external USB drives. I have not checked this recently, but if my memory is any good, I think that the designation remains in the BIOS configuration because I saved the set up that I changed in order to set the boot priority.

I have no experience of UEFI so I will not offer a suggestion. But I doubt that it is 14.04 specific.

Regards.

---

### Post by yCAxYRA on 2014-03-01
> **oldfred said:**
> Is one grub and the other shim? 
Or perhaps Boot?

This should show details.
 # from live CD and use efibootmgr
sudo efibootmgr -v


 
Yes, one is grubx64.efi and other shimx64.efi . So in theory i could get rid shim if i dont care about signing grub but grubx64 must be there? Or in anotherwords its not a bug, its feature? :D
As for external hdd, its Samsung D3 station 2TB and it works very well except for special features that are windows only. I dont even grasp the difference between usb3 hdd and internal hdd in terms of speed. Although ssd where kubuntu is, there i can feel the DIFFERENCE compared to ordinary hdd. :)

---

### Post by oldfred on 2014-03-01
I thought I saw somewhere that they were only going to use shim for both secure and non-secure boot. 
Do both work with your configuration?

I was going to build new computer from my Desktop 2006 vintage Core Duo with several updates but added a SSD two years ago. I since have had trouble justifying new build as it runs so well for what I do.
But old laptop is really short of RAM, cannot really upgrade. On user posted he buys better laptop with hard drive, immediately removes Windows drive and puts in new SSD with Ubuntu. That seems like what I will do soon.

---

