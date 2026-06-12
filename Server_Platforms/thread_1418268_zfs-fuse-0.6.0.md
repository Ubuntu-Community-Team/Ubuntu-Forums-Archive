---
title: "zfs-fuse-0.6.0"
date: 2010-02-28
forum: Server Platforms
---

### Post by kachaffeous on 2010-02-28
Built zfs-fuse from source for my home server.  Figured I would share.

zfs-fuse-0.6.0  for Ubuntu 9.10

First time doing this so no guarantees, but it works on my box.  This allows updating to zpool version 16.

[http://www.mediafire.com/file/z52hmttmdmg/zfs-fuse_0.6.0.deb](http://www.mediafire.com/file/z52hmttmdmg/zfs-fuse_0.6.0.deb)

---

### Post by tyn on 2010-03-12
Was it as easy as the zfs-fuse website suggests it is?  I'm running on a usb stick install of xubuntu 9.10 (AMD64) so I'm not entirely sure that I have any compilers/development utilities.

This is what the zfs website says ([http://zfs-fuse.net/):](http://zfs-fuse.net/):)
> 
1. Install the required dependencies (libaio, libattr, libacl, libz, SCons, the FUSE libraries, and all development packages associated to these libraries).

sudo apt-get install libaio-dev libattr1-dev libacl1-dev libz-dev libz-dev libfuse-dev libfuse2 scons libssl-dev

2. Download the latest stable source release from this page.

3. Compile by uncompressing the source release, and running the command scons in the directory where the uncompressed files reside.


---

