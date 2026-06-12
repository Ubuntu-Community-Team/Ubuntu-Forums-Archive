---
title: "Moving .ssh folder from real Ubuntu to Virtual Ubuntu"
date: 2009-02-23
forum: Virtualisation
---

### Post by lyceum on 2009-02-23
I was running Ubuntu native on my last laptop, but I needed to switch to Mac and I hate dual booting, so I loaded VMware Fusion so I could run Ubuntu in Mac OSX (as I have no way of running OSX in Ubuntu). I need to more the .ssh folder to my VMware Ubuntu, but there is no .ssh folder, or I can`t get to it. I think I may need sudo for that. What it the easiest way to go about this?

---

### Post by bodhi.zazen on 2009-02-23
You can copy the .ssh directory to a usb device, then mount the usb device in the guest.

could you can use samba ?

Last, if you install a ssh server, use scp

```
scp -r ~/.ssh user@ubuntu:/home/user
```

Alternates would be ftp or http, any network protocol will do really.

---

### Post by lyceum on 2009-02-25
> **bodhi.zazen said:**
> You can copy the .ssh directory to a usb device, then mount the usb device in the guest.

could you can use samba ?

Last, if you install a ssh server, use scp

```
scp -r ~/.ssh user@ubuntu:/home/user
```

Alternates would be ftp or http, any network protocol will do really.

Thanks. My issue was that I didn't know what a .ssh file was (still don't really) and couldn't figure out why there wasn't one on the virtual Ubuntu. I just changed the folder from ssh to .ssh and now I have one and everything is working fine.

-edit- 

Was trying to mark this as solved, but it looks like there is a new way of doing it? I don't have time to figure it out, but this thread is solved, thanks!

---

### Post by bodhi.zazen on 2009-02-25
Nope, you have to manually edit the title.

~/.ssh normally holds keys, authorized keys, and known_hosts 9depending on if you are working on the server / client side).

---

### Post by lyceum on 2009-02-26
> **bodhi.zazen said:**
> Nope, you have to manually edit the title.

~/.ssh normally holds keys, authorized keys, and known_hosts 9depending on if you are working on the server / client side).

Good to know, thanks!

---

