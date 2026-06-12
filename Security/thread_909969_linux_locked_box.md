---
title: "linux locked box"
date: 2008-09-04
forum: Security
---

### Post by thevikas on 2008-09-04
Hi,

I have a apache+php+mysql site. I have been given the task to prepare a installed linux box which will run this site and also make sure that the data of this database/php should not be copied out of the system.

The problem is that the machine will not be physically in our control. The basic security has been placed so that you cannot login into the console without the right sequence of username/passwords. Beyond that I do not know much. Therefore for starters, the hard drive can be unplugged or a live cd can be used to mount into the filesystem (even though the machine did not come with a optical drive, one can still be wired in, booted along with easy bios changes).  I think getting into the system along with a privileged account using the linux login console is very low cause passwords will be "safe enough".

Another secondary problem is that the machine should not panic on sudden power-offs. Beyond that, I think linux and my site are stable enough. If the login prompt wants to fix the filesystem, it will have to do it by itself at next boot-time. No one from the tech will ever see the machine after it is sent to the destination.

I have read a few things about encrypted file systems. But never really seen them at work.

I need suggestions on what are the ways possible to do achieve the target. I have moderate knowledge of linux/ubuntu though Im a programmer myself.

Thanks a lot,
Vikas

---

### Post by hyper_ch on 2008-09-04
you can encrypt the box but as you do not have physical access to it it will be complicated.

---

### Post by cdenley on 2008-09-04
Anyone with physical access can get into your system. The best preventative measure you can do is encrypt everything. However, they can still retrieve encryption keys from memory if you leave your system running. Also, that would require you to have physical access to reboot for kernel updates, unless you somehow got an ssh server running before the encrypted partitions had to be mounted.

---

