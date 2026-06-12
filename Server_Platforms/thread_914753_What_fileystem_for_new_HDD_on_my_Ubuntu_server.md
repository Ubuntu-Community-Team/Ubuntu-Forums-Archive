---
title: "What fileystem for new HDD on my Ubuntu server"
date: 2008-09-09
forum: Server Platforms
---

### Post by super_czar on 2008-09-09
Am planning to add a new 1TB HDD to my Ubuntu home server (which runs as a NAS, webserver and media repository and serves files to a Windows desktop, laptop and a macbook running OS X Leopard

I would prefer to backup my OS X via time machine to the NAS
What file format should I use on the new HDD so that it plays nice with all the devices

I can't use FAT32 since I have quite a few movies that exceed 8-9GB in size (single file)

Can ubuntu play well with HFS+, I would prefer to use HFS+ since my Mac will have an easytime backing up data onto it

---

### Post by Krupski on 2008-09-09
> **super_czar said:**
> Am planning to add a new 1TB HDD to my Ubuntu home server (which runs as a NAS, webserver and media repository and serves files to a Windows desktop, laptop and a macbook running OS X Leopard

I would prefer to backup my OS X via time machine to the NAS
What file format should I use on the new HDD so that it plays nice with all the devices

I can't use FAT32 since I have quite a few movies that exceed 8-9GB in size (single file)

Can ubuntu play well with HFS+, I would prefer to use HFS+ since my Mac will have an easytime backing up data onto it

To my knowledge, the FS used on your remote server is irrelevant since higher software layers (samba, apache, ftp, etc..) deal with the disk driver, not the low level drive itself.

That said, a while back I discovered that the XFS file system was faster than EXT3 and it also had much less overhead (i.e. more of the total disk was available as storage).

So, I asked "if XFS seems so much better, why does Ubuntu use EXT3?"

The answer I finally got was that EXT3 is more robust data integrity wise and recovers better from crashes and power losses.

So, in my NAS box I use the EXT3 file system.

Remember, bits are bits. It doesn't matter where they come from (a MAC, a PC or a C-64). If you write them, they will be recorded. If you read them, you will get them.

Hope this helps!

-- Roger

---

