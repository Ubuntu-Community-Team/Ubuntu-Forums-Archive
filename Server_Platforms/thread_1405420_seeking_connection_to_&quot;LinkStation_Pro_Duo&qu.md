---
title: "seeking connection to &quot;LinkStation Pro Duo&quot; NAS"
date: 2010-02-12
forum: Server Platforms
---

### Post by SaintDanBert on 2010-02-12
I run Ubuntu Karmic on various laptops and need to connect to "shares" that live on a Buffalo Technologies "LinkStation Pro Duo" NAS. Has anyone made this work and have wise words to share?

(Okay, you can stop screaming and running from the room.)

I see from their PDF manual, that the drives are either EXT3 or XFS formatted (glimmer of hope) and that both FTP (ugh) and SMB (hmmm) protocols are supported. I hope that someone has found a way to use NFS or other cloud-like facility to use storage on these boxes.

I know that SMB means that I would use SAMBA from the linux side of things. I currently have all sorts of troubles at home trying to SAMBA among my family mix of win-XP, win-Vista, and win-7. If there is a good SAMBA thread -- that doesn't require a full time job -- please pass that along too.

Cheers,
~~~ 0;-Dan

---

### Post by gordintoronto on 2010-02-12
First, you need to make sure all your computers have the same workgroup.  If you change it, reboot!

Then: select place "network," double-click on "windows network," double-click on your workgroup, double-click on a computer, double-click on a Share, and there you are.

---

