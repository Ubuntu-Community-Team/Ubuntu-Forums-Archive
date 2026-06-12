---
title: "Help with PAM/VSTPD on 8.04"
date: 2010-03-23
forum: Server Platforms
---

### Post by audiowonderland on 2010-03-23
I am trying to setup a secured ftp server for our band to share new tracks between our studios. Previously I had a Fedora 3 server using VSFTPD and PAM with virtual users that worked well and I would like to replicate that. Unfortunately I have had issues getting the Berkeley DB software to install properly which seems to be a requirement to get the virtual users function working in PAM. Is it available available from the repository?

Once I get it working I am planning to shutoff SSH password authentication and using keys to lock down access. I have the iptables config from the old server to install on this new box.

On a related note, is there a better option to provide secure files sharing on the net? I am open to other ideas besides an FTP server.

---

