---
title: "Apple shuts down ZFS open source project"
date: 2009-10-24
forum: The Cafe
---

### Post by CoreyB. on 2009-10-24
From [AppleInsider]("http://www.appleinsider.com/articles/09/10/23/apple_shuts_down_zfs_open_source_project.html").

---

### Post by Vadi on 2009-10-24
apple is awesome! buy apple! best products ever!

;)

---

### Post by DeadSuperHero on 2009-10-24
The title seems a little misleading. As far as I'm concerned, ZFS still exists for FreeBSD and OpenSolaris.

---

### Post by jrothwell97 on 2009-10-24
Well, it's certainly intriguing: Oracle's purchase of Sun and the NetApp patent lawsuit were probably both contributing factors.

Obviously, it's a shame, but I think the cloud may have a silver lining: Apple are obviously unhappy with HFS, and since they're now [hiring file system engineers](http://jobs.apple.com/index.ajs?method=mExternal.showJob&RID=42559), it's pretty obvious they'll be working on their own next-generation file system.

This may be a better thing than it seems: Apple has a history of open-sourcing things like libzeroconf and libdispatch under permissive open-source licenses. The obvious advantage of this is that it could be ported to the Linux kernel space without the GPL/CDDL-related mangling ZFS had, and could also be ported to proprietary operating systems without similar GPL-linking-clause-related mangling that would plague porting, say, the ext2/3/4 and btrfs file systems to Windows.

Of course, I could be wrong and they could end up turning it into a monolithic proprietary hunk: however, considering Apple's track record on technologies like this, their new file system could turn out to be very beneficial indeed.

---

### Post by chris200x9 on 2009-10-24
> **jrothwell97 said:**
> 
This may be a better thing than it seems: Apple has a history of open-sourcing things like libzeroconf and libdispatch under permissive open-source licenses. The obvious advantage of this is that it could be ported to the Linux kernel space without the GPL/CDDL-related mangling ZFS had, and could also be ported to proprietary operating systems without similar GPL-linking-clause-related mangling that would plague porting, say, the ext2/3/4 and btrfs file systems to Windows.
.


I was just wondering, is that even possible technically? Porting to windows I mean, I thought linux/bsd/solaris/mac could pretty much *share* filesystems because they were *nix not because of licensing issues.

---

### Post by jrothwell97 on 2009-10-24
> **chris200x9 said:**
> I was just wondering, is that even possible technically? Porting to windows I mean, I thought linux/bsd/solaris/mac could pretty much *share* filesystems because they were *nix not because of licensing issues.

In theory, it's perfectly possible to write an ext2/3/4 driver for Windows (it'd be handled in the same way as the NTFS and FAT drivers). The problem lies in the fact the GPL does not allow linking GPL-licensed code with proprietary code, which makes creating a kernel-space driver a legal grey area.

The alternative is to create a user-space driver, but the problems with that are numerous: first, it'd be achingly slow, and secondly, it couldn't be used as a boot partition.

---

### Post by hessiess on 2009-10-24
Why apple is abandoning ZFS is beyond me, its miles ahaid of any outer file system.

---

### Post by Bachstelze on 2009-10-24
> **hessiess said:**
> Why apple is abandoning ZFS is beyond me, its miles ahaid of any outer file system.

Ever heard of BTRFS?

---

### Post by hessiess on 2009-10-24
> **Bachstelze said:**
> Ever heard of BTRFS?

Yes, but it is still in development, ZFS on the other hand is finished.

---

### Post by schauerlich on 2009-10-24
> **hessiess said:**
> Why apple is abandoning ZFS is beyond me, its miles ahaid of any outer file system.

Patent issues. Sun owns the patents on ZFS, but they just got bought by Oracle. Oracle develops btrfs, which means they'll probably shut down ZFS themselves. Apple doesn't want to take on the primary developer role.

> **Bachstelze said:**
> Ever heard of BTRFS?

It's GPL'd, which Apple tends to stay away from because of all the linking issues.

---

### Post by ssam on 2009-10-24
licensing does not stop people porting file systems. you can re-implement any filesystem in any license for any OS. this how linux supports FAT and HFS.

it does slow you down though, as you can just copy and paste the code from the other OS.

---

### Post by schauerlich on 2009-10-24
> **ssam said:**
> licensing does not stop people porting file systems. you can re-implement any filesystem in any license for any OS. this how linux supports FAT and HFS.

it does slow you down though, as you can just copy and paste the code from the other OS.

Apple isn't willing to rely on a hacky, reverse engineered filesystem.

---

### Post by HappinessNow on 2009-10-24
> **EDavidBurg said:**
> Apple isn't willing to rely on a hacky, reverse engineered filesystem.Isn't that exactly what Apple is built on?

---

### Post by NCLI on 2009-10-24
Can someone more patient than me *please *post [here]("http://www.engadget.com/2009/10/24/zfs-open-source-project-abruptly-shuts-down-snow-leopard-weeps/") and explain that the ZFS project being shut down has nothing to do with it being Open Source, and that, in fact, it will most likely live on *because *it's open source, and the community will be able to maintain it?

---

### Post by schauerlich on 2009-10-24
> **&#20170 said:**
> Isn't that exactly what Apple is built on?

No.

[http://en.wikipedia.org/wiki/HFS%2B](http://en.wikipedia.org/wiki/HFS%2B)

---

### Post by ssam on 2009-10-25
> **EDavidBurg said:**
> Apple isn't willing to rely on a hacky, reverse engineered filesystem.

doesn't have to be a hacky reverse engineering job if you have the specifications to the file system.

---

### Post by schauerlich on 2009-10-25
> **ssam said:**
> doesn't have to be a hacky reverse engineering job if you have the specifications to the file system.

The HFS+ specification is open, and the Linux driver for it still sucks. And anyways, even if Apple wanted to reimplement ZFS from scratch, the technology itself is patented, meaning they could still be sued.

---

