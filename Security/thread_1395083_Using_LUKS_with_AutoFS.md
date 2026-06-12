---
title: "Using LUKS with AutoFS?"
date: 2010-01-31
forum: Security
---

### Post by m00dawg on 2010-01-31
I finally figured out how to make sure I can mount my eSATA LUKS encrypted drive without having to run 'fdisk -l' to figure out which device it is (hint: use /dev/disk-by-uuid) but I still have to manually run 'cryptsetup luksOpen ...' when I want to use the drive.

The drive is for backups of my home NAS so I consider the NAS to be trusted and, as a result, I would like to automatically mount the drive when I connect it. I know AutoFS can be setup to run scripts but I have found no clear documentation on how to do this with LUKS/cryptsetup. Right now, I have a BASH script that does the work of mounting the drive but it would be nice to use the drive in a more direct manner.

On an aside, I also find that 'cryptsetup luksOpen ...' often hangs the first time I run it, and does not allow me to CTRL-C out of it. I have to start another copy of my backup script before things work. Very odd.

This is on all Ubuntu 0.94. Any help would be much appreciated!

---

