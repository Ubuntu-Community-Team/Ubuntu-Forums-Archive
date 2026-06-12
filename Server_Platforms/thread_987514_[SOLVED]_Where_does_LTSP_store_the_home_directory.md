---
title: "[SOLVED] Where does LTSP store the /home directory?"
date: 2008-11-19
forum: Server Platforms
---

### Post by Dragonbite on 2008-11-19
I am about to set up an LTSP server and I want to move the user's /home directory into a separate partition (possibly separate hard disk) but I am not sure which to place there.

Also I want to know from where should I backup my files.

There is one set under the root /home directory for the entire server but I seem to remember (haven't fooled around with LTSP lately) that there is a copy under /etc/ltsp or /var/ltsp or something like that, which is where the clients actually connect to.

I may just have to do an install and poke around to refresh my memory if I am not making sense here.

---

### Post by Dragonbite on 2008-11-20
The LTSP portion stores the files in (it appears) ```
/opt/ltsp/<architecture>
or in my case
/opt/ltsp/i386/...
```

but since they are empty in my Edubuntu 7.10 version I suspect that the actual files are located in the regular root directory and only the LTSP-specific files are located in the /opt/ltsp/<arch> location.

---

