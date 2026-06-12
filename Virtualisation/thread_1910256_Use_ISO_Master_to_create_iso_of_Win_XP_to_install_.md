---
title: "Use ISO Master to create iso of Win XP to install in a VirtualBox?"
date: 2012-01-16
forum: Virtualisation
---

### Post by Ms. Daisy on 2012-01-16
Is anyone familiar with ISO Master? Apparently I'm a blockhead and can't  get my two ISOs to combine into one ISO.  I've spent an hour googling  tutorials and this forum, learned a little but not enough to solve the  problem.

Specifically, I'm trying to create one bootable image for Windows XP  from my restore & OS CDs.  I replaced the hard drive on my XP  computer and installed Ubuntu.  Now I want to put XP back on another  machine, but this time in a virtualbox instead of on the hard disk.  So  it's a legit install and legit CDs. I know the CDs are good because I  recently installed XP on the hard drive (but subsequently wiped it out  when I replaced it with Ubuntu).

I created an ISO of each of the CDs. I'm able to add the contents of one ISO image to ISO Master.  But I  can't add the contents of the second one- it only allows me to add the  entire second ISO as one file.  I gave that a shot and it won't boot.

I'm open to unrelated alternatives. How can I install XP on the virtualbox when I have two install CDs?

---

### Post by imachavel on 2012-01-16
oh yeah, I never got this one either. I almost downloaded 6 separate .iso files of lion to try and install on a virtual machine :lolflag:

but why can't you select the file location to install those .isos into the virtual machine instead of from a disk or external drive? Same problem? I see what you mean:

[http://www.magiciso.com/tutorials/miso-createmultibootcd.htm](http://www.magiciso.com/tutorials/miso-createmultibootcd.htm)

this isn't extremely descriptive, but then I haven't looked super extensively for the answer to this either. It seems very possible though. Do you have a valid activation key?

---

### Post by Custom Cowboy on 2012-01-16
It should be possible to create 2 cd drives in the virtual mechine and have the iso images loaded onto each at bootup, the boot order will be able to be set in the virtual mechine. It will need to boot on the OS iso

---

### Post by Ms. Daisy on 2012-01-16
> **Custom Cowboy said:**
> It should be possible to create 2 cd drives in the virtual mechine and have the iso images loaded onto each at bootup, the boot order will be able to be set in the virtual mechine. It will need to boot on the OS iso
OMG- I never thought of that. I'll give it a try tomorrow.

---

### Post by japzone on 2012-01-17
You can mount as many ISOs in VB as you want, you just need to make a Drive for each ISO. No need to do something complicated like merging ISOs.

---

### Post by carl4926 on 2012-01-17
k3b can copy cd to image only

And FYI, don't know if this applies
But you can't use OEM CD's in Virtual Machines

---

### Post by japzone on 2012-01-17
If you hadn't already Nuked your XP install I would have suggested you use [**VMware vCenter Converter™**]("http://www.vmware.com/products/converter/") to convert your PC install into a VMDK that VirtualBox can boot from.

---

### Post by Ms. Daisy on 2012-01-17
> **japzone said:**
> If you hadn't already Nuked your XP install I would have suggested you use [**VMware vCenter Converter™**]("http://www.vmware.com/products/converter/") to convert your PC install into a VMDK that VirtualBox can boot from.
I can always reinstall it, convert it, then nuke it.  I'll give this a try if mounting 2 CDs doesn't work in virtual box.  Thanks.

---

### Post by xyzzyman on 2012-01-17
Your XP restore discs are possibly locked to the other computer (Some brands checked the BIOS, etc...) so they may refuse to install.

---

### Post by Ms. Daisy on 2012-01-17
> **xyzzyman said:**
> Your XP restore discs are possibly locked to the other computer (Some brands checked the BIOS, etc...) so they may refuse to install.
That's exactly what happened.  At least I figured that out by mounting two cd drives in the virtual box instead of going to all the trouble of creating one iso image.

---

### Post by bluexrider on 2012-01-17
> **carl4926 said:**
> k3b can copy cd to image only

And FYI, don't know if this applies
But you can't use OEM CD's in Virtual Machines

I hate to burst your bubble. My XP virtualbox is running made from a DELL OEM CD.

---

### Post by xyzzyman on 2012-01-17
> **bluexrider said:**
> I hate to burst your bubble. My XP virtualbox is running made from a DELL OEM CD.

Dell XP CD's were usually install CD's and not recovery cd's that checked the BIOS. Your license though doesn't allow for it though so technically we can't talk about your VB install on this forum. :)

---

### Post by bluexrider on 2012-01-17
> **xyzzyman said:**
> Dell XP CD's were usually install CD's and not recovery cd's that checked the BIOS. Your license though doesn't allow for it though so technically we can't talk about your VB install on this forum. :)
Recovery CD is a different story. Yes I realise that. Got the DELL box running on 10.04 anyway.

---

### Post by Ms. Daisy on 2012-01-17
Just to be clear in my particular case, I read the EULA for my version which is Windows XP Professional SP2. There is no restriction or exclusion from virtualization.

---

### Post by japzone on 2012-01-18
> **Ms. Daisy said:**
> I can always reinstall it, convert it, then nuke it.  I'll give this a try if mounting 2 CDs doesn't work in virtual box.  Thanks.
Yeah that's probably best if your OEM disc won't install in VB.

---

### Post by xyzzyman on 2012-01-18
Get a regular XP ISO, install it, and use the XP serial # on your case to activate it? What's the chances you've ever actually used that serial #?

---

