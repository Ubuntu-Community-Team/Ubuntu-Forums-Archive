---
title: "Need to migrate 64 bit server to 32, some questions about backup..."
date: 2011-05-12
forum: Server Platforms
---

### Post by Homer314 on 2011-05-12
Hi guys. Hi need to "Virtualize" a 64bit 10.04 server and run it on Virtual Box without a virtualization compatible cpu, so i can run 32bit guests only...

I'm hope i can backup my working paths and restore on a fresh 32bit vm with this script

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

Can i expect that this theory will work ?

Thank's a lot.

---

