---
title: "JFS Virtual Partition Mounting"
date: 2012-10-16
forum: Virtualisation
---

### Post by kronflux on 2012-10-16
I'm trying to set up a virtual JFS partition/image using the following tutorial:
( [http://maurits.tv/data/garrysmod/wik...index3761.html](http://maurits.tv/data/garrysmod/wik...index3761.html) )

I've already created the JFS image, however when I get to the mounting stage, the command is as follows:
"sudo mount -o rw,loop /root/test.img /mnt/test/"

and I get:

"mount: Could not find any loop device. Maybe this kernel does not know about the loop device? (If so, recompile or `modprobe loop'.)"

This is running on a Ubuntu Server 12.04 64-bit VPS.

I tried "modprobe loop" which gave me:

"WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module loop not found."

and under "/dev" I didn't see anything reflecting the name "loop"

I'm not very experienced with linux, so all of this is greek to me, but what I'm trying to do is to create a filesystem that isn't case sensitive, so that some addons for a GMOD gaming server will work correctly.

---

