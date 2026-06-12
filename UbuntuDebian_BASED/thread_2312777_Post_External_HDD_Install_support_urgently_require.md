---
title: "Post External HDD Install support urgently required"
date: 2016-02-07
forum: Ubuntu/Debian BASED
---

### Post by martin154 on 2016-02-07
Hi all,

I have been experimenting with a number of linux distributions lately  and have decided to settle with EOS for my home laptop. I am impressed  with the performance of this OS and would like to install it on an  external HDD which I can boot from on any computer. The reason for this  is that I travel alot in my job and am a keen photographer, so while I  am travelling I would like to process my photos in my raw editor of  choice DARKTABLE on my company laptop.

So I watched a number of tutorials and felt pretty well prepared to install to my WD 500GB external USB 3.0 HDD.

Here is the process I followed:

1. booted as normal and used gparted to remove all partitions from the WD HDD
2. closed gparted, shutdown and booted into live session from dvd with WD HDD plugged in
3. Selected install os
4. when asked where I wanted to install I selected something else
5. in the free space of my WD HDD i created partitions /boot @ 300mb, /home @ 200gb, / @ 20gb and swap at 10gb
6. selected to install the bootloader to the /boot partition of my WD HDD
7. installed

Upon reboot I could boot from the external drive. Great!  However I  could no longer boot my laptop as normal, it simply gave me a grub  prompt!

I fixed this problem by going into the live session again and installing and running boot-repair.

Now I can boot the laptop as normal, but I CANT boot from my external WD HDD [IMG]https://elementaryforums.com/styles/default/xenforo/clear.png[/IMG](. My external drive shows up at boot options, but selecting just results in a flashing cursor!

Any help in getting my external hdd bootable again would be greatly appreciated. 

Regards from the ALPS and many thanks in advance.
Martin   						

ps: strange, if I  remove the internal HDD from the laptop then I can boot from the  external HDD. Put the internal drive back in and no chance to boot from  the external drive. The plot thickens........

ppss: in addition to the procedure above I have also tried to let EOS do its own install/partitioning of the drive by selecting wipe disk and install EOS, but the situation is still the same.

---

### Post by QIII on 2016-02-07
Hello!

The first things to do are (but don't do them just yet until you answer my question at the end):

1.  Remove the external drive and run boot repair on the internal drive.

2.  Remove the internal drive and run boot repair on the external drive.

This should leave you with two disk that are independent of each other -- that is, they should boot on their own when either is plugged in and the other is not.

To determine the next step, would you let us know if you are you running the external drive via USB, eSATA, Firewire, etc?

---

### Post by martin154 on 2016-02-07
> **QIII said:**
> Hello!

The first things to do are (but don't do them just yet until you answer my question at the end):

1.  Remove the external drive and run boot repair on the internal drive.

2.  Remove the internal drive and run boot repair on the external drive.

This should leave you with two disk that are independent of each other -- that is, they should boot on their own when either is plugged in and the other is not.

To determine the next step, would you let us know if you are you running the external drive via USB, eSATA, Firewire, etc?


hi many thanks for your quick response. 
yes, the external hdd is connected via usb.

i repaired the internal drive with boot-repair already, but I did not think to remove the internal HDD and run boot-repair on the external drive. that is a great idea! I will wait for your feedback however before attempting this step.

---

### Post by QIII on 2016-02-07
Remove the internal and run boot repair on the USB external.

The next thing to do would be to have them both plugged in and go to your machine, start it up and enter the BIOS/UEFI setup utility.

Make sure that you have the option to boot from USB set up and then check to be sure that USB comes before the internal drive.  This assumes that you will generally want your machine to boot to the USB drive if it is connected when you turn the machine on.

Under hard drives, make sure that your internal drive is the first (in this case the only) disk in the boot list.

Save, exit and continue booting.  Since you have both disks installed at this point, you should boot to your external drive -- since your boot order will look for a USB drive before you onboard drive.

When you get there, you may want to do 

```
sudo update-grub
``` so that if you start your machine with your external drive plugged in, you can still choose to boot from the internal if you choose.

Don't bother doing the same with your internal drive.  With your BIOS/UEFI set to boot first from USB, you'll never hit the internal drive on startup if the USB drive is plugged in.

Shut down and disconnect the external drive.  Restart and make sure that your machine will boot to the internal drive when the external is not attached.
[B]
ONE MAJOR CAVEAT:[/B]  If you boot to your internal drive when both the external and the internal are plugged in and find that updates are available for the OS on your internal drive, choose not to run the updates, shut down, remove the external drive and reboot to the internal drive only.  Run your updates.  I say this because some updates will cause GRUB to be updated *on the internal drive*, the external drive would be found if it were plugged in, and GRUB would be updated to boot either from the internal drive or the external and you could end up without the ability to boot from the external drive again.  

Don't worry about this if you are updating the OS on your external drive.  You want GRUB on that one to be aware of the internal drive.

---

### Post by martin154 on 2016-02-07
> **QIII said:**
> Remove the internal and run boot repair on the USB external.

The next thing to do would be to have them both plugged in and go to your machine, start it up and enter the BIOS/UEFI setup utility.

Make sure that you have the option to boot from USB set up and then check to be sure that USB comes before the internal drive.  This assumes that you will generally want your machine to boot to the USB drive if it is connected when you turn the machine on.

Under hard drives, make sure that your internal drive is the first (in this case the only) disk in the boot list.

Save, exit and continue booting.  Since you have both disks installed at this point, you should boot to your external drive -- since your boot order will look for a USB drive before you onboard drive.

When you get there, you may want to do 

```
sudo update-grub
``` so that if you start your machine with your external drive plugged in, you can still choose to boot from the internal if you choose.

Don't bother doing the same with your internal drive.  With your BIOS/UEFI set to boot first from USB, you'll never hit the internal drive on startup if the USB drive is plugged in.

Shut down and disconnect the external drive.  Restart and make sure that your machine will boot to the internal drive when the external is not attached.
[B]
ONE MAJOR CAVEAT:[/B]  If you boot to your internal drive when both the external and the internal are plugged in and find that updates are available for the OS on your internal drive, choose not to run the updates, shut down, remove the external drive and reboot to the internal drive only.  Run your updates.  I say this because some updates will cause GRUB to be updated *on the internal drive*, the external drive would be found if it were plugged in, and GRUB would be updated to boot either from the internal drive or the external and you could end up without the ability to boot from the external drive again.  

Don't worry about this if you are updating the OS on your external drive.  You want GRUB on that one to be aware of the internal drive.

Thanks. I will try this today and let you know. What i dont get is what aspect of the boot on the external usb hdd needs to be repaired because if i remove the internal hdd the usb boots just fine!

---

### Post by martin154 on 2016-02-07
hi,

i tried the procedure listed above. both disks boot on their own, but the external usb HDD still wont boot when the internal drive is in the machine. If when booting I go into boot device options and try to select the device (external usb device) manually, it is indeed listed however when I try to boot I get an error message immediately saying "selected boot device failed).

ideas?

---

### Post by martin154 on 2016-02-07
after many hours of playing I finally got it to work. The problem was that when selecting the boot device internal cd/dvd to start live session I was selecting the UEFI option.

1. removed internal hdd
2. started live session from dvd being sure to avoid the UEFI option
3. started install
4. at install option selected something else to make my own partitioning scheme
5. 500mb /boot, 20gb /, 8.5gb swap and rest /home. all made on the external usb HDD
6. after install started from usb HDD and ran all updates
7. started again from live cd and ran boot-repair

now I can boot from the USB HDD on my work laptop..... YAY!

---

