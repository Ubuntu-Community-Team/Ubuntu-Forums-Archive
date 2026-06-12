---
title: "installation help for Vmplayer 4.0 in 11.10"
date: 2011-12-24
forum: Virtualisation
---

### Post by indyeah on 2011-12-24
Hi Guys,

I downloaded VMware player 4.0 bundle.I marked bundle file as executable in properties and after clicking it opens terminal asks for my password and then gives this error message 

(gksudo:2209): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"

So how can i install VM player and/or whats the proper installation procedure for the same.

Thanks guys

Edit: Used this command for installation but still getting the same error
```
gksu bash VMware-Player-4.0.0-471780.x86_64.bundle
```

---

### Post by BC59 on 2011-12-24
Try this guide, is fantastic:
[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

---

### Post by indyeah on 2011-12-24
> **BC59 said:**
> Try this guide, is fantastic:
[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

Thanks worked like a charm:P

merry xmas

---

### Post by dcstar on 2011-12-25
> **BC59 said:**
> Try this guide, is fantastic:
[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

Or simply:

```
sudo ./VMware-Player-4.0.0-471780.x86_64.bundle
```

Why do people over-complicate things?

---

