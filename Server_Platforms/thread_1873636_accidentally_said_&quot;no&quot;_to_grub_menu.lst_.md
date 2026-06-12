---
title: "accidentally said &quot;no&quot; to grub menu.lst replacement"
date: 2011-11-01
forum: Server Platforms
---

### Post by Wej on 2011-11-01
Hello,

I have been working through some upgrades of a 9.04 server, trying to get it to 10.04 at least. I am trying to do this without having to wipe anything out and reload it, due to it being somewhat critical of a system.

I followed a tutorial on how to use the old-version repositories to get it upgraded from 9.04 to 9.10, and everything seems good, except when I did the apt-get dist-upgrade, I accidentally said "no" to replace my grub's menu.lst file. Now it still boots the old kernel, even though it has a newer kernel installed. What do I need to do to have it ask me to replace the menu.lst file again, but this time I can say yes? Does grub-mkconfig apply to this? I ran it without parameters, it dumped to the console, but the format looked wrong for a menu.lst file. Here is the pertinent part of my current menu.lst:
```

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-11-server (/dev/sda)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-11-server root=/dev/md0 ro quiet splash vga=773
initrd          /boot/initrd.img-2.6.28-11-server

title           Ubuntu 9.04, kernel 2.6.28-11-server (/dev/sdb)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.28-11-server root=/dev/md0 ro quiet splash vga=773
initrd          /boot/initrd.img-2.6.28-11-server

title           Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-11-server root=/dev/md0 ro  single
initrd          /boot/initrd.img-2.6.28-11-server
```

One thing I am not sure about is what kernel it downloaded. I thought it said it was a generic PAE kernel, which seemed strange, considering I am upgrading from a server specific kernel. I have a few different linux-image* files in my archives:
```

linux-image-2.6.31-23-generic-pae_2.6.31-23.75_i386.deb
linux-image-generic-pae_2.6.31.23.36_i386.deb
linux-image-server_2.6.31.23.36_i386.deb
```

Note: My current version of grub says it is 0.97; I don't want to install Grub2 on the system.

Thanks

---

### Post by darkod on 2011-11-01
As far as I know, only since grub2 menu.lst was made obsolete and grub.cfg started to get used.

If you don't want to move to grub2, grub1 works only with menu.lst AFAIK.

On the other hand, the "offer" to replace menu.lst happens when grub2 is installed. Are you sure you don't have it? Or you do have it just not wanting to use it?

If you simply don't want to use grub2 even if it's installed, just make a new entry in your menu.lst for the latest kernel and that's it. With menu.lst it works the old way, editing directly the file.

And for every new kernel you would have to do it manually.

Grub2 and grub.cfg can auto update with the latest kernel so you don't need manual editing, but that's another topic if you are not using it.

---

