---
title: "swap motherboard...need to reinstall?"
date: 2008-08-14
forum: Server Platforms
---

### Post by jonabyte on 2008-08-14
So I need to swap a bad motherboard in a new Dell server that has Ubuntu installed. I am told its the exact same model as what is already there.
I am wondering if I will need to reinstall the system?
I am going to do a backup, but would like to know if anyone has any insight?

Thanks

---

### Post by glotz on 2008-08-14
I think not. I once took a hard disk with a complete Ubuntu install to a new machine with entirely different hardware. Worked just fine. It was a desktop though but I don't think it matters here.

---

### Post by jonabyte on 2008-08-14
thanks, thats good to know, I hope it will be that easy.

---

### Post by windependence on 2008-08-14
Linux is MUCH more forgiving on this than Windoze. In most cases you will be fine if the hardware is supported. As you did, backups should always be made before attempting it though.

-Tim

---

### Post by jonabyte on 2008-08-21
well the swap went last night and no need to reinstall, just adjust the time (probably due to the new bios) and for some reason the static ip assigned originally was changed to dhcp.

---

### Post by windependence on 2008-08-21
Yeah, that probab;y changed because of the MAC address of the NIC.

-Tim

---

