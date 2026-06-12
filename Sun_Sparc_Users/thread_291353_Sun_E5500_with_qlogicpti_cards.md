---
title: "Sun E5500 with qlogicpti cards"
date: 2006-11-02
forum: Sun Sparc Users
---

### Post by lowen on 2006-11-02
Ok, trying out 6.10 on my E5500, which has three Sun Ultra Diff SCSI SBUS controllers, two D1000 drive shelves, and a mix of various SCSI drives.  All of this already works with Aurora Linux 2.0 (kernel 2.6.13-1.1603sp1smp), using the qlogicpti driver.  This driver is not on the list available during 6.10 server install.  As this box has no floppy drive, a floppy driver disk would be useless.  Any hopes for a respin with the qlogicpti SBUS card drivers built?  The CDROM on the esp controller was detected.

The box has eight processors, 8GB of RAM, and the three Qlogic PTI controllers.  dmesg output available upon request; as the drives number from /dev/sda through /dev/sdv, the dmesg is fairly long.:D 

I have an E6500 (10 CPU's and 6GB of RAM) with a 36G drive on the esp, so I'm going to try that, but it seems to me that a relatively common older controller like the diff SCSI card would be supported out of the box.

---

### Post by netztier on 2006-11-02
> **lowen said:**
> 

I have an E6500 (10 CPU's and 6GB of RAM) with a 36G drive on the esp, so I'm going to try that, but it seems to me that a relatively common older controller like the diff SCSI card would be supported out of the box.

In Dapper, the esp module was available, but was not loaded with the kernel from the CD-ROM. Right after first boot, one had to change to another tty and modprobe esp, then return and continue the installation. Then boot rescue, modprobe esp, chroot into the installed partition and rebuild an initrd.img with esp included. I think there is reason to believe that this is still so with 6.10.

See this [thread]("http://www.ubuntuforums.org/showthread.php?t=166882").

Maybe the process is the same with the controller in your 5500 and the qlogicpti module?

regards

Marc

---

### Post by lowen on 2006-11-02
Hmmm.  Now to figure out how to switch VC's through a remote serial console connection (telnet term server, Siteplayer Telnet, not a direct serial connect, and no framebuffer).  I'm not sure switching VC's is possible through a serial console; but I'm ok with being proven wrong on that.:)

---

### Post by lowen on 2006-11-02
Well, the only place the string 'qlogic' occurs in the initrd on the sparc ISO is in the SBUS list; there doesn't appear to be a kernel module listed.  I tried loopback mounting the initrd (on the E5500 running Aurora), but mount doesn't detect the filesystem type; and trying -t ext2 doesn't work.  What is the filesystem type of the installer's initrd?

---

### Post by netztier on 2006-11-02
[Double post deleted]

---

### Post by netztier on 2006-11-02
> **lowen said:**
> Well, the only place the string 'qlogic' occurs in the initrd on the sparc ISO is in the SBUS list; there doesn't appear to be a kernel module listed.  I tried loopback mounting the initrd (on the E5500 running Aurora), but mount doesn't detect the filesystem type; and trying -t ext2 doesn't work.  What is the filesystem type of the installer's initrd?

I'd doubt that you'll find the qlogicpti module in the initrd.img that is delivered on CD-ROM. I have no clue what type of file the initrd.img kernel is - well, it's a rudimentary kernel, after all.

My Suns are out of reach, so I can't tell for sure - if I were you, I'd start looking for esp and/or qlogicpti in **[FONT="Courier New"]/lib/modules/<kernel version>/drivers/scsi [/FONT]**(from memory...). If Auroralinux has this module, then why shouldn't Ubuntu? Probably all we need is to get the thing loaded at the right time.

regards

Marc

---

### Post by lowen on 2006-11-03
I've reported the lack of the Qlogic driver as a bug on Launchpad; it's now assigned and confirmed.  We'll see where it goes.

---

### Post by netztier on 2006-11-03
> **lowen said:**
> I've reported the lack of the Qlogic driver as a bug on Launchpad; it's now assigned and confirmed.  We'll see where it goes.

Good luck there :-)

I've just checked on my Ultra 5:

```

marc@fire:/lib/modules/2.6.15-27-sparc64/kernel/drivers/scsi$ ls -al
...
...
...
drwxr-xr-x  2 root root   4096 2006-09-30 19:22 qla2xxx
-rw-r--r--  1 root root 188034 2006-09-16 04:23 qlogicfc.ko
-rw-r--r--  1 root root  47775 2006-09-16 04:23 qlogicpti.ko
...
...

```

It's there, allright, on an installed box, that is. Checking when booting rescue from CD-ROM... it's not available. Raising a bug was the way to go, then. Adding **esp** wouldn't hurt either for Ultra 1 and Ultra2.

I think I'll add a comment...

[I]Edit: 
Better check the grounds I'm standig on before posting. Above was true in 6.06 (Dapper), but 6.10 (Edgy) has the **esp** module on the CD-ROM and loads it during setup. Havent' gone so far as to test if it also included in the first initrd.img that is installed during setup. So I'll keep shut for the moment.
[/I]

regards

Marc

---

### Post by lowen on 2006-11-03
The esp driver is loaded and available just fine on 6.10.  My other big test box, an E6500, has a disk board hanging off the esp on an I/O board, and it installed and boots fine.  It's a ten proc box with 7GB of RAM.

Now to get ssh X11 tunneling working....

---

### Post by netztier on 2006-11-15
> **lowen said:**
> Now to get ssh X11 tunneling working....

Er... Is there a lot more to it beyond running **[FONT="Courier New"]ssh[/FONT]** with the [FONT="Courier New"]**-X**[/FONT] parameter? 

And of course verifying that X11 forwarding is enabled in **[FONT="Courier New"]/etc/ssh/sshd_config[/FONT]** ?

regards

Marc

---

