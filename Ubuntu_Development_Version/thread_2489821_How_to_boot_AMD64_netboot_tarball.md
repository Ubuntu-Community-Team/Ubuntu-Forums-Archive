---
title: "How to boot AMD64 netboot tarball"
date: 2023-08-10
forum: Ubuntu Development Version
---

### Post by jagsdesai on 2023-08-10
I am trying to test install Ubuntu from this **AMD64 Netboot tarball** found on this page: [http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/)

There used to be `Mini ISO` but now there's a 133MB file: `mantic-netboot-amd64.tar.gz`

Edit: When I extract the tar.gz file, I get these files:
```
grub (Directory with one file: `grub.cfg`)
pxelinux.cfg (Directory with one file: `default`)
bootx64.efi
grubx64.efi
initrd
ldlinux.c32
linux
pxelinux.0
```

So, how can I boot this tarball through KVM virtual manager... do I have to convert this into ISO first?  Thanks.

---

### Post by grahammechanical on 2023-08-10
I have never experimented with this method of installing. I do understand that I tarball is a compressed file. Try putting the tarball into a folder and de-compressing it. You may end up with an image file that can be burnt to a USB memory stick..

Regards

---

### Post by jagsdesai on 2023-08-10
> **grahammechanical said:**
> Try putting the tarball into a folder and de-compressing it. You may end up with an image file that can be burnt to a USB memory stick..

Regards

Guess I wasn't clear enough. When I extract the tarball file: `mantic-netboot-amd64.tar.gz`, instead of any image file, I get files as listed in my original post. Thanks.

---

### Post by jagsdesai on 2023-08-10
I just found an option to boot directly from kernel in kvm virtual manager. But it's just gonna download a complete ISO from [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

So it's not like what `Mini ISO` used to be, where you can select packages to install.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292584&stc=1[/IMG]

---

