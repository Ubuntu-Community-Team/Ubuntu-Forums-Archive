---
title: "installing server onto 2gb flash drive"
date: 2010-08-30
forum: Server Platforms
---

### Post by kustomjs on 2010-08-30
Hey Guys
I just wanted to know if anybody got any server versions installed onto a flash drive that is 2gb and if you did can you tell me how to do that because I have been trying to do this on an VXL Itona TC3533-LI thin client for the past 2 nights and cant get any where with it. I have tried to format the flash drive in FAT32 then try to install it by ubuntu server live cd and still no go.

---

### Post by oldfred on 2010-08-30
Are you trying to do a full install? Or copy the ISO to the flash for installation of the server.

If full install (does it even fit?) you need a linux format ext2 for flash or ext4 without journal.

If you are wanting an ISO just install grub2 to the FAT formated flash drive and copy the ISO to the flash drive. Modify grub's grub.cfg to loopmount the ISO.

---

### Post by BkkBonanza on 2010-08-30
I've done this and used it for my mini-itx based router. But I haven't done it for a thin client and don't know how that may change things.

The way I did it (which is certainly not the only way, but it worked) was:

On my desktop I chose System, Administration, Startup Disk Creator and used that to create a "Live" System disk on a flash drive. 

Then I placed that on my target PC and booted on it.

Then I inserted a second (final target) flash drive into the target PC and used the Live boot to install onto that flash drive. I used a 4GB drive and I'm not sure if 2GB is enough for a default install but it should work with options like "minimal install".

After that I removed the Live flash drive, and set the BIOS to boot from the other one. Sometimes that happens automatically anyway but you do need to be sure the BIOS supports booting from USB Mass Storage Devices. Older ones usually don't.

If you have a CD drive on the target PC then obviously there would be no need for a Live flash drive.

Note, initially I created a Virtualbox machine on my desktop containing the Live version and used that to install to a flash drive but I found due to hardware differences between the VM and the target PC that this didn't boot well when moved over to the target PC.

---

### Post by kustomjs on 2010-08-30
im trying to do a full system install for the server.

---

### Post by snowpine on 2010-08-30
> **kustomjs said:**
> Hey Guys
I just wanted to know if anybody got any server versions installed onto a flash drive that is 2gb and if you did can you tell me how to do that because I have been trying to do this on an VXL Itona TC3533-LI thin client for the past 2 nights and cant get any where with it. I have tried to format the flash drive in FAT32 then try to install it by ubuntu server live cd and still no go.

Here are instructions for installing Ubuntu Server; 2gb should be sufficient (default server install is under 1gb):

[https://help.ubuntu.com/10.04/serverguide/C/installation.html](https://help.ubuntu.com/10.04/serverguide/C/installation.html)

That it is a flash drive is irrelevant; Ubuntu does not care whether the drive is interior or exterior to the computer.

I suspect the problem in your case is one of two things:

1. FAT32 is not a Linux filesystem; ext4 with the 'noatime' option is my recommendation.
2. Your thin client BIOS may not support what you are trying to do.

---

### Post by kustomjs on 2010-08-30
the thin client gives me a option in bios to boot from usb-fdd,usb-zip,usb-hdd.

---

### Post by BkkBonanza on 2010-08-30
> **kustomjs said:**
> the thin client gives me a option in bios to boot from usb-fdd,usb-zip,usb-hdd.

For this purpose, normal hd partition, you need to choose usb-hdd. The other ones won't work here.

---

### Post by kustomjs on 2010-08-30
does any flash drive works?

---

### Post by BkkBonanza on 2010-08-30
In general, yes. But there could be some weird product out there that wouldn't - having not tried them all. But, yes, usually flash drives are pretty generic. I've heard of reports in some cases where some manufacturers have problems in some devices but haven't had that problem myself.

When you try to boot on your flash drive what messages do you see? If no message then likely still BIOS config or hardware. If "Invalid operating system" or something to that effect then it's related to no/invalid MBR (master boot record) or OS presence. If it gets as far as Grub/Linux messages then it's problems in Linux config. Using a Live CD image (CD or flash) that shouldn't occur.

---

### Post by kustomjs on 2010-08-30
well when I tried a 8GB sandisk after it was installed it would go post screen saying verifying DMI pool data then just sets there and do noting. I am going to try 2GB again to see if I can get it to install correct.

---

### Post by BkkBonanza on 2010-08-30
Make sure the boot order is set correctly in the BIOS. If a non-existant HD is still set as **first** boot device then even if a USB HD is bootable it will wait/timeout on the non-existant HD.

---

### Post by kustomjs on 2010-08-30
I am going to try to install 10.04 by universal usb installer on my 8GB sandisk is there anything else I need to do with that besides make sure the bios set as usb-hdd as first.

---

### Post by TwoEars on 2010-08-30
I really don't recommend using a flash drive for this. You should be using an external hard drive with a separate power supply, if anything.

---

### Post by BkkBonanza on 2010-08-30
I don't see a problem with a flash disk for this. It's been working great for me on my router and a thin client system is similar in that the flash disk acts most as a read only system disk, with user data usually kept on the network drives / "the cloud".

It's low power, reliable, and fast (if you have a decent flash disk). The current wear leveling firmware is advanced enough that flash drives aren't going to wear out under any typical usage. I have had perfectly fine results in my experience.

---

### Post by BkkBonanza on 2010-08-30
> **kustomjs said:**
> I am going to try to install 10.04 by universal usb installer on my 8GB sandisk is there anything else I need to do with that besides make sure the bios set as usb-hdd as first.

Unless I'm forgetting something, that is all that's required in the BIOS. They do vary somewhat so poke around and make sure there's nothing else that seems related.

I'm not sure what you mean by "universal usb installer" though. I just installed normally as if to a hard disk and it works great. For that to work the flash disk has to show as a normal /dev/sdxx device.

---

### Post by kustomjs on 2010-08-30
well that universal usb installer didnt work so I am thinking its more something with BIOS and the post screen shows usb 1.1 so I think that is the reason why its not working correctly so I been trying to figure out how to flash that bios so its up to date. Also the post screen shows my cruiser as usb storage device.

---

### Post by oldfred on 2010-08-31
Even though my BIOS says I can boot from many USB devices including USB-HDD, that did not work with my flash drive. But it does work when I choose which hard drive to boot, the flash drive is listed among the SATA drives.

---

