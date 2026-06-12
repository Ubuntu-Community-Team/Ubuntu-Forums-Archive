---
title: "Disk encryption &amp; backup"
date: 2010-02-10
forum: Security
---

### Post by Coco999 on 2010-02-10
I would like to backup the most important directories from my HD to another HD, or eventually data DVDs, in an encrypted manner. If possible not to do it file per file, but blocks of many directories or even a full partition. Ideally, retrieval  of single files is necessary. I need not security of the highest degree, but please avoid the simplest and more or less obvious encryptions. Thank you for your help.

---

### Post by tubbygweilo on 2010-02-10
Coco999, A directory full of Truecrypt encrypted files may well be the way to go as you can then copy the top level directory and all below will follow. You can then retrieve and decrypt any file held on your backup media with the added bonus that your backups are encrypted and safe from prying eyes. Just remember to backup your Truecrypt passphrase / key and keep it separate from your backuped  data. IIRC [Truecrypt]("http://www.truecrypt.org/docs/") cautions against encrypting at a partition level so I use it at a folder/file level and it works.

Some more advice from the docs;
> How to Back Up Securely

Due to hardware or software errors/malfunctions, files stored on a TrueCrypt volume may become corrupted. Therefore, we strongly recommend that you backup all your important files regularly (this, of course, applies to any important data, not just to encrypted data stored on TrueCrypt volumes).


Non-System Volumes

To back up a non-system TrueCrypt volume securely, it is recommended to follow these steps:

Create a new TrueCrypt volume using the TrueCrypt Volume Creation Wizard (do not enable the Quick Format option or the Dynamic option). It will be your backup volume so its size should match (or be greater than) the size of your main volume.

If the main volume is a hidden TrueCrypt volume, the backup volume must be a hidden TrueCrypt volume too. Before you create the hidden backup volume, you must create a new host (outer) volume for it without enabling the Quick Format option. In addition, especially if the backup volume is file-hosted, the hidden backup volume should occupy only a very small portion of the container and the outer volume should be almost completely filled with files (otherwise, the plausible deniability of the hidden volume might be adversely affected).

Mount the newly created backup volume.

Mount the main volume.

Copy all files from the mounted main volume directly to the mounted backup volume.

IMPORTANT: If you store the backup volume in any location that an adversary can repeatedly access (for example, on a device kept in a bank's safe deposit box), you should repeat all of the above steps (including the step 1) each time you want to back up the volume (see below).

If you follow the above steps, you will help prevent adversaries from finding out:

Which sectors of the volumes are changing (because you always follow step 1). This is particularly important, for example, if you store the backup volume on a device kept in a bank's safe deposit box (or in any other location that an adversary can repeatedly access) and the volume contains a hidden volume (for more information, see the subsection Security Requirements and Precautions Pertaining to Hidden Volumes in the chapter Plausible Deniability).

That one of the volumes is a backup of the other.


---

### Post by Viper187 on 2010-02-10
I've been wondering about this, myself. I have an encrypted softraid setup for my data, but I've never found a decent method of backing up to optical media. The amount of DVDRs I'd need is getting absurd anyway, but I've been thinking about BD-R since I don't really trust HDDs anymore. I know a guy that had 2 drives on his RAID5 die within a couple hours of each other. Anyway, an encrypted partition has been more convenient for my purposes. I just haven't heard of any way to build a DVD image with an encryped partition instead of having to encrypt files individually.

---

### Post by DZ* on 2010-02-10
I use external drives encrypted with LUKS for backups. Here's how to prepare the drive
(assuming it is /dev/sdc1).

```
WillTrash='/dev/sdc1'
umount $WillTrash
# dd if=/dev/urandom of=$WillTrash ## some recommended this
cryptsetup luksFormat $WillTrash
cryptsetup luksOpen $WillTrash dsk
mkfs.ext3 /dev/mapper/dsk
cryptsetup luksClose dsk
WillTrash='/dev/null'
```

Then simply stick it in and you'll be prompted for a passphrase, or you can mount it manually as 
```
cryptsetup luksOpen /dev/sdc1 cmnt; mount /dev/mapper/cmnt /media/disk
```

You can do this with DVDs as well:
[http://www.ai.wu.ac.at/~aweichse/manual/encrypted_dvd/](http://www.ai.wu.ac.at/~aweichse/manual/encrypted_dvd/)

---

### Post by Coco999 on 2010-02-13
Thank you for your help. I've installed Truecrypt and am in the process to study it. Alternatively, I also have the suggestion of LUKS. I'm closing the thread as solved.

---

