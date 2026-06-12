---
title: "mount and blade: warband"
date: 2011-05-20
forum: Wine
---

### Post by us11csalyer on 2011-05-20
I got warband to work near perfection on ubuntu 11.4. Only problem is the 180 degree mouse thing.

playon
1.3.8 wine primary
1.2.2 mousepatch wine
gpu: hd5750

Is there a way to fix the 180 degree mouse thing?

---

### Post by bobwyajnr on 2011-05-21
> **us11csalyer said:**
> 
Is there a way to fix the 180 degree mouse thing?

Yes, if you'd perhaps bothered to check out the [WINE AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20604")... You read the forum Ubuntu Forum/Wine sticky threads first before posting - right??!! [-X

Pull the latest WINE build from the Ubuntu WINE team PPA (currently 1.3.20). Also make sure you update to WINE 1.3.21 ASAP (1.3.20 breaks a lot of games - there are a lot of fixes in the WINE Git tree that will be officially merged in the next version of WINE). Minor releases, of WINE, are normally a month or two apart.

BTW One problem with using POL is that the WINE developers won't support it (basically because it uses patched versions of the WINE source and also they will want you to test with latest development version of WINE).

Bob

---

