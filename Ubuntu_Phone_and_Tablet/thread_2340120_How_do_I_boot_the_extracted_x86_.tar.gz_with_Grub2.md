---
title: "How do I boot the extracted x86 .tar.gz with Grub2?"
date: 2016-10-15
forum: Ubuntu Phone and Tablet
---

### Post by T2uiYKb7 on 2016-10-15
[B]Edit: Done some more snooping and I seems it's intended to be installed on Android devices* (despite saying the opposite on the download page.) *The boot and recovery .img files can't easily be installed on a UEFI x86 tablet intendd for Windows. [COLOR=#008000]I'm guessing I can use a Grub entry that point's to certain files (kernel, initrid)  to boot it?[/COLOR] I already have (EFI) Grub booting off my 1st partition of my tablet.
[/B]
> [http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/)

" 32-bit PC (i386) preinstalled touch image

For  almost all PCs. This includes most machines with Intel/AMD/etc type  processors and almost all computers that run Microsoft Windows, as well  as newer Apple Macintosh systems based on Intel processors. "

  etc.
So it has all the same support and the desktop 16.10 version? The same kernel drivers etc.? More touch, sound drivers typically used on Atom/Core M tablets?
 
Can I exract/dd it to a partition then boot it from Grub?

It's just strange that it says ***"almost all computers that run Microsoft Windows" ***yet it doesn't have boot/efi files or an installer.

---

### Post by T2uiYKb7 on 2016-10-22
[SIZE=3][COLOR=#008000]How can  I boot yakkety-preinstalled-touch-i386.tar.gz with Grub2?[/COLOR][/SIZE]

If I extract it to an .ext3 partition then from my small Grub2 FAT32 partition add an entry too grub.cfg will it boot?

Something similar to.

```
menuentry 'Ubuntu Touch i386' 

    search --no-floppy --fs-uuid --set=root enter-UUID-here
    
    linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=enter-UUID-here
    initrd    /boot/initrd.img-4.4.0-31-generic
```

---

### Post by krusty8 on 2016-10-22
I don't know the answers to your questions about those tar.gz files, but if your actual goal is to get ubuntus touch experience on your PC then it might be easier to install the necessary packages from within your normal ubuntu desktop installation. See, e.g. [https://bregmatter.wordpress.com/2016/07/04/previewing-the-new-unity/](https://bregmatter.wordpress.com/2016/07/04/previewing-the-new-unity/)
Maybe it has become even easier since then. Maybe no ppa required anymore. Now that I think about it didn't they say they even include it out of the box in the just released 16.10 version? 
Keywords, other than Ubuntu Touch, you'll want to look out for are Unity8 and Mir.

---

