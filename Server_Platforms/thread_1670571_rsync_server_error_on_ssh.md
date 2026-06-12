---
title: "rsync server error on ssh"
date: 2011-01-19
forum: Server Platforms
---

### Post by kgatan on 2011-01-19
Hello,

I have a problem with my rsync server when trying to sync over ssh.
Ive reconfigured ssh to use port 581 and use the following rsync command as googled,

```
rsync -azvv -e "ssh -p581" srcfolder/ user@server::destination
```

and i get

```
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.6]
```

When i use it without SSH it works like a charm and except for rsync SSH works as it should.

Sever is running Ubuntu 10.04.

---

