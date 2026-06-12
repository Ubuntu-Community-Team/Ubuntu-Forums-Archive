---
title: "How to use ZFS in Ubuntu Studio 14.04?"
date: 2015-12-13
forum: Ubuntu Studio
---

### Post by sethanath2 on 2015-12-13
Hi,

I want to try using ZFS in Ubuntu Studio 14.04?
I also want to know if ZFS would be good for me since I am using my Linux for playing games too, plus VLC and surfing the internet.
Do you think that ZFS would work well with Thunar, Wine, PlayonLinux, and pretty much anything else?
Do you think that Ubuntu Studio would give me the option to use ZFS during the installation in the near future?

Can you let me know the steps to use ZFS in Ubuntu Studio?

Thanks.

---

### Post by sethanath2 on 2015-12-13
Now, I also heard that by doing so, my PC would use more electricity. What else can come with it, though?

---

### Post by lukeiamyourfather on 2015-12-21
ZFS is fairly resource hungry and it will use as much memory as it is allowed to. It's typically used for file server or NAS applications where the machine doesn't have a lot of user applications to compete with. It can be used on a desktop or workstation with a few tweaks like limiting how much memory the ARC can use. There's information about setting it up on Ubuntu on my blog.

[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

Keep in mind that ZFS requires ECC memory! If it's a typical desktop computer it's not going to have ECC memory.

---

### Post by sethanath2 on 2015-12-21
> **lukeiamyourfather said:**
> ZFS is fairly resource hungry and it will use as much memory as it is allowed to. It's typically used for file server or NAS applications where the machine doesn't have a lot of user applications to compete with. It can be used on a desktop or workstation with a few tweaks like limiting how much memory the ARC can use. There's information about setting it up on Ubuntu on my blog.

[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

Keep in mind that ZFS requires ECC memory! If it's a typical desktop computer it's not going to have ECC memory.

Thanks for your help.

---

### Post by yoshii on 2015-12-25
I have had good results with ext3 as the filesystem.  And I know older versions of puppy linux used ext2 which can be installed without encryption.  For some things ext2 might be faster, but ext3 is probably more stable because of the journaling.  ext4 is newer but it has some issues with risk of data loss because it's journaling works differently than ext3.  Luckly some systems where ext4 or ext2 are the default still work with ext3.

I used to use FAT32 for compatibility with some old Windows recovery programs and stuff but I switched to ext when I got rid of Windows completely.  I know that NTFS is discouraged for some distros.

---

### Post by lukeiamyourfather on 2015-12-29
You should do some research on ZFS. It's not at all like any of the file systems you listed and uses fundamentally different design approaches. It's like someone asking about hybrid cars and responding with information about a Ford Model T. If you've switched over to Linux completely at this point it might be very useful to you.

---

### Post by matt_symes on 2015-12-29
Hi

I heard a rumour that zfs may be included as a filing system on Ubuntu 16.04 and not just a technological preview. The kernel module may be built using dkms if it's not included as a module by default. This may well cause problems for some people if the kernel module does not build for some reason.

The way PC-BSD does boot environments using zfs is fantastic.

Copy on write, snapshotting filing systems are the way forward and it's just a shame BTRFS is not in the same league yet.

Kind regards

---

### Post by jlparsons on 2016-01-23
> **lukeiamyourfather said:**
> Keep in mind that ZFS requires ECC memory! If it's a typical desktop computer it's not going to have ECC memory.

Hasn't this been debunked?  Source: [http://jrs-s.net/2015/02/03/will-zfs-and-non-ecc-ram-kill-your-data/](http://jrs-s.net/2015/02/03/will-zfs-and-non-ecc-ram-kill-your-data/)

Conclusion was:

"“Authority” in this case doesn’t get much better than Matthew Ahrens, one of the cofounders of ZFS at Sun Microsystems and current ZFS developer at Delphix. In the comments to one of my filesystem articles on Ars Technica, Matthew said “There’s nothing special about ZFS that requires/encourages the use of ECC RAM more so than any other filesystem.”"

Don't shoot the messenger, I have no freaking clue either way. :D

---

### Post by yoshii on 2016-01-23
@luke:  I realise that some of these newer filesystems are advanced.  I wasn't disputing that.  It's just that for some applications, such as audio or video recording require the minimum amount of resource usage.  So using an older filesystem is not necessarily a bad choice if you need something based more on speed and basic stability rather than advanced forms of journaling and sophisticated forms of file management.  And yes, I have read a little bit about ZFS.  And it didn't convince me to install it instead of the conventional and oldish ext3.  Besides, if you live on the cutting edge, you bleed on it too.

---

