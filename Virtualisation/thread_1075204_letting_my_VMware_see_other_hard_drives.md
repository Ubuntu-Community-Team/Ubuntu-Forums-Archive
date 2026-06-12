---
title: "letting my VMware see other hard drives?"
date: 2009-02-20
forum: Virtualisation
---

### Post by Arminius on 2009-02-20
I'm using VMware workstation, and I'm in the section that let's u add hard drives?
now my understanding is that it will only let my virtual drive see and detect the other "real" drives on my pc.
that it won't format them or delete the data?
if that's wrong let me know, but when u go forward to the device section, it has some choices /dev/sde
                    /dev/sdc
                    /dev/sda
                    /dev/sdb

how do I find out which hard drives these are? it warns that if I select the boot drive it might cause terrible things to happen?
so it's my understanding that when I click on the right drive that the virtual drive will detect and see that drive and all my files on the real drive will be safe and uneffected?

oh and it's save to click on use entire disk?

---

### Post by Arminius on 2009-02-21
bump

---

### Post by dcstar on 2009-02-21
> **Arminius said:**
> I'm using VMware workstation, and I'm in the section that let's u add hard drives?
now my understanding is that it will only let my virtual drive see and detect the other "real" drives on my pc.
that it won't format them or delete the data?
if that's wrong let me know, but when u go forward to the device section, it has some choices /dev/sde
                    /dev/sdc
                    /dev/sda
                    /dev/sdb

how do I find out which hard drives these are? it warns that if I select the boot drive it might cause terrible things to happen?
so it's my understanding that when I click on the right drive that the virtual drive will detect and see that drive and all my files on the real drive will be safe and uneffected?

oh and it's save to click on use entire disk?

Ok, the reason VMs should not have direct access to any drive the host OS uses is pretty basic - All (repeat **ALL**) these OSs assume exclusive control of these resources. Having two OSs control them ceases the exclusive control.

If you want to take the risk then live with the potential consequences (and please don't complain here if something goes wrong), if you don't then just set up controlled access through things like Samba shares.

---

### Post by HermanAB on 2009-02-21
The best way to share folders or drives is through NFS.  NFS is the absolutely easiest network file system to set up.  The reason why nobody ever talk about it, is because it just works - as opposed to Samba which never works...

Here, I wrote something:
[http://aeronetworks.ca/nfs-howto.html](http://aeronetworks.ca/nfs-howto.html)

Cheers,

Herman

---

