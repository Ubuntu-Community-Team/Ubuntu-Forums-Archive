---
title: "Create a remote ssh folder from command line?"
date: 2009-12-04
forum: Server Platforms
---

### Post by tstack77 on 2009-12-04
I'd like to create a folder on my headless server that acts as an ssh connection to my sister's computer a few miles away. The endgame is to be able to simply cp files into that folder in order to send on to her computer.

If there's an easier way than this idea to create a secure connection I'd love to hear it as well.

-axel

---

### Post by cdenley on 2009-12-04
```

sudo apt-get install sshfs
man sshfs

```

---

### Post by tstack77 on 2009-12-04
Thanks! I'll post back when I run into the snags :P

---

### Post by Iowan on 2009-12-04
> **tstack77 said:**
> Thanks! I'll post back when I run into the snagsThere will probably be a few as you get into port-forwarding, etc... but help is available.

---

