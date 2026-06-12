---
title: "Adaptec I20 Raid controller boot hangs"
date: 2007-02-13
forum: Server Platforms
---

### Post by kwambus on 2007-02-13
Hi,

I don't hold out much hope here as my searches suggest that this question remains unanswered in the past, but I can but try.

I have installed both Dapper Server and Edgy Server onto a Supermicro twin Zeon server which has an Adaptec I20 raid controller.

The install went fine but on boot up I get:

iop0: device already claimed
iop0: DMA / IO allocation for I2O controller failed

and booting halts at that, nothing I can do. Interestingly Edgy Live CD installs and boots without a problem, but that's not really a solution for a production server.

Can anyone point me in the direction of a solution? I have searched for hours and come up with nothing I can try.

Thanks.

---

### Post by kwambus on 2007-02-14
Well as i guessed no reply.

Shame that all the posts regarding the I20 bugs get no replies, especially with it being a pretty standard enterprise raid controller.

I am surprised that Ubuntu Server doesnt support it, maybe it's not quite enterprise ready :(

---

### Post by trexcom on 2007-02-19
I found the solution!

I had the same problem with my server (Fujitsu Siemens Primergy E200 - I2O with 2 system drives)
Now i'm going to explain how I solved, so you can fix your issue.


The installation procedure of Ubuntu Server (Dapper) assigned the following devices to my arrays

[B]/dev/i2o/hda
/dev/i20/hdb[/B]

After installation, at first boot, system hanged because the kernel module for I20 controller assignes the following devices to the arrays

[B]/dev/sda
/dev/sdb[/B]

As you can see, they are not the same, so you must change them manunally.
You have to modify your **/boot/grub/menu.lst** and let images to point to new root device (for me /dev/sda3); you must also modify the Grub config file in the default area (search for a line starting with *# kopt=*) in the same way, so if you upgrade your kernel images, the machine will work fine after reboot

Don't forget to modify also your **/etc/fstab**; you must give to your mount points the right devices!


I hope to be clear; 
my English is not so good after midnight! :) 

Bye
Trexcom

---

### Post by kwambus on 2007-02-20
Excellent! Solution worked and thank you so much for looking into it. I can once more return to my boss with a Ubuntu Server solution :)

(Hope this gets fixed in Feisty since the problem has been around since late 2004)

Thanks again.

---

