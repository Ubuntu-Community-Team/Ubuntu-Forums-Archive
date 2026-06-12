---
title: "Vmware server usb crash"
date: 2008-03-24
forum: Virtualisation
---

### Post by enrycone on 2008-03-24
Hi, I'm using Vmware Server in Kubuntu.

When I try to mount USB devices and I enable on my virtual machine (win xp), it  crash in a few seconds.

Anyone know if is it a common Vmware bug?

Thanks in advance.

Enrycone

---

### Post by fjgaude on 2008-03-24
It certainly is not a bug with folks who are using gnome, Ubuntu. VMware is solid with USBs and the like.

---

### Post by lukemack on 2008-07-10
I'm getting this problem and I'm using Gnome on Hardy so I'm guessing the previous poster is wrong.

---

### Post by jkreitz on 2008-07-10
I'm having the same issue too with the USB flash drive crashing my XP VM. I've got Ubuntu 8.04 and am using VMware 1.0.6. I added this to \etc\fstab get VMware to recognize my flash drive:

# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

But plugging in the drive will give XP a BSOD.

---

### Post by fjgaude on 2008-07-10
> **lukemack said:**
> I'm getting this problem and I'm using Gnome on Hardy so I'm guessing the previous poster is wrong.

I have no issues running files from a USB in VM WinXP to Ubuntu and vice versa using Windows Explorer, the file manager... no crashes, just works.

I use smb shares... works good, quick!

---

### Post by RandyRandola on 2008-07-10
There is a problem.

I have my hp1020 working perfectly in uBuntu. (after following the steps outlined [here]("http://foo2zjs.rkkda.com/"))
XP Pro on VMware works flawlessly except for printing.

New Windoz drivers from HP.

Select VM, Removable Devices, USB Devices, and I see the hp1020.
If I select it, and try to print to it (either test page or from an application) the screen goes blue with a dump of some sort (I would post it but it flashes by too quickly) and then XP tries to reboot. 

I say try as it stays on the Windoz screen until I de-select the printer. Then it all works again.

---

### Post by fjgaude on 2008-07-10
> **RandyRandola said:**
> There is a problem.

I have my hp1020 working perfectly in uBuntu. (after following the steps outlined [here]("http://foo2zjs.rkkda.com/"))
XP Pro on VMware works flawlessly except for printing.

New Windoz drivers from HP.

Select VM, Removable Devices, USB Devices, and I see the hp1020.
If I select it, and try to print to it (either test page or from an application) the screen goes blue with a dump of some sort (I would post it but it flashes by too quickly) and then XP tries to reboot. 

I say try as it stays on the Windoz screen until I de-select the printer. Then it all works again.

I take it you have loaded the new driver while you are in VM WinXP?

I have a Canon i9100 and an Epson R220 that work perfectly in VM WinXP, both USBs. The Epson works perfectly in Ubuntu but not the Canon.

I only use the VM for the graphic programs that I'm so used to for work flow.

---

### Post by RandyRandola on 2008-07-12
That's not useful at all. We need to hear from users who have had this problem (or one like it) and how they fixed it.

Maybe it's a bug and we'll have to figure it out on our own!

---

### Post by sgleo87 on 2008-09-01
> **RandyRandola said:**
> There is a problem.

I have my hp1020 working perfectly in uBuntu. (after following the steps outlined [here]("http://foo2zjs.rkkda.com/"))
XP Pro on VMware works flawlessly except for printing.

New Windoz drivers from HP.

Select VM, Removable Devices, USB Devices, and I see the hp1020.
If I select it, and try to print to it (either test page or from an application) the screen goes blue with a dump of some sort (I would post it but it flashes by too quickly) and then XP tries to reboot. 

I say try as it stays on the Windoz screen until I de-select the printer. Then it all works again.

I have the same problem with my Canon MP500. It works fine in Ubuntu. The drivers installed correctly on my XP virtual machine (using VMWare Server) but when I start a printing job I get the blue screen. Anyone found a solution to this yet?

---

### Post by RandyRandola on 2008-09-02
VMware 1.0.6 has an issue with some USB 2.0 devices. Until the manufacturer fixes this, you would need to get a USB1.0 hub and plug your USB 2.0 devices into that.

I have not tried VMware 2.0 yet as it seems to have too many bugs. And I can live with just one at this time. 

Lots o help aren't I? :lolflag:

---

### Post by tufcamman on 2009-03-02
Hey,

I've had this problem too, but I found a way to fix it.  I'm using all sorts of USB 2.0 devices on my XP Vmware now.

You need to edit your .vmx file that describes your virtual machine to include these things.

virtualHW.version = "6"
usb.present = "TRUE"
ehci.present = "TRUE" //I had to add this one, it wasn't allready there

Restart your Virtual Machine and you should be in business.  No more Blue Screen of Death when you try to plug in your scanner :)

---

