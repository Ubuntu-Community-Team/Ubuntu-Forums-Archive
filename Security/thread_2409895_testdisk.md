---
title: "testdisk"
date: 2019-01-08
forum: Security
---

### Post by mcyber4 on 2019-01-08
Hi 
as expected there seems to be a rootkit in hidden/unwritable sections of the hd. testdisk finds misaligned sectors etc. and says disk to be smaller than indicated.
Formatting with gparted or win10 doesn't solve this.
Any way to completely format a hd with testdisk?
Thanks

---

### Post by SeijiSensei on 2019-01-08
You could try zeroing the device, then trying gparted again.  I think testdisk lets you open a shell.  If so,

```
dd if=/dev/zero of=/dev/sda bs=1M
```

will write zeroes to the entire device /dev/sda. (Replace "/dev/sda" with the identifier for the disk you're trying to reformat.}

Don't know whether that will cure your problem.

This will take a while.

---

### Post by yetimon_64 on 2019-01-08
> **SeijiSensei said:**
> You could try zeroing the device, then trying gparted again.  I think testdisk lets you open a shell.  If so,

```
dd if=/dev/zero of=/dev/sda bs=1M
```

will write zeroes to the entire device /dev/sda. (Replace "/dev/sda" with the identifier for the disk you're trying to reformat.}

Don't know whether that will cure your problem.

This will take a while.
@OP, running the above command is often referred to a "factory reset" and will completely reset a drive including boot/hidden sectors. On reading your post it is exactly what I'd try to use in this sort of situation.

> Any way to completely format a hd with testdisk?
If testdisk **can't** open a root shell you can use this command from a terminal with the sudo command eg. ```
sudo dd if=/dev/zero of=/dev/sda bs=1M
```
I have often used this particular command from a live cd terminal to totally reset a drive when partitioning problems have occurred. Though I've never experienced your particular problem regarding rootkits. 

**Important notes** ...
It is important, if you use the above command, to **BACK UP** any needed data on the drive to a separate drive, **including if present any EFI partition data**. The above command used on a drive **will erase everything**.
As SeijiSensei notes ... > Replace "/dev/sda" with the identifier for the disk you're trying to reformat ... that is, **ensure you write to the correct device**. 

I have had such resets on occasions take 8 to 10 hours to complete on large HDDs (1 TB and larger). One particular 1TB drive reset on a USB2 external dock took 4 days (](*,)); if you use an external dock, make sure it is USB3 or eSATA etc.

 Once complete you will have to use gparted and install a new boot sector for the drive and rebuild your partition scheme before you will be able to do any further formatting etc.

> Don't know whether that will cure your problem. Same here ... though I suspect it will from my experience using that command.

---

### Post by mcyber4 on 2019-01-10
No luck, same as with Windows low level format app.

ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=1M
dd: error writing '/dev/sda': No space left on device
476941+0 records in
476940+0 records out
500107862016 bytes (500 GB, 466 GiB) copied, 949.542 s, 527 MB/s
ubuntu@ubuntu:~$

---

### Post by SeijiSensei on 2019-01-10
That's not an indication of an error, just that it reached the end of the device.  It appears to have written 500 GB of zeroes.  Did you try formatting it?

---

### Post by mcyber4 on 2019-01-11
As I've written above I have formatted it many times/ways.
dd and other low level formatters only wrote 465gb of 500gb
But funny enough I now see when the rootkit kicks in by having 3 items in .gnupg. If I disconnect/reboot the live cd there's only one item in ~.gnugp
That rootkit was made by a stinky, bold monkey as it infects most touched objects and anything written to usb devices.
But those that pay are as dumb.
I'll send in the drive as it's still on warranty.

---

