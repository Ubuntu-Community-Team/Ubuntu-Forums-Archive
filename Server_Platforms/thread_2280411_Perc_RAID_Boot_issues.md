---
title: "Perc RAID Boot issues"
date: 2015-05-29
forum: Server Platforms
---

### Post by ryan161 on 2015-05-29
A quick request for assistance, which would be so much appreciated. Running the program doesn't provide me with the option to run a repair at all.

Here's the boot info  [http://paste.ubuntu.com/11439213/](http://paste.ubuntu.com/11439213/)

The first drive of six in a RAID 10 setup went bad. It won't boot now. Trying to get it to boot.  Ubuntu Server 14.01 LTS

---

### Post by oldfred on 2015-05-30
Moved to your own thread in Server area, since RAID.

I do not know RAID. 
What kind of RAID? Hardware or mdadm?
It is not showing a valid partition table, but that could just be the type of system it is, so do not know if wrong or not.
It is only showing one drive, also. 
Usually even with RAID, it will show the other drives.

---

### Post by darkod on 2015-05-30
When you say it went bad, did you replace it already or not? During mdadm setup it asks you if you want it to boot degraded. If you selected No and if one member of the raid is still failed, then the array is degraded and it won't boot.

You want to boot it to continue using it, or to replace the failed member? If you plan to replace the disk ASAP you can do that booting the machine in live mode using the Desktop live CD. In fact that might be the preferred, replacing the disk from live mode instead of booting the array. It's up to you.

Also the issue could be if your board is trying to boot only from the first disk, and if that is the one that failed. In theory grub should have been installed on all disks, so as long as your board is trying to boot from all disks in order, it should not be an issue of missing grub.

Otherwise, for more info, you would have to boot in live mode and run some mdadm commands to get details of your array.

---

### Post by ryan161 on 2015-05-30
Thanks for assistance. It is a Dell PowerEdge server with PERC RAID card.

---

### Post by ryan161 on 2015-05-30
Darko,

Thanks for the help! It has not been replaced yet, the Boot Info [http://paste.ubuntu.com/11439213/](http://paste.ubuntu.com/11439213/) shows as it is now. The virtual disk/RAID has been put in Degraded state to attempt to boot/recover. 

We are planning the replace the failed drive (will be here on Monday) - but our concern is losing the data on the other drives.
Indeed, the issue is that it is trying to boot only from the first disk, and it is that one that failed. We don't have grub installed on all disks.

So once we have bad drive replaced - what is the procedure? How do we get Ubuntu on new disk and RAID up, with all data/settings as it was before?

When you say "[COLOR=#000000] replacing the disk from live mode instead of booting the array" what do you mean by this? I haven't done this before, so your help is much appreciated!

[/COLOR]

---

### Post by darkod on 2015-05-30
I thought you are using mdadm linux software raid. If you are using the hardware PERC raid, then mdadm has nothing to do with it. In fact, the hardware raid should run the booting, in that case the grub should be on the MBR of the array. The array should still be up with one member issing from raid10, so in fact it should boot ok.

But in this case you are in the hands of the PERC card, it doesn't depend much on ubuntu. And the replacing of the disk is not done from ubuntu, so ignore my previous comment. After replacing the disk the PERC should start the rebuild automatically. If that will make it boor or not, I don't know.

This is why most common for linux servers is to use mdadm software raid. Much more flexible but HW raid has it's strong points too...

---

### Post by ryan161 on 2015-05-30
Yes it is hardware PERC RAID.  We thought that with only 1 disk failed of the RAID 10 that it would be bootable - but apparently not. It appears the MBR/grub is on the first disk, the disk that failed (does make sense?).  What does [http://paste.ubuntu.com/11439213/](http://paste.ubuntu.com/11439213/)  explain? Is the MBR and partitions in tact/recoverable? 

Also, why the Boot-repair not provide me with option to do "Recommended Repair"?  The only option I have is to run the Boot Info.

---

### Post by oldfred on 2015-05-30
Changed your title to Perc RAID, since that is important.

Not sure if Perc uses standard partitions and boot loaders or not. You may only see it correctly if using the Perc hardware & drivers.

Grub has several .mod RAID files that you load with the insmod command. Not sure if one of those is required or not. Or if totally custom.

---

### Post by darkod on 2015-05-30
With HW raid the array is assembled right away at the start after the BIOS POST. After that the OS (Windows, Linux) sees a single disk equivalent (or how many different arrays you set up in the HW raid config). The script results go along these lines by showing only sda (the array) and sdb (usb stick). That's why you don't see six disks like you would with SW raid.

So I would be very surprised if grub ended up on the first disk because for ubuntu the disks don't exist as devices. Only the array. Grub should be on the array MBR.

Why the script is not showing a boot loader on sda (which is the array) I don't know. Maybe it can't "understand" this PERC array completely. That might be the reason it's not offering a recommended repair too. Besides, in my opinion, servers are too serious to use recommended repairs, when you can't know for sure how will it end up. With production servers you do things manually and very carefully.

You could still try booting into live mode, try to activate the array, and check it out. That should work under the assumption that live mode can read the PERC, and that the PERC is keeping the array still assembled and functioning. From live mode you can even install grub to the MBR of the array. Of course only if the array is read and activated correctly by ubuntu.

Since the server was running so far, I would assume ubuntu can read this PERC array.

Depending how long you have to wait to replace the failed disk, you might decide not to touch anything until that is done and see how it goes after the disk is replaced. It might start working on its own. In fact, a raid10 should keep working with one member missing but in your case it might be an unfortunate combination of PERC raid + ubuntu/grub complication.

You said the "virtual disk has been put in degraded state to try to boot". Was that manually? If yes, in what state was it automatically without anyone changing it? Are you sure the PERC is passing the array still as active?

---

### Post by SeijiSensei on 2015-05-30
When you boot the machine, are you given an option to enter the RAID BIOS?  If so, you'll want to handle all the operations from there.  As darkod says, Linux knows nothing about the components of the array or how to manage them.  It sees only a single device.

---

### Post by ryan161 on 2015-05-30
> **darkod said:**
> 

You said the "virtual disk has been put in degraded state to try to boot". Was that manually? If yes, in what state was it automatically without anyone changing it? Are you sure the PERC is passing the array still as active?

Yes, done manually. With the one disk failing, the PERC at first was halting the mounting of the Virtual Disk. The only way to proceed is to select the bad drive in the PERC BIOS and allow PERC then to mount the Virtual Disk without the bad disk. The result is that the Virtual Disk (disk array) is in the DEGRADED state. The practical symptom is that now it doesn't boot Ubuntu.

So, to answer your question, the Array is active, but in a degraded state.

---

### Post by ryan161 on 2015-05-30
Yes, I can enter the RAID BIOS by Ctrl-R. In the Raid BIOS the first disk in the Array is marked as "failed" and is marked as "missing" from the Array. The array is now in degraded state. 
The H/W setup is 6 disks RAID 10. The first disk has failed, and now the system doesn't boot. I'm waiting for new disk to arrive on Monday. With the new disk, will it restore the RAID to bootable condition?

Thanks for the reply!

---

### Post by ryan161 on 2015-05-30
> **darkod said:**
>  So I would be very surprised if grub ended up on the first disk because for ubuntu the disks don't exist as devices. Only the array. Grub should be on the array MBR.
Agreed. Hence my surprise why it isn't booting up. The Array is up, albeit in degraded state.


> **darkod said:**
> You could still try booting into live mode, try to activate the array, and check it out. That should work under the assumption that live mode can read the PERC, and that the PERC is keeping the array still assembled and functioning. From live mode you can even install grub to the MBR of the array. Of course only if the array is read and activated correctly by ubuntu. 
Yes, I have booted into live mode - how would I  1.) check if the array is assembled and 2.) install grub to the MBR?  

> **darkod said:**
> Depending how long you have to wait to replace the failed disk, you might decide not to touch anything until that is done and see how it goes after the disk is replaced. It might start working on its own. In fact, a raid10 should keep working with one member missing but in your case it might be an unfortunate combination of PERC raid + ubuntu/grub complication. 
Drive will be here on Monday, but I need to consider all my options at this point.

Thank you for your reply.

---

### Post by darkod on 2015-05-31
In general, the dmraid package handles HW raid. To search for all arrays and activate them, the command is:
```
sudo dmraid -ay
```

I think that will list any arrays found. If it does, be careful when working in it because one is the array, and another thing partitions on it. The partitions would usually end in p1, p2, etc and the array device is the whole name before that.

List the results of that command and we will see.

PS. Forgot to mention. dmraid is used with the motherboard raid chips and probably some HW cards, but I am not sure if it is used with the PERC card or not. Before trying that dmraid command it might be best to check all disks and partitions with:
```
sudo parted -l (small L)
```

If that lists the array as /dev/sda that means it is already recognized without dmraid. The dmraid devices start with /dev/mapper/... In that case you could try managing /dev/sda as any other single disk.

---

### Post by ryan161 on 2015-05-31
Thank you, I will try that and let you know.

---

