---
title: "openssh server on server install"
date: 2006-11-29
forum: Server Platforms
---

### Post by Lars Noodén on 2006-11-29
There is a server install option for 6.06.1 for the x86 arch.  It seems to install the openssh client by default and not the server.  I'd expect the opposite.  Also, there's probably no reason that sshd needs to run all the time as a demon, it can probably be called by xinetd when it is needed.  The connections are intermittent and usually long lasting so it's well suited to xinetd.

---

### Post by elst on 2006-11-29
Ubuntu follows a "no open ports by default" policy, which is why an SSH server isn't installed by default.

Running SSH from inetd/xinetd isn't a common configuration. I don't  really know why that's the case, but I'd speculate that it doesn't offer enough of a practical benefit.

---

