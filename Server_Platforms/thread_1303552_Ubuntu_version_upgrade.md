---
title: "Ubuntu version upgrade"
date: 2009-10-28
forum: Server Platforms
---

### Post by happyhacker on 2009-10-28
I am following the instructions and have just done the update i.e. apt-get update followed bu apt-get upgrade.

Now the server is connected to the network have has some connected Samba shares.

Is it OK now to issue the command apt-get do-release upgrade on my 8.10 with those conncetions live and probably doing backups?

Also, does this download the complete Ubuntu meaning I have a wait of an hour or two before the upgrade installs?

---

### Post by cdenley on 2009-10-28
Generally, when a service is upgraded, it is restarted. This would mean that any active connections would be lost. Updating to a newer version will take a while, depending on your bandwidth and hardware.

---

