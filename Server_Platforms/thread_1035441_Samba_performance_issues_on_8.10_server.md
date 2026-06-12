---
title: "Samba performance issues on 8.10 server"
date: 2009-01-09
forum: Server Platforms
---

### Post by gdiscenza on 2009-01-09
I'm running 8.10 on a Dell 1435 w/4GB ram and serving up several shares that are actually located on a NFS box that is on a dedicated Gigabit network.

Performance is miserable!

Click on a drive - wait, wait, wait, wait, contents!
Click on a folder - wait, wait, wait, wait, contents!

I checked the log files and the only thing that I could find is the following entry:

libsmb/clientgen.c:cli_receive_smb (165)
Receiving SMB: Server stopped responding

This message repeats at irregular intervals between 10 seconds and 5 minutes.

I'm ready to tear my hair out!!!

Whatever files you want me to post I will.

TIA!

-Gregg

---

