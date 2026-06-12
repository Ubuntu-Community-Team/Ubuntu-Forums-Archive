---
title: "connect to windows server"
date: 2009-12-28
forum: Server Platforms
---

### Post by gameguy on 2009-12-28
Is there any way so I can get my laptop to connect to an XP server using 9.10.
I've installed SMB.
Lets say the workgroup is "workgroup", local username=gameguy, local password=secret, server username=guest, server password=blah.

---

### Post by CharlesA on 2009-12-28
If you are attached to the network it should be as simple as browsing to the "network"

Places > Network > Windows Network > Computer > Share

You will be prompted for username/domain/password.

I didn't need to install anything extra after I installed Ubuntu Desktop 9.10.

---

### Post by gameguy on 2009-12-28
:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by CharlesA on 2009-12-28
Check here: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7352392](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7352392)

---

### Post by gameguy on 2009-12-28
Yes. Dad has a firewall (ESET), and won't disable it. I don't know how to configure it, but dad probably does (I forgot, but I want it to be located at /server, not networks>server-PC)

---

### Post by CharlesA on 2009-12-28
smb://computername/share

---

