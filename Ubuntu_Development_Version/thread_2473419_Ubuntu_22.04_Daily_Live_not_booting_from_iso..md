---
title: "Ubuntu 22.04 Daily Live not booting from iso."
date: 2022-04-04
forum: Ubuntu Development Version
---

### Post by kagashe on 2022-04-04
I am trying to boot Ubuntu 22.04 jammy-desktop-amd64.iso by inserting following menu in /etc/grub.d/40_custom
menuentry "Jammy Jellyfish Desktop iso" {
            set isofile="/home/user/jammy-desktop-amd64.iso"
            loopback loop (hd0,X)$isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
            initrd (loop)/casper/initrd
    }
I could not boot and getting the error:
Unable to find a medium containing a live file system.

I had checked the iso for sha256sum and found it ok.

I had downloaded the iso on last Saturday April 02.

I had used
```
zsync http://cdimage.ubuntu.com/daily-live/current/jammy-desktop-amd64.iso.zsync
```

but there are no updates to iso and it gives same error.

Kamalakar

---

### Post by ajgreeny on 2022-04-04
Was thar zsync command the full command you used, as it does not show the normal input and output file names that I always use to update an iso image file?

---

### Post by tstechster on 2022-04-04
I have the exact same problem!  No solution found yet!

---

### Post by kagashe on 2022-04-04
> **ajgreeny said:**
> Was thar zsync command the full command you used, as it does not show the normal input and output file names that I always use to update an iso image file?

The command I use is as per this [help page]("https://help.ubuntu.com/community/ZsyncCdImage") and it works.

By the way I downloaded [Ubuntu 22.04 Beta iso]("https://releases.ubuntu.com/jammy/ubuntu-22.04-beta-desktop-amd64.iso") and it does not boot and gives same error.

Kamalakar

---

### Post by ajgreeny on 2022-04-04
Ah, I see.

I use zsync to frequently update my xubuntu.iso image file already on my machine so I point the zsync command you used to an existing iso file with ```
zsync http://cdimage.ubuntu.com/xubuntu/daily-live/current/jammy-desktop-amd64.iso.zsync -i /path/to/file.iso -o /path/to/newfile.iso
```
This allows me to get a newer iso but download just the new parts of the file.

---

### Post by guiverc on 2022-04-04
I zsync my ISO using a script  (*it does a series of grep's on the manifest of the ISO & whatever I tested last time, before performing diffs so I have an idea of what differences there will be*); and my `zsync` command is

```
zsync -u http://cdimage.ubuntu.com/lubuntu/daily-live/current/jammy-desktop-amd64.iso  jammy-desktop-amd64.iso.zsync

```


Anyway, I added your 

```
menuentry "Jammy Jellyfish Desktop iso" {
   set isofile="/jammy-desktop-amd64.iso"
   loopback loop (hd0,2)$isofile
   linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
   initrd (loop)/casper/initrd
}
```

I assume you changed "**(hd0,X)**" to match your setup; for the box I used the X was a 2 you'll note  (*of no importance but I put the iso in /* *too; I don't want .iso files on my user directory backups*)

Anyway it starts to boot, but eventually gets to 

```
/init: line 49: can't open /dev/sr0: No medium found
```

Alas that's an error I've seen loads of times (*trouble reading the ISO*) but it's been a few cycles so I currently have nothing further..  I'll have to find the bug reports (*groovy? hirsute?*) when the ISO was varied a lot & this issue appeared somewhat regularly so I can refresh myself on potential issues & thus potential fixes.

---

### Post by oldfred on 2022-04-04
I usually have to umount the isodevice, it seems to always be mounted to the drive I want to install into and that complicates things

sudo umount -lrf /isodevice

I always change to the folder with my ISOs. I just noticed I am using pending not current.
zsync [http://cdimage.ubuntu.com/kubuntu/daily-live/pending/jammy-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/kubuntu/daily-live/pending/jammy-desktop-amd64.iso.zsync)

And I have been experimenting with configfile entry into the grub or loopback version in the ISO. But having errors when first starting to boot.
configfile /boot/grub/loopback.cfg

```
menuentry "Kubuntu 22.04 Jammy amd64 loopback.cfg" {
      iso_path=/ISO/jammy-desktop-amd64.iso
      export iso_path
      loopback loop $iso_path
      set root=(loop)
      configfile /boot/grub/loopback.cfg
    }


```

Edit/Update:
The error I get when I remove quiet splash to see boot process is near beginning of boot about 5.09 with my HDD and just after it seems to have mounted my partitions. Do not know then if a bad partition which I do not otherwise see, or next step in boot process.
stdin: invalid argument # & that keeps repeating forever.

---

### Post by zebra2 on 2022-04-05
Last week at beta I decided to upgrade my wife to Jammy.  My Iso would not zsysc. I had to zsync the entire iso.  Had to do clean install due to boot sector changes. I am pretty good at re-installs so no problem.

---

### Post by guiverc on 2022-04-05
> **zebra2 said:**
> Last week at beta I decided to upgrade my wife to Jammy.  My Iso would not zsysc. I had to zsync the entire iso.  Had to do clean install due to boot sector changes. I am pretty good at re-installs so no problem.

There have been problems with builds, and if the build doesn't complete successfully, all tests pass etc. - no new ISO update occurs.

I've been watching a discussion in a *development* room (IRC) this last hour in a window on another screen (*ignoring it mostly; above my pay grade!*) as to why... launchpad team says no issue they can fix; Canonical IS needs to fix etc... but it happens. Failures have been pretty regular of late, meaning teams have had to trigger a *manual rebuild* which means the ISO becoming available can be much later (*or not occur if the team didn't trigger the rebuild*)..

As for the install; you know you can *upgrade via re-install* easily.. ie. with no format, a note of your *manually installed *packages is made, system directories are wiped, new system installed, then your noted *manually installed* noted earlier are re-installed, without touching any user file.. ie. it's quick and easy, esp. if you're only using Ubuntu repository software.

Chances are you knew all this.. Posted just in case.

---

### Post by g-info-l on 2022-04-06
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/1960457](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/1960457)


> **guiverc said:**
> I zsync my ISO using a script  (*it does a series of grep's on the manifest of the ISO & whatever I tested last time, before performing diffs so I have an idea of what differences there will be*); and my `zsync` command is

```
zsync -u http://cdimage.ubuntu.com/lubuntu/daily-live/current/jammy-desktop-amd64.iso  jammy-desktop-amd64.iso.zsync

```


Anyway, I added your 

```
menuentry "Jammy Jellyfish Desktop iso" {
   set isofile="/jammy-desktop-amd64.iso"
   loopback loop (hd0,2)$isofile
   linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
   initrd (loop)/casper/initrd
}
```

I assume you changed "**(hd0,X)**" to match your setup; for the box I used the X was a 2 you'll note  (*of no importance but I put the iso in /* *too; I don't want .iso files on my user directory backups*)

Anyway it starts to boot, but eventually gets to 

```
/init: line 49: can't open /dev/sr0: No medium found
```

Alas that's an error I've seen loads of times (*trouble reading the ISO*) but it's been a few cycles so I currently have nothing further..  I'll have to find the bug reports (*groovy? hirsute?*) when the ISO was varied a lot & this issue appeared somewhat regularly so I can refresh myself on potential issues & thus potential fixes.

---

### Post by tstechster on 2022-04-16
Booting iso from grub works now!  (As of April 16, 2022). Still waiting for the xubuntu  iso to update, but the others seem to be working fine.  Thank you Canonical team!

---

### Post by kagashe on 2022-04-16
> **tstechster said:**
> Booting iso from grub works now!  (As of April 16, 2022). Still waiting for the xubuntu  iso to update, but the others seem to be working fine.  Thank you Canonical team!
Thanks. It works.

Kamalakar

---

