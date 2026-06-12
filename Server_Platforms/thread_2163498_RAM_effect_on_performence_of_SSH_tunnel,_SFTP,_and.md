---
title: "RAM effect on performence of SSH tunnel, SFTP, and samba"
date: 2013-07-18
forum: Server Platforms
---

### Post by SchnappiJedi on 2013-07-18
Does additional RAM make an SSH tunnel, SFTP connection, or samba share faster (independent of internet speed of either the server location or remote client)?

Basically would a 1 GB (RAM) ssh server have the same SFTP, ssh tunnel, and samba upload and downspeeds over an equal internet or LAN connection as the same server with 8 GB of RAM?

---

### Post by CharlesA on 2013-07-18
Doubt it, especially considering the load those services exert on the server itself. If you are transferring files, you would probably get hung up with I/O before you ran into memory issues.

---

### Post by SeijiSensei on 2013-07-18
You can test this yourself.  Open two terminal windows and run **top** in one of them.  In the other one use something like rsync to transfer a large file and watch what happens to resource utilization.  Like Charles, I don't think you'll see much of a memory effect.

---

### Post by nerdtron on 2013-07-18
Same here, I don't think more RAM will affect the transfer speed. Although it's good that the minimum is 1GB.
A faster CPU, faster hard drive and fast connection (Gigabit LAN or faster internet) will increase the transfer speed.
CPU: SSH and SFTP uses encryption so it need more cpu cycles than regular copying.
Faster HDD: sure do! Fast read times will make the data fly out more quickly!
Faster Connection: you need a connection that will maximized the transfer capability of the SFTP/SAMBA server.

---

