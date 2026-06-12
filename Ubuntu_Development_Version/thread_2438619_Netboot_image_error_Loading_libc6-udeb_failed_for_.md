---
title: "Netboot image error Loading libc6-udeb failed for unknown reasons. (Focal)"
date: 2020-03-15
forum: Ubuntu Development Version
---

### Post by victor-jon on 2020-03-15
Hi,

I am using focal netboot image from [here]("http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/images/netboot/"), It is loading directly from hard-disk as described [URL="https://askubuntu.com/questions/1025656/how-do-i-boot-an-iso-file-from-my-drive-using-grub2-on-uefi-machines"]here
[/URL]

This is content of **/etc/grub.d/40_custom**

```
menuentry "Net Install 20.04" {
        linuxefi (hd1,gpt10)/Downloads/ubuntu-installer/amd64/linux
        initrdefi (hd1,gpt10)/Downloads/ubuntu-installer/amd64/initrd.gz
}
```

After rebooting and selecting it starts the installation, but at partition disk it throws following error:

```
[LEFT][COLOR=#333333][FONT=monospace]Failed to load installer component[/FONT][/COLOR][COLOR=#333333][FONT=monospace]
Loading libc6-udeb failed for unknown reasons. Aborting.[/FONT][/COLOR][/LEFT]

```

I also tried with mini.iso from usb, but the error persists.

Any clue how to fix that ?

Thanks.

---

### Post by sudodus on 2020-03-15
I get that error too, but have not had the energy too create a bug report; I am only waiting for a new and working version.

By the way, I tested the current Ubuntu Server daily iso file (yesterday, 2020-03-14 , when the current focal mini.iso was dated 2020-03-10) and Ubuntu Server works.

If you write a bug report, please post a link to it, and I will click on 'affects me too' in order to confirm it.

---

### Post by dino99 on 2020-03-15
Possibly a gpt/uefi problem
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

---

### Post by victor-jon on 2020-03-15
Thanks. I found [this]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1867502") bug on launchpad. I will try with server image.

---

### Post by Irihapeti on 2020-03-15
I encountered the same problem and I've marked myself as affected by the bug. If others could also do this, it could be helpful.

---

### Post by sudodus on 2020-03-15
@victor-jon,

Thanks for the link. I have marked myself as affected by the bug.

Good luck with the Ubuntu Server image.

---

### Post by deadflowr on 2020-03-15
Probably fallout from this bug:
[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1867431]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1867431")

---

