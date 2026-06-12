---
title: "Force vsftpd to use passive mode..."
date: 2010-06-17
forum: Server Platforms
---

### Post by ragtag on 2010-06-17
I've set up Ubuntu 10.04 server that is NAT-ed through a firewall. It's running vsftpd, which works fine...as long as it's run in PASSIVE mode. Most ftp clients seem to automatically choose PASSIVE mode (it worked fine with Nautilus, Filezilla and Windows Explorer), but some like "ftp" on the command line, don't. If I try to run "ls" in "ftp", it outputs:

```

200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.

```

And nothing else. If I set it to passive mode, it runs fine.

Is there anyway to configure vsftpd, to tell the client to use PASSIVE mode by default?

---

