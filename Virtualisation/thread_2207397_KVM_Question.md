---
title: "KVM Question"
date: 2014-02-23
forum: Virtualisation
---

### Post by rayj00 on 2014-02-23
I am running Ubuntu 12.04 and using KVM to virtualize a few servers.

Every time I create an Ubuntu server (non-gui) client VM the subsequent window is the incorrect size.
If I vi a file, I have to scroll up and down to get to the top and bottom of the file.

How to fix this?

Thanks,

Ray

---

### Post by 1clue on 2014-02-23
First thing:

Once your VM is installed, you don't have to use the console anymore.  Start the ssh server and log in using your favorite terminal.

Second thing, in virt-manager you can go to the View menu and resize to VM.

---

### Post by rayj00 on 2014-02-23
Thanks.  I kinda knew that but I was just wondering how to fix this.

Thanks,

Ray

---

### Post by TheFu on 2014-02-24
> **1clue said:**
> First thing:

Once your VM is installed, you don't have to use the console anymore.  Start the ssh server and log in using your favorite terminal.

Second thing, in virt-manager you can go to the View menu and resize to VM.

Exactly. i only use the console as a last resort. ssh is 100000x faster, maybe 100001x. ;)

For me, it is the lack of a good select/paste that really bothers me even more than the speed problem.  With ssh in an xterm, select/paste works like GOD intended on all UNIX systems.

After all, we all know that the only reason for any GUI is to more easily manage our terminals. ;)

---

