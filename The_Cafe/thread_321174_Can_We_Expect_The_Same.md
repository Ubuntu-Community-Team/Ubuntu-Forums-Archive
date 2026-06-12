---
title: "Can We Expect The Same?"
date: 2006-12-18
forum: The Cafe
---

### Post by spockrock on 2006-12-18
so it turns out apple OS X has ported over ZFS, for leopard.  [Read Me](http://loop.worldofapple.com/archives/2006/12/17/zfs-file-system-makes-it-to-mac-os-x-leopard/).  So I know there were plans on porting ZFS over to linux but when in the jazz can we expect it???  I would love to run the ZFS file system on Ubuntu.......

---

### Post by tageiru on 2006-12-18
> **spockrock said:**
> so it turns out apple OS X has ported over ZFS, for leopard.  [Read Me](http://loop.worldofapple.com/archives/2006/12/17/zfs-file-system-makes-it-to-mac-os-x-leopard/).  So I know there were plans on porting ZFS over to linux but when in the jazz can we expect it???  I would love to run the ZFS file system on Ubuntu.......

When Sun decides to release Solaris as GPL...

Linux can already do most of what ZFS is doing with LVM.

---

### Post by NESFreak on 2006-12-28
> **tageiru said:**
> When Sun decides to release Solaris as GPL...

Linux can already do most of what ZFS is doing with LVM.

someone is trying to make it work in userspace. i believe it was a summer of code project. This means it will be slow (read: not as fast as when compiled into the kernel) and your boot partition can't ever be zfs.

My hope is that someone will release kernelpatch so you can get ZFS yourself (or let let others build the kernel for you and dump it in the restricted repro and let you choose wat kernel to use at install)

Really want transparent file system compression. Saved me several GB on my ntfs partition. (in order to make more space free for ubuntu. Works perfect!) 

NESFreak

---

### Post by mbn18 on 2007-01-17
More info on the developer [_blog web site_]("http://zfs-on-fuse.blogspot.com/")

I hope it will be available soon. ZFS is a real revolution. :mrgreen:

---

