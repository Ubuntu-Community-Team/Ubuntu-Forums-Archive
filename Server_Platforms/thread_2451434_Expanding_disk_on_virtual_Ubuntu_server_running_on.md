---
title: "Expanding disk on virtual Ubuntu server running on ESXi 7"
date: 2020-10-04
forum: Server Platforms
---

### Post by Parth_Maniar on 2020-10-04
Hello,

 
 I hope you and your loved ones are safe and healthy.
 

I  have a VM running Ubuntu 20.04.1 LTS on VMWare ESXi. There are two  volumes one running as boot (backed by HDD) and one is mounted (which is  from SSD). Mounted volume was initially 360 GB in size, I 

have inceased  it 406 GB in ESXi. Post reboot of the VM I do see the disk space  increasing in ```
 fdisk 
``` but not in ```
df -i
```. 
  




[IMG]http://users.ox.ac.uk/~kell4724/current_disk_size.png[/IMG]


What do I do to expand the disk?

---

### Post by TheFu on 2020-10-04
**df -i** only shows inodes.  That isn't exactly useful 99.99999% of the time.  **df -Th** is much more useful, but really the command I provide a few paragraphs below is even better.

Changing the size on the hypervisor is like magically changing a 360G HDD into a 405G HDD and doing a bit-for-bit clone.
What you have now is a 405G HDD that is only partitioned for 360G and the file system hasn't been extended.  If you use any volume management, those would need to be modified as well.

So, first we need to know if there is any volume management being used inside the guest VM.  Something like LVM or ZFS or BRTFS. If you use those, things are different.  I'm fairly good with LVM, so I can help with that. If you can have downtime, please say so. If you can't have downtime, please say so. We can deal with both situations with LVM, but the answers are different.

Run these commands from inside the guest VM OS:
[LIST]
[*]What file systems are being used?  **df -hT -x squashfs -x tmpfs -x devtmpfs**
[*]Are you using any volume management inside the guest OS?  **lsblk -e 7 -o name,size,type,fstype,mountpoint**
[*]What are the current partition table settings?  **sudo fdisk -l**
[/LIST]

When posting, please remove any 'loop' devices that show up in any output. Those are all cruft and unwanted. Post using _code tags_, so the output is readable. Use the _advanced editor_ here for that.

Those two ugly commands provided remove stuff we don't want to see. They keep the cruft down. I have aliases for each because they are so very handy.

Thanks. Use _code tags_.

---

### Post by Parth_Maniar on 2020-10-04
Hi @TheFu, I apologise for giving partial information.

1. I would like to avoid downtime. However, since I am running two VMs for high availability; I can keep VM off for sometime (half an hour?)
2. Filesystem is *ext4*.
3. I am not using any volume management tool but when I installed Ubuntu server I did see LVM being used for the boot volume. 

I hope this information helps.


[http://users.ox.ac.uk/~kell4724/parition_details.png](http://users.ox.ac.uk/~kell4724/parition_details.png)

---

### Post by ajgreeny on 2020-10-04
Please do not use large images inline when you post.
If you want to show terminal output copy the text, including the command, by highlighting with the mouse then copy it either bu Right click->Copy or with **Ctrl+Shift +C** then paste it in your reply.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

If you do need to add an image please use the Attachment icon (a paperclip) in the toolbar of the reply window.
If you use the Quick Reply window you will need to click on the **Go Advanced** button to see the icon.

---

### Post by Parth_Maniar on 2020-10-11
Here is I solved my specific problem. Things to keep in mind:



[LIST=1]
[*]My OS is installed on a separate physical disk (/dev/sda [HDD]) 
[*]I attached a partition from my SSD to the VM (/dev/sdb [SSD].) This was done to increase IOPS and conserve cost. 
[/LIST]


How did I expand the volume?


[LIST=1]
[*]Shutdown the VM.
[*]Increase size of the SSD volume through VMWare ESXi.
[*]Boot the VM.
[*]Stop programs (services) using the SSD volume
[*]Unmount the partition
[/LIST]



```

growpart /dev/sdb (partition number) --dry-run (for me the partition number was 1.) 

```


Followed by 



 ```

resize2fs /dev/sdb1 (since my partition was 1) 
```
[/CODE]

Done! 

Thank you to everyone for helping me out.


PS: Source: [https://unix.stackexchange.com/questions/373063/auto-expand-last-partition-to-use-all-unallocated-space-using-parted-in-batch-m](https://unix.stackexchange.com/questions/373063/auto-expand-last-partition-to-use-all-unallocated-space-using-parted-in-batch-m)

---

### Post by ameinild on 2020-10-11
If it was me, rather than resize filesystems directly, I would use LVM2 to make a logical volume and install the system on this. I believe this is an easier and safer way to resize volumes.

---

