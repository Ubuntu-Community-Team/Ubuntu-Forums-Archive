---
title: "freenx server 9.10: windows users can't mount share forlders"
date: 2010-03-25
forum: Server Platforms
---

### Post by Ricardo.Diaz on 2010-03-25
Hi,

When I connect with my ubuntu 9.10 x86_64 freenx server from Linux/Mac share folders from client side will properly mounted and I can use with no problems.

When I connect to the same server from windows box, I get this error message:

> Info: Share: '//COMPUTER/FOLDER' failed to mount: mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Last two days I was googleing a lot about this but all I tryed didn't work.

Is there somebody share folder works from windows connection?

Thanks in advance,
Ricardo Díaz

---

### Post by johnson.d on 2010-03-26
Can you explain your setup in detail?

---

### Post by Ricardo.Diaz on 2010-03-26
I was installed in a Ubuntu 9.10 x86_64 clean box FreeNX from Launchpad ppa using this info:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

FreeNX is working fine with remote users accesing from Linux or Mac boxes with the last NX Client downloaded from nomachine.com. From these boxes smb shares are mounted fine and works as expected.

When I try to connect from Windows XP client, the share I selected in client side is not right mounted showing allways this message:

> Info: Share: '//COMPUTER/FOLDER' failed to mount: mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

In Windows XP machine the share is available for the net and users can read and write with no problems.

If you need more info, please let me know.

Thanks,
Ricardo Díaz

---

