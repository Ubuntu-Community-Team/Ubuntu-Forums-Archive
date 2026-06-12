---
title: "Win7 Guest saved files not showing in Ubuntu"
date: 2012-01-13
forum: Virtualisation
---

### Post by ethanova on 2012-01-13
I've got Win7 in a VirtualBox run as su on Ubuntu 11.04. When I had a program through Win7 save an mp3 file, it corrupted (I guess) the file. Nautilus doesn't recognize the file. I can see it with ls through terminal, and when I run 'll' instead of having permissions and the norm to the left of the file name, it just says ? ? ? ?. Also cannot chmod it, input/output error is returned. Any ideas on how to get this fixed?

---

### Post by japzone on 2012-01-13
Your not very clear. It sounds like you made a file in Win7 and copied it to Ubuntu using the VirtualBox Folder Sharing feature. Then the file somehow got corrupted and you can't Delete/Modify/ect it.

If the above is true you need to repair the corrupted part of your Harddrive. 

**_Section 1_**(For FAT/FAT32/ext1,2,3,4 Filesystems)
Before continueing please determin if the corrupted file is on the same Drive Ubuntu is booting off of. If so please boot into a LiveCD/LiveUSB of Ubuntu before continueing.

1) Open Disk Utility and find the drive with the corrupted data(10.10-and-below=System-->Administration-->Disk Utility -- 11.04-and-above=Search "Disk Utility")

2) Determin the Filesystem of the Partition with the corrupted Data and Unmount the Partition to be repaired, also take note of its location(ie: /dev/sdb1)

3) Now Open Terminal and enter one of the Following Commands, Make sure to replace "/dev/sdb1" with your Partition's location
```

##If it's a Linux EXT filesystem
sudo fsck -y /dev/sdb1

##If it's a FAT filesystem
sudo fsck.vfat -y /dev/sdb1

##If it's an NTFS file System refer to "Section 2"

```
Your Drive should be repaired.

**_Section 2_**(For NTFS Filesystems)
If the damaged Data is in the Virtualbox VM of Windows 7 or the Harddrive it was saved to is NTFS then you must do things diferently. There is no reliable Linux tool for fixing the Winodws NTFS filesystem so you must use a Windows tool for best results.

-If in VirtualboxVM or External NTFS Harddrive
1) Boot up VM
1.5) If External Harddrive, Attach it to the VM using the Devices-->USB menu
2) Open CommandPrompt window and enter
```
chkdsk/?
```
This will bring up help on using the chkdsk command to repair the NTFS drive

-If Internal NTFS Partition you must boot into a Windows OS or Windows Recovery Disk and access a Command Prompt and run the chkdsk command.
If you don't have a Windows Installation or Windows Recovery Disk handy, Download and Burn the **Hiren's Boot CD** to Disk and run **MiniXP** from boot.
[http://www.hirensbootcd.org/download/]("http://www.hirensbootcd.org/download/")(Scroll to the Bottom of the Page for Download)

---

### Post by CharlesA on 2012-01-13
> **ethanova said:**
> I've got Win7 in a VirtualBox run as su on Ubuntu 11.04. When I had a program through Win7 save an mp3 file, it corrupted (I guess) the file. Nautilus doesn't recognize the file. I can see it with ls through terminal, and when I run 'll' instead of having permissions and the norm to the left of the file name, it just says ? ? ? ?. Also cannot chmod it, input/output error is returned. Any ideas on how to get this fixed?
 The "?" is because ls cannot determine the permissions of the file.

Is this on a non linux file system (NTFS, FAT)?

Also, why are you running VBox as "su" ? It shouldn't need to run with root privileges.

---

