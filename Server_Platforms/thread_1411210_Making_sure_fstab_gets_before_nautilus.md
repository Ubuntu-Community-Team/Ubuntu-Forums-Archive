---
title: "Making sure fstab gets before nautilus"
date: 2010-02-19
forum: Server Platforms
---

### Post by denarced on 2010-02-19
Here's the problem.
I moved my data to a server, which is automatically mounted at startup with fstab. I also defined my Desktop to a directory which is on the NFS-share that is mounted at startup.

The problem is that fstab doesn't seem to get there fast enough.
Nautilus show my home-folder as Desktop and reset the config-file where I define the custom Desktop location.

You can get around this by killing nautilus, redefining the .config/user-dirs.dirs-file and starting nautilus again but I'd like to fix the problem, not the symptoms.

How to do it?

---

### Post by BobVila on 2010-02-19
Have you edited the timeout option in fstab to give the machine a bit more time to mount the nfs share properly?

add something like this to the end of your nfs line in fstab:
```
timeo=60
```

(the timeout option is in TENTHS of seconds, so that works out to 6 seconds. Adjust accordingly)

---

### Post by denarced on 2010-02-19
> **BobVila said:**
> Have you edited the timeout option in fstab to give the machine a bit more time to mount the nfs share properly?

add something like this to the end of your nfs line in fstab:
```
timeo=60
```

(the timeout option is in TENTHS of seconds, so that works out to 6 seconds. Adjust accordingly)

Sounds like something I'm looking for.
Thanks

---

