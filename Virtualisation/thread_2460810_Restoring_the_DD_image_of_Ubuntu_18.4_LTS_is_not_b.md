---
title: "Restoring the DD image of Ubuntu 18.4 LTS is not booting up"
date: 2021-04-19
forum: Virtualisation
---

### Post by jinugc2 on 2021-04-19
I am new to Linux . I have received a DD image exported from a Linode Cloud to restore in a local VM. I have booted the VM with  ubuntu-18.04.5-desktop-amd64.iso live and restored to he disk with DD command . I am able to see all the files in the disk but the system is not getting booted .

---

### Post by DuckHook on 2021-04-19
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

### Post by CharlesA on 2021-04-19
> **jinugc2 said:**
> I am new to Linux . I have received a DD image exported from a Linode Cloud to restore in a local VM. I have booted the VM with  ubuntu-18.04.5-desktop-amd64.iso live and restored to he disk with DD command . I am able to see all the files in the disk but the system is not getting booted .

Are you able to see the file structure from the live environment after you restored the dd image?

---

### Post by jinugc2 on 2021-04-19
Yes , I am able to see the files and able to open by mounting the /dev/sda

---

### Post by CharlesA on 2021-04-20
> **jinugc2 said:**
> Yes , I am able to see the files and able to open by mounting the /dev/sda

That's good at least.

Do you already have /boot ?

If so, try running the procedure here:
[https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by jinugc2 on 2021-04-20
Sorry getting error .  
grub-install: Warning : File System 'ext2' doesn't support embedding
grub-install: Warning : Embedding is not possible. GRUB can only be installed in this setup by using blocklists . However, blocklist are UNRELABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists

I have tried [COLOR=#000000]boot-repair and the report is in [/COLOR]http://paste.ubuntu.com/p/HWcHTFb5jY/

---

### Post by CharlesA on 2021-04-21
How did you try installing grub?

Like this?

```
sudo grub-install /dev/sda
```

---

### Post by jinugc2 on 2021-04-21
I was used sudo su - before so i just use the grub-install /dev/sda

---

### Post by CharlesA on 2021-04-22
Do you know how the dd image was originally generated?

If you've already tried to reinstall grub that way, you could always try the old "tar everything and then restore it to a different drive"

It's a bit of a pain, but it might get your issue fixed.

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

