---
title: "Dell R410 with SAS 6/i RAID controller"
date: 2011-11-30
forum: Server Platforms
---

### Post by kepstein on 2011-11-30
I have a Dell R410 with a SAS 6/i RAID controller. I have a RAID1 set up. During install of Ubuntu Server 11.04 everything goes well, with no indication of any problems. After the install is complete and the server goes down for a reboot, that's where things start to fall apart. The box starts to boot and then promptly gets dropped to the Busybox shell. 

I've read all sorts of thread on using the rootdelay= option in the /boot/grub/grub.cfg but it hasn't helped. More bizarrely, is that as soon as I get dropped at the initramfs prompt, if I type "exit" the server continues to boot, and within a second or so is fully up and running. 

 I compared with another R410 I have running the exact same version of Ubuntu Server, where I did not experience this issue. The only difference I can see is that on the other box I have a PERC 6/i controller instead of the SAS 6/i controller.  

Any ideas out there? Are there other changes I have to make in grub to make this work?

---

### Post by SeijiSensei on 2011-12-01
Hmm, just yesterday, I installed 10.04 server on an R410 with SAS and didn't have any issues with it. The SAS controller manages the two-drive RAID 1 array and presents it as a single device to the operating system.  

Running lsmod shows a SAS driver as the first kernel module loaded on this box.  When you get the past the grub issue and the machine starts, do you see any sas_ modules in the list?

Do you see the same behavior if you boot the "recovery mode" version of the kernel?  Did you install grub to the root of /dev/sda?  I use a separate /boot partition; maybe that matters?

If you're just putting the machine into service, perhaps you should try installing 10.04.3 LTS server instead of 11.04.  I generally avoid any non-LTS releases when I'm building servers.

One reason I can think of for a problem at boot is if the sas modules aren't included in the initrd image that Linux uses during boot.

---

### Post by kepstein on 2011-12-01
I do see SAS modules being loaded once I have the box up and running. 


Module                  Size  Used by
ipmi_si                52720  1
mpt2sas               139322  1
raid_class             13554  1 mpt2sas
mptctl                 38779  1
ipmi_devintf           17747  2
ipmi_msghandler        45498  2 ipmi_si,ipmi_devintf
dell_rbu               13714  0
joydev                 17606  0
lp                     17789  0
psmouse                73535  0
dcdbas                 14438  0
i7core_edac            27903  0
ghes                   13658  0
edac_core              53845  1 i7core_edac
serio_raw              13166  0
hed                    13226  1 ghes
power_meter            18191  0
parport                46458  1 lp
mptsas                 59148  2
mptscsih               44457  1 mptsas
mptbase               102904  3 mptctl,mptsas,mptscsih
usbhid                 46956  0
usb_storage            53538  0
uas                    17996  0
hid                    91020  1 usbhid
bnx2                   85989  0
scsi_transport_sas     40545  2 mpt2sas,mptsas

At this point I want to stick with 11.04. The reason primarily being that we already have a DEV and QC environment built out, and we want to keep environments strictly controlled - to that end, we'll be replacing the SAS controller with a PERC 6/i controller, but until the parts are delivered I need to have these machines up and running. 

Thanks.

---

### Post by kepstein on 2011-12-01
We grabbed a loaner PERC controller card and replaced that SAS 6/i controller, imported the foreign disks, and booted up with no problem at all. I suspect that Ubuntu doesn't like that very basic SAS controller too much. 

We'll be ordering some PERC cards and moving on from there. 

Thanks again.

---

### Post by Philip550c on 2012-02-20
Which PERC cards do you use?
From what I can tell ubuntu doesnt work with many of them.
[http://ubuntuforums.org/showthread.php?t=1519896]("http://ubuntuforums.org/showthread.php?t=1519896")

---

