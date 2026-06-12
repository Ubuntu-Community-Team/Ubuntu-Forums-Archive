---
title: "Using Truecrypt to encrypt home directory"
date: 2009-07-02
forum: Security
---

### Post by MikeSD on 2009-07-02
Hi,
I'm relatively newbie to Ubuntu, I want to encrypt home dir with Truecrypt 6.2a without repartitioning drive (no space for more partitions).

Seems I have found a working way to do this , but maybe this isnt the best solution, so I will appreciate any suggestions...

I've created TC container.
I've copied all contents of my homedir say /home/user to container.
Added ```
truecrypt /pathto/container /home/user
``` to beginning of /etc/gdm/Init/Default

Now before gnome login screen, Truecrypt password request window pops.
If correct password is entered, container mounts as my homedir.
This also works with Truecrypt hidden containers.
(i'm the only user of this PC, so this method suits me)

So method seems to be working...
I'm just thinking maybe theres more beautiful way to do this?

Thanks

---

