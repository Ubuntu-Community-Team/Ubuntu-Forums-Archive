---
title: "rebooted after 400 days....now stuck in GrubLand"
date: 2012-08-03
forum: Server Platforms
---

### Post by platinumwhitty on 2012-08-03
So I am a new administrator at an ISP and Ubuntu is used on the servers.  Needed to reboot the machines so file checking could happen and new kernel would load.

OH CRAP!!!

Now it either says File not Found for 10.04  Kernel 2.6.32-22-server

OR

for 10.04 Kernel 2.6.24-27-server it complains about an LVM volume being degraded and drops to BusyBox

I have read the forums but still stumped but learned enough to know I needed to attach results from boot info script!

I have a similar machine that I can still get to and it says it is running Ubuntu 10.04.1 Kernel 2.6.32-24-server and another running 2.6.32-28.

I think this is either a Grub (0.97) or LVM or combination issue that is probably fixable but I am not in possession of the knowledge to do so.

I would appreciate any help and will provide any additional requested information about the system that I am able to get.

Thanks!

---

### Post by darkod on 2012-08-03
I know you said you are new so you probably won't be able to answer some questions, but we have to ask. I see many confusing things in the results, but not sure I have all the answers too.

So, under the assumption the bootinfo script created the results correctly:

1. On the /dev/sda disk you seem to have grub1 and 10.04 LTS installed with LVM. 10.04 LTS is coming with grub2, but this might have been removed if someone wanted to use grub1. Or the 10.04 was an upgrade from 8.04 and they didn't upgrade grub on purpose.

2. The menu.lst on /dev/sda1 is looking for kernel 2.6.32-22 which doesn't exist on the /dev/sda disk (look at the list of boot files, it lists many kernels present but not that one).

3. As if the above is not confusing enough, the /dev/sdb disk has grub1 and 8.04 LTS installed with LVM according to the results. What the hell? If this is a production server, who installs dual OS? How do they use the server, one day with 10.04 and the next day with 8.04? Makes no sense... Usually you don't dual boot servers.

I can't be sure if the whole LVM was a single installation and somehow broke off, or what. Because at the moment this looks like dual boot.

The menu.lst on /dev/sdb1 looks correct, and the kernel it wants to boot 2.6.24-16 exists on /dev/sdb.

---

### Post by platinumwhitty on 2012-08-06
Here is a results file from the primary DNS server whose setup should be similar to the one I am having trouble with.  It also has not rebooted in over 400 days so I would expect I could have similar issues but  hoping to figure them out with the secondary DNS server first.  :)  

1.  I remember trying to upgrade grub via Webmin and it failed but not sure why.  This could be why the older grub is still on that box.

2.  The HD was getting full and I manually deleted some of the older kernels - WHOOPS - could have caused my own problem.  Could I simply point it to a kernel that is there and expect it to boot?

3.  I believe this could be hardware RAID.  Would that explain some things?  The primary server shows 2 SCSI devices but only A has partitions on it and it is the only physical device showing in LVM.

Learning lots and sure appreciate the assist!!



Caryl

---

### Post by darkod on 2012-08-06
1. I understand the GUI of webmin might be tempting, and I am not some great server administrator neither, but try to do as much with the CLI as you can, especially about the bootloader upgrades. I wouldn't let webmin touch that.

2. If you were deleting kernels here too, you might have a problem also. Look in the results where menu.lst is displayed, scroll through the options until the menu entires show up. First, the default option in grub1 is 0 which means the first entry (they start counting from 0). Now, if you look at the first entry, it is looking for kernel 2.6.32-24 and that is not listed as present in sda1: List of files loaded by grub. You could edit menu.lst and change 2.6.32-24 with 2.6.32-41 which is the latest kernel present on sda1. That should work.
The third entry is looking for kernel 2.6.24-28 which is present and should boot but since according to the settings grub1 will try to load the first entry, the third one is pointless.
Besides, I wouldn't try booting 2.6.24-xx since it's previous version of ubuntu, notice the difference with 2.6.[COLOR=Red]32[/COLOR]-xx.

3. What could be most important. Usually hardware raid on servers is proper hardware raid, which means the raid device is set up long before the OS comes into play. If these are two disks in raid1 then ubuntu should see a single /dev/sda disk. I have recently installed 10.04.4 LTS on a couple of Dell servers and it recognized the raid1 array as single /dev/sda disk.
In your case, both on the server where you have the issues, and in these results of the other server, it recognizes two disks, almost like separate ones.
I definitely don't expect that from hardware raid.

Can you try this on the "broken" server:
Attach a monitor, keyboard and mouse and boot it with the ubuntu desktop live cd (so you can boot it in live mode, the server cd can't boot into live mode).
Open /dev/sda1 and open the /grub/menu.lst file.
Assuming they have the same kernels with the server whos results you posted, replace the kernel of the first entry as suggested above in number 2. Save and close the file.
Reboot without the cd and see if it boots that 2.6.32-41 kernel.

Even though the raid setup looks weird, lets see if it can boot if the kernel is correct in menu.lst.

---

### Post by platinumwhitty on 2012-08-07
THANKS SO MUCH TO DARKOD~~ :KS

Pointing to GRUB to 32-41 did the trick.

I have already changed my other server B4 I reboot it!

Enjoy your day!

Caryl

---

### Post by darkod on 2012-08-07
No problem, glad you got it going.

I have to say again, that raid setup looks weird. The disks should not show as sda and sdb in fdisk.

I don't know if you want to investigate that further or you are happy running the servers as they are as long as they boot. :)

---

### Post by platinumwhitty on 2012-08-09
Think I will go with it for now.

Tonight is rebooting ns1!!

Caryl

---

