---
title: "XP in virtual box from &quot;Rescue Disk&quot; ?"
date: 2011-07-23
forum: Virtualisation
---

### Post by grey1beard on 2011-07-23
I'm currently running 10.04 on a Toshiba laptop, and I have a problem installing a Ricoh Gelsprinter which I ran on XP(98 not supported).

As I have recently reinstalled 10.04, and removed the original xp installation, I now realise that I either have to reinstall xp as a dual boot, or to run the printer via a virtual box with xp inside.

Snag - I only have the Toshiba rescue disk that came with the machine, rather than an original xp on cd.
Question - is it possible to use this as a source to do the install inside the virtual box ?

I'm not sure until I try that I can even go back to a dual boot with this disk now I have deleted the original os :(

Advise/help/suggestions most gratefully received.

John

---

### Post by Tea4all on 2011-07-23
I probably could get the printer working in Ubuntu. If you want to go with the Virtual machine route, I know how to do that too. You just need to be **really** careful, or you can **corrupt** your Ubuntu install.

---

### Post by grey1beard on 2011-07-24
Hi Tea4all,
I'd be much happier getting the printer running in Ubuntu. 
I need xp like a hole in the head !
I have tried before on another machine running 10.10, but only with limited results.
I can't remember the details, but it was pretty useless, so if you care to spend the time guiding me through, I'd be happy to try, whatever the result ;)

This laptop is up-to-date, running 10.04.3
John

---

### Post by Tea4all on 2011-07-24
What's the model?

---

### Post by grey1beard on 2011-07-24
Toshiba Satellite A30
The printer is Aificio GX 3000

Not sure which you needed, but there you go. :)
John

---

### Post by Tea4all on 2011-07-24
Is this over a network, or directly plugged in?

---

### Post by grey1beard on 2011-07-25
The printer is plugged in via usb.

John

---

### Post by Tea4all on 2011-07-25
Any way to plug it in through Ethernet? My Internet got cut off, so I'm using the neighbor's.:D If not, there is no way for it to work without a Virtual machine or a Windows PC. If you have an old, unused desktop, I would recommend using that instead and use Windows printer sharing. [https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)
If not, a virtual machine.
1. Convert the recovery partition to Virtualbox format
```
sudo cat /dev/YOURPARTITION | VBoxManage convertfromraw stdin OutPutFile.vdi NUMBEROFBYTES

```
Use fdisk to find the NUMBEROFBYTES 
```
sudo fdisk -l /dev/YOURPARTITION
```
Replace YOURPARTITION and NUMBEROFBYTES with the correct information.
**Be sure the information is correct or you can destroy ALL the data on the hard drive! **
2. Make a new VM in Virtualbox. Inport OutPutFile.vdi and set it as the boot partition. Boot and install. You can delete OutPutFile.vdi when you're done.

---

### Post by grey1beard on 2011-07-26
Thanks Tea4all.
I think the acquisition of an old desktop might be a good idea, as I have a couple of other programs that are giving me problems in ubuntu.
But with your instructions in one of my subscribed threads, it's easy for me to have another go later.
Thanks again,
John

EDIT Unless there is such a thing as an ethernet/usb converter  :)
I'll have a look, and if there is, I'll give you a heads up.

EDIT 2 Have got an adapter winging its way to me.
I'll come back when it arrives, and have had a chance to see if it works ;)

---

