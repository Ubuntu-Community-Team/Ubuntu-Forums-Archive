---
title: "Virtualbox share problem"
date: 2009-02-25
forum: Virtualisation
---

### Post by jdabgotra on 2009-02-25
Hi Community,
I have a problem with virtualbox shares. I am running XP guest and Intrepid client. I have to frequently reconnect to the share using the "net use x: \\vboxsvr\share" command. Is there any way around this?
Best
James

---

### Post by Perryg on 2009-02-25
> **jdabgotra said:**
> Hi Community,
I have a problem with virtualbox shares. I am running XP guest and Intrepid client. I have to frequently reconnect to the share using the "net use x: \\vboxsvr\share" command. Is there any way around this?
Best
James

Is windows the host or the guest?
Anyway in windows use this:
```
net use x: \\vboxsvr\share /persistent:yes
```

---

