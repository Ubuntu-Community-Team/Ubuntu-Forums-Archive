---
title: "CloneZilla Reports &quot;Kernel too old&quot; ???"
date: 2016-04-20
forum: Virtualisation
---

### Post by Rick St. George on 2016-04-20
Running UbuntuStudio v14.04 LTS

Running CloneZilla in VBox and Attempting to Read a Backup on an External Drive. But Screen shows;

> 
ERROR! No existing partitions or no unmounted partitions are found! To use ConeZilla to save or clone a partition, the source partition must exist or be unmounted! If you are sure the partition exists in this machine, maybe the kernel is too old? Press Enter to exit ....


I recently removed old kernels. Could this be the problem? If so, How can I check and fix it?

Thanks for any suggestions.
Rick

---

### Post by QDR06VV9 on 2016-04-20
> **Rick St. George said:**
> Running UbuntuStudio v14.04 LTS

Running CloneZilla in VBox and Attempting to Read a Backup on an External Drive. But Screen shows;



I recently removed old kernels. Could this be the problem? If so, How can I check and fix it?

Thanks for any suggestions.
Rick
Try this for
> Error! No existing partition(s) or no unmounted partition(s) are found! To use Clonezilla to save or clone a partition, the source partition must exist or be unmounted! If you are sure the partition exists in this machine, maybe the kernel is too old?
Press Enter until presented with the choice of poweroff / reboot / enter command line prompt / start over.

Select "Enter command line prompt"
Issue the command: 
```
cd /home/partimag
```

Issue the command: 
```
sudo /opt/drbl/sbin/ocs-sr -g auto -e1 auto -e2 -c -r -j2 -p true restoreparts image-file sda1 sda2 sda3
```
After this, the partition table and the partition contents should be restored correctly.
Regards

---

### Post by Rick St. George on 2016-04-20
Get the following;
> 
/opt/drbl/sbin/ocs-sr: command not found


---

### Post by QDR06VV9 on 2016-04-20
> **Rick St. George said:**
> Get the following;

That is odd?
Not sure how you did your setup in making the .img , But Check this site for more solutions: [http://clonezilla.org/advanced/make-live-recovery-manually.php](http://clonezilla.org/advanced/make-live-recovery-manually.php)
I need some time to think on this and grab a quick snack.
EDIT: Just to be sure the method used was something along these lines
> 1. Connect the external hard drive (source of the image) and the blank  hard drive (target). The machine does not have any other drives.
2. Boot Clonezilla live CD, select English US keyboard.
3. Select "Start Clonezilla"
4. Select "device-image"
5. Select "local_dev"
6. Select the external drive containing the image
7. Select root directory
8. Select "Expert" mode
9. Select "restoreparts"

If you used a different method could you describe that here.

---

### Post by Rick St. George on 2016-04-21
Followed those steps, Except that in No.1 above -  the target drive is Partition 1 on Drive No. 2 (drive 1 is OS on a SSD). VirtualBox is running on Drive 1, but created the VDrive on Drive 2 Partition 1 (target), while Drive 2 Partition 2 (source) has the Backup 90GB image. That didn't seem to work, so I moved the Backup image to an external 2TB HD via USB. 

Perhaps since it is auto-mounted, could this be a problem? If I click the icon to disengage it, the system won't see it at all?!?!?

Starting the Recovery VDisk in VirtualBox to Boot first with DVD to Run ConeZilla (in order to Restore the BU to empty Partition 1 on Drive 2. Run into problem as mentioned in my first post - which is Step 6 (fail) in post above.

Any ideas?

---

### Post by Rick St. George on 2016-04-21
Also Note: Upon selecting Devices / USB / had to go back into Settings and Select the USB device. Then upon running the VM again, received this
> 
ERROR: Failed to attach the USB device Wester Digital Passport 0820 (1012) to the virtual machine. Details: Failed to create a proxy device for the USB device (Error: VERR_PDM_NO_USB_PORTS).


Does this Help explain what's going on? Because it doesn't to me. My WD Passport shows up in File Mgr.

Stumped ! ! !

---

### Post by Rick St. George on 2016-04-21
Finally got it to show up (after closing and re-open VM) and got as far as RESTORE DISK, but receive this Error;

> 
Shutting down the Logical Volume Mgr. Found udevd rule causes block devices with LVM signatures to be automatically added to their volume group. Temporarily disable it otherwise the partition tool won't be able to inform the kernel the changes of partition table ...
/lib/udev/rules.d/85-lvm2.rules -> /lib/udev/rules.d/85-lvm2.rules.drblsave
Finished Shutting down the Logical Volume Mgr. Searching for images ....
**[COLOR=#ff0000]No disk image is found in /home/partimag.. Make sure you already save an image! Or make sure you did not try to restore an image saved from partition(s) to disk(s)! Program terminated!!![/COLOR]**


Still Stumped !?!?

---

### Post by QDR06VV9 on 2016-04-21
Sorry Got A long list of chores this afternoon.
I have never used a VM doing this before..So new teritory for both of us.

If you remove the xfs lvm snapshot of 1404root using the installed system   (Yours may be different syntax)
```
sudo lvremove /dev/sys-vg/1404root
```
and then boot with the same clonezilla-live usb key as above then the alt testing live usb should work as expected for imaging the installed drive.

Hence the problem appears initially to be with lvm snapshot volumes.
Just to be on the safe side make another copy or copy to another folder encase of a mishap..(So Two copy's of that .img)

---

### Post by Rick St. George on 2016-04-22
Forgive my ignorance Runrickus, but would that be at the Command Prompt while running CloneZilla in the VM? And then ReBooting the VM?

I don't know what a USB key is; or 1404root; or lvm snapshot. Don't care at this point. All I want to do is Restore my BU in an empty partition so I can retrieve a file. Next time, I won't use ConeZilla for a BU. Thanks man for any help!

BTW ... my kernel verion is;
3.13.0-85-lowlatency

Rick

---

### Post by QDR06VV9 on 2016-04-22
> **Rick St. George said:**
> Forgive my ignorance Runrickus, but would that be at the Command Prompt while running CloneZilla in the VM? And then ReBooting the VM?

I don't know what a USB key is; or 1404root; or lvm snapshot. Don't care at this point. All I want to do is Restore my BU in an empty partition so I can retrieve a file. Next time, I won't use ConeZilla for a BU. Thanks man for any help!

BTW ... my kernel verion is;
3.13.0-85-lowlatency

Rick
There is nothing to forgive, I have used linux for 12 years and still get stumped from time to time..:D
USB key = USB Drive or USB Thumb Drive sorry I was not more clear on this.
But yes at a command prompt while running CloneZilla in the VM.
But I also have had a few issues using CloneZilla.
Now i just use dd to clone any of my drives.(Off the subject at hand)

---

### Post by Rick St. George on 2016-04-24
I didn't get to enter the command above. Now I do not get the message in #7 above, because I chose "RestorePart" as in partition. I want to Restore the Backup into the VBox partition 200GB space. Received this Message;

> 
No partition is found in this machine. To resotre an image of partition, partition(s) must exist on the destination disk. Now enter another shell to allow you to create partition tale on the destination disk. You may use fdisk, cfdisk, sfdisk, or parted to do that. When everything is done, run "exit" to go back to the original program.


Funny ... I don't recall having to create a pratition with a VM (virtual machine). Does this sound right to anyone? Maybe I should have posted this under Virtual Machine. 

ATTN: MODERATOR You may want to MOVE this Post!

Thanks for any and all help . . especially to "RunRickus". 
Any ideas?
Rick

---

### Post by QDR06VV9 on 2016-04-25
Moved to Virtualisation at OP request

---

### Post by Rick St. George on 2016-04-25
Grabbed a copy of System Rescue CD, and used Gparted to format the new partition inside the new Virtual Disk. 

Got as far as Restoring the BackUp, and received a FAIL message. (gone now can't reprint). But it referred me to this;
[URL="http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq"]http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq
[/URL]

Followed the process of renaming files (using SDA2) location for new VirtualDisk, and received the FAIL message again.
Still unsuccessful. Will try something and post results. Any ideas would be appreciated.
Thanks!
Rick

---

### Post by Rick St. George on 2016-05-07
Here is the Error I now get;

> 
cat: /tmp/2016-02-28-img-tmp-cnvted/sda2.ext4 ptcl-img.gz.aw: input/output error

Partclone fail, please check /var/log/partclone.log!

gzip: stdin: unexpected end of file
>>> Time elapsed: 1211.94 sec
Fininshed unicast restoring image 2016-02-28-img-tmp-cnvtd to /dev/sda2.
Informing the OS of partition table changes .... done!
***********************************************
Failed to restore partition image file /tmp/2016-02-28-img-tmp-cnvtd/sda2* to /dev/sda2! Maybe this image is corrupt or there is no /tmp/2016-02-28-img-tmp-cnvtd/sda2*!  if you are restoring the image of partition to different partition, check the FAQ on Clonezilla website for how to make it.
Press Enter to continue ....


Note during the process, it shows on the screen it is going to make a temp file of the image.
Why .... I don't know.
Any suggestions?  I don't believe the img file is corrupt.

thanks for any help!

---

### Post by QDR06VV9 on 2016-05-09
Hey we be on to something with the new error reported
> Failed to restore partition image file  /tmp/2016-02-28-img-tmp-cnvtd/sda2* to /dev/sda2! Maybe this image is  corrupt or there is no /tmp/2016-02-28-img-tmp-cnvtd/sda2*!  if you are  restoring the image of partition to different partition, check the FAQ  on Clonezilla website for how to make it.
Press Enter to continue ....
I have seen that one before and as suggested
[http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq](http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq)
Read over that a bit to make it fit your circumstance's.
For Reference: [https://sourceforge.net/p/clonezilla/bugs/123/](https://sourceforge.net/p/clonezilla/bugs/123/)
Maybe??

---

### Post by Rick St. George on 2016-05-10
Sorry Runrickus ... Did that, mentioned in post 13 above. But noticed there are other files referencing SDA1 within them. Changing them also to SDA2, and we'll see what happens.

NOPE ... still FAILS. Then CloneZilla deletes all that it has done.

---

### Post by QDR06VV9 on 2016-05-10
I am trying to recreate to see if there is something we are missing here.
Might take me a bit though.
But if you remember how you set-up Clonezilla for this it might be helpful to me.
Thanks.

---

### Post by QDR06VV9 on 2016-05-11
Mr. St. George I have done three successful restores in a VB with Clonezilla.
I am very sorry I have nothing here to help you with.:sad:
Not sure if this matters though I used Tuxboot to create my Clonezilla Bootable: [http://tuxboot.org/download/](http://tuxboot.org/download/)
But we tried.

---

### Post by Rick St. George on 2016-05-19
> **runrickus said:**
> I am trying to recreate to see if there is something we are missing here.
Might take me a bit though.
But if you remember how you set-up Clonezilla for this it might be helpful to me.
Thanks.

I'm starting up the New VBox VDisk with CloneZilla CD in the disk-drive. CloneZilla boots up (otherwise the VD won't boot - no OS yet). After Clonezilla comes up, I use "RestorePart" to restore a Backup on an External Drive plugged into the USB port. Select it as "Partimage" and attempt to Restore to the VDrive in the VBox. It starts and goes to about 20 to 30% Restoring when it hits the Error Message quoted above.

May have to give up on this scenario. But I will wait for one last suggestion. Any takers?

Rick

---

