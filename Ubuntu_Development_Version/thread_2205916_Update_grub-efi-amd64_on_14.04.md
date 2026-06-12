---
title: "Update grub-efi-amd64 on 14.04"
date: 2014-02-16
forum: Ubuntu Development Version
---

### Post by medb2 on 2014-02-16
Can't update grub-efi-amd64 package on MacBook Pro.
Got the output
```
Setting up grub-efi-amd64 (2.02~beta2-6) ...
Installing for x86_64-efi platform.
grub-install: error: cannot open `/boot/efi/EFI/ubuntu/System/Library/CoreServices/boot.efi': No such file or directory.
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
  grub-efi-amd64
```

Actual path to boot.efi is ```
/boot/efi/System/Library/CoreServices/boot.efi
```

How to fix?

---

### Post by oldos2er on 2014-02-16
Moved to Ubuntu +1.

---

### Post by medb2 on 2014-02-18
I'm thinking to make symlink from /boot/efi/System/Library/CoreServices/boot.efi to /boot/efi/EFI/ubuntu/System/Library/CoreServices/boot.efi
But I'm think that better solution is to change grub configuration, but I don't know how to do this.

Any suggestions are welcome)

---

### Post by medb2 on 2014-02-21
I have asked the same question on askubuntu.com: [http://askubuntu.com/questions/423687/update-grub-efi-amd64-on-14-04](http://askubuntu.com/questions/423687/update-grub-efi-amd64-on-14-04)

---

### Post by Cavsfan on 2014-02-21
> **medb2 said:**
> I have asked the same question on askubuntu.com: [http://askubuntu.com/questions/423687/update-grub-efi-amd64-on-14-04](http://askubuntu.com/questions/423687/update-grub-efi-amd64-on-14-04)

I wish I could help you but I know nothing about a MacBook Pro. I wonder if you couldn't just install grub-pc instead of grub-efi-amd64.

I'm pretty sure it's up to you which one to go with but am not totally sure. You could check this out. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And this thread.

[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by ventrical on 2014-02-21
> **medb2 said:**
> I'm thinking to make symlink from /boot/efi/System/Library/CoreServices/boot.efi to /boot/efi/EFI/ubuntu/System/Library/CoreServices/boot.efi
But I'm think that better solution is to change grub configuration, but I don't know how to do this.

Any suggestions are welcome)

 Maybe to try and run at #root through recovery mode.

---

### Post by medb2 on 2014-02-22
Thanks for suggestions, but I'm able to boot into Ubuntu, I just can't upgrade the grub-efi-amd64 package.
I have filed bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1282918](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1282918)

---

### Post by medb2 on 2014-02-22
The previous error was because of the /boot/efi partition was mounted as read-only. After remounting it as read-write I have got the same error like in the [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1282375](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1282375)
```
Setting up grub-efi-amd64 (2.02~beta2-6) ...
Installing for x86_64-efi platform.
grub-install: error: Can't create file: No such file or directory.
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64

```

---

### Post by medb2 on 2014-02-22
I have come up with hacky solution: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1282375/comments/4](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1282375/comments/4)

---

