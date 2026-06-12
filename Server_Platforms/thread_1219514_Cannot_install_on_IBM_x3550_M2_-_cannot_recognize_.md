---
title: "Cannot install on IBM x3550 M2 - cannot recognize CD-ROM"
date: 2009-07-21
forum: Server Platforms
---

### Post by alecm3 on 2009-07-21
I have a brand new IBM x3550 M2 server (Xeon 5500 series CPUs)  (released this April), which has some new SATA CD-ROM controller (in the UEFI, the BIOS replacement, it says something about emulating SATA as IDE, but there are no real settings to change any of this).

The installation of 8.04 Server LTS goes past the language, keyboard layout choice (which means it initially succeeds in reading from the CD-ROM), and then it says that it cannot mount CD-ROM after booting the kernel.
I tried various boot options, to no avail.

Do you have any ideas on how to install Ubuntu on this, before I try PXE install or SuSE which is officially supported on this hardware?

UPDATE: 8.04.1, 8.04.3 do not install, however 9.04 server INSTALLS!

Question: is 9.04 (with ReiserFS) stable for production? I would normally prefer LTS.

---

### Post by Vegan on 2009-07-22
I use the default ext3 which is the most widely used. It works fine for me so I have no reason for an alternative.

I use 9.04 and kernel 2.6.30 with no problems on my LAMP stack.

---

### Post by alecm3 on 2009-07-22
> **Vegan said:**
> I use the default ext3 which is the most widely used. It works fine for me so I have no reason for an alternative.

I use 9.04 and kernel 2.6.30 with no problems on my LAMP stack.

That's good news. Also, what does lack of LTS mean? Will apt-get stop working after 18 months?

Are you using it under heavy load? We will run single threaded custom Python TCP servers, 1 server per core, 8 servers per machine, with the average load average of 5.0 on the machine (out of 8.0 max), and our bottle necks are networking and CPU, not disk I/O.

---

### Post by dragos2 on 2009-07-22
> **alecm3 said:**
> 

Question: is 9.04 (with ReiserFS) stable for production? I would normally prefer LTS.

The author of reiserfs is in jail for murdering his wife, not that this should impact using the
filesystem exccept that its development hanged and it has some bugs.

I would not go with reiserfs in production, better use well tested ext3, jfs, xfs.

---

### Post by Tolaris on 2009-08-21
> **alecm3 said:**
> Do you have any ideas on how to install Ubuntu on this, before I try PXE install or SuSE which is officially supported on this hardware?

Sorry I got this to you late, but the easy solution is to transfer the install media to USB, and install from a USB key.  I have had a similar problem many times in the past 4 years of releases, either with servers that don't have an optical drive, or that exhibit the same boot/install/can't-mount-cdrom problem.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

The alternate/server installer can be a pain for this, as it will boot from USB, begin, and then STILL try to mount the cdrom!  The second link shows how to get around this.

---

