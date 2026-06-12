---
title: "Accessing Ubuntu from another Ubuntu"
date: 2013-02-21
forum: Virtualisation
---

### Post by SxN00 on 2013-02-21
Hi All,

I have the following setting: the HDD is split in two, first half is Windows 7, second half is Ubuntu (let's call it U1). In Windows I'm running a VirtualBox in which I have installed another Ubuntu - U2.

Problem: I'd like to mount U1's main partition in U2, but I can't seem to find it. It looks like U2 cannot see beyond himself and host. How can I go around this?

Thanks for your advice,
SxN

---

### Post by snowpine on 2013-02-21
Welcome to the forums!

I think what you are describing is impossible due to the "sandbox" nature of virtual machines.

---

### Post by SxN00 on 2013-02-21
:(

Thanks anyway, at least I know what not to search for

SxN

---

### Post by Melges on 2013-02-21
Hi, as i understand you want to access from virtual machine to real host disk partition. Maybe this [link]("http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software") helps you.

---

### Post by dcstar on 2013-02-22
> **SxN00 said:**
> Hi All,

I have the following setting: the HDD is split in two, first half is Windows 7, second half is Ubuntu (let's call it U1). In Windows I'm running a VirtualBox in which I have installed another Ubuntu - U2.

Problem: I'd like to mount U1's main partition in U2, but I can't seem to find it. It looks like U2 cannot see beyond himself and host. How can I go around this?


You use basic networked File Sharing in the Windows host - when you set it up for EXT4 support - and the U2 Ubuntu.

---

### Post by SxN00 on 2013-02-25
@Melges: checked the link, it refers to an older version of VirtualBox, of the Sun era. I was working on translating in Oracle terms, when I got the suggestion from dcstar.

@dcstar: inspired by your advice, I checked on the net for software that makes ext3/ext4 volumes available for Windows, and found ext2fsd. Installed and configured, also made the whole volume shared with U2 in VirtualBox. It's running now and, so far, works perfectly. I
Ext2fsd is offered cautiosly in write mode, but I had no problem yet writing (U2 wrote on U1).

Thanks for all your suggestions,
SxN

---

### Post by markbl on 2013-02-25
> **Melges said:**
> Hi, as i understand you want to access from virtual machine to real host disk partition. Maybe this [link]("http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software") helps you.
The link on how to do this in the current user manual is [https://www.virtualbox.org/manual/ch09.html#rawdisk](https://www.virtualbox.org/manual/ch09.html#rawdisk).

---

