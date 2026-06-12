---
title: "vmware player fails to start after upgrade to 9.10"
date: 2009-11-08
forum: Virtualisation
---

### Post by froff on 2009-11-08
hello
My vmware player fails to start after upgrade system to version 9.10 (64b)

```

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual machine communication interface                            failed
   Blocking file system                                               failed
   Virtual ethernet                                                   failed

```

Anybody can help?

---

### Post by fjgaude on 2009-11-08
I believe you have to re-install player... just go to the folder where you have the bundle and make sure it is exicutable. Then do a ./ in front of it from root or sudo.

If you don't understand, come back here.

---

### Post by froff on 2009-11-08
> **fjgaude said:**
> I believe you have to re-install player... just go to the folder where you have the bundle and make sure it is exicutable. Then do a ./ in front of it from root or sudo.

If you don't understand, come back here.


thanks, but I did reinstall player from bundle and it didn't solve the problem :(

---

### Post by fjgaude on 2009-11-08
If you don't use Player 3.0 I don't think it works.

---

### Post by froff on 2009-11-08
> **fjgaude said:**
> If you don't use Player 3.0 I don't think it works.


But current version is 2.5.3, not 3.0
Ok, I'll try. Currently I have 2.5.2

best regards

---

### Post by fjgaude on 2009-11-08
I think you can upgrade from within Player, at least you can from 3.0, the one I'm using from vmware.com.

---

### Post by froff on 2009-11-09
> **fjgaude said:**
> I think you can upgrade from within Player, at least you can from 3.0, the one I'm using from vmware.com.


Sorry, my mistake. Latest version is 3.0, not 2.5.3.
Great! Everything works perfectly :)
Thank You very much.

---

