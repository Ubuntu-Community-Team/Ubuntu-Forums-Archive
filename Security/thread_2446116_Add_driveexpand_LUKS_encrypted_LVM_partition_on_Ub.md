---
title: "Add drive/expand LUKS encrypted LVM partition on Ubuntu Server 20.04"
date: 2020-06-25
forum: Security
---

### Post by learning-linux on 2020-06-25
I  have an Ubuntu 20.04 server that currently has an LVM comprising 2 1tb  hard drives that is LUKS encrypted. I just put a new 3tb drive in as  well, and need to expand the LVM to encompass the new drive. I don't  have the ability to image it as I have no spare media large enough, so I'm hoping I can expand the existing  LVM rather than creating a new one. 

  I don't have anything super important on it, so if worst case happens  and I lose anything, all I'm out is quite a few hours of work getting  everything setup; but I'd prefer to not have that happen, obviously.

---

### Post by TheFu on 2020-06-25
I'm not certain that LUKS container decryption can be caused across multiple storage devices. That will be the challenge, I think. That would mean that the VG wouldn't see all the storage in the VG simultaneously.

Please post some facts.  Connect all the storage you want to use.
[LIST]
[*]sudo lvs
[*]sudo vgs
[*]sudo pvs
[*]lsblk -e 7 -o name,size,type,fstype,mountpoint
[*]sudo fdisk -l
[/LIST]

Please use _code tags_, so the columns line up here (forums) as they do in the terminal.

Found this from 2014: 
> The usecase of one passphrase across multiple hard-disks is strange, and is akeen of "master passphrase". Typically one should use different passphrases for each LUKS volume. If you have multiple disks, which are utilised as a single system, it's best to e.g. use RAID or LVM (as appropriate e.g. RAID0 level, non-replicated VG/LV ) first to create a single block devices our of multiple physcial hard-drives, and then encrypt that as a single LUKS encrypted volume with one passphrase. This way, user is only asked for decryption passphrase once for the single encrypted volume that there is in that system.

[https://github.com/rioderelfte/multi-luks](https://github.com/rioderelfte/multi-luks) seems related.

I should say that in my early years with LVM, I lost 80% of my data spanning a VG across 3 drives when 1 of those drives failed.  OTOH, that loss convinced me to get backup religion, so I've not had any big data loss since then.

How are you doing backups?  Screwing with this sort of stuff can cause data loss.  Definitely try whatever you are planning in a VM with a few fake HDDs connected.  Were it me, I'd keep the OS and data VGs separate. That way I could make the data mounts happen well after boot.

Sorry, no real answer from me.

---

