---
title: "URGENT PRODUCTION HELP: 3+ servers rooted tonight"
date: 2008-09-19
forum: Security
---

### Post by beniji on 2008-09-19
Guys, I think my server farm has been seriously exploited.

Running a routine "netstat -tlpn" as root on one production apache server  tonight (ubuntu gutsy) I noticed that the PID did not show up at all for one open TCP port (even though I was root and all other listen sockets had their PIDs listed). 

Sure enough I could telnet into that port from another server - this was no bogus artifact. The socket was  held open and tcpdump showed traffic flowing at either end.

lsof did not show this particular socket as being open (!?).

With lsof not showing the socket at all, and netstat's -p option not revealing any PID, I started to get very worried and turned to /proc.

When connecting in externally to this port I noticed that NO INODE IS CREATED. An inode should surely always be created for each end of a socket. I checked, and it is for all other genuine ports open on that box. But not when I connect to the suspicious port.

In other words, unless I am missing something, the only way this can be happening is if I have an exploited kernel or kernel module. I am aware that kernel module exploits of this form exist, where a remote attacker can trigger a kernel based keylogger etc with a special command sequence sent over TCP.

The same symptoms are now shown on 2 others of my servers.

This is bad - I have gone into emergency mode and done what i can - revoked a load of keys, deleted sensitive logs and so on. 

Now I'm stuck. The servers are still up and running - I'm not sure if this is indeed an exploit but it ain't looking good. 

Any security gurus help me out here?

Ben

---

### Post by beniji on 2008-09-20
I think this was a false alarm - having compared the dpkg selections on all servers I noticed the" suspect" ones all had nfs-kernel-server installed. There appears to be some strange magic there (the clue is in the "kernel" part) which is only revealed by "rpcinfo -p".

---

