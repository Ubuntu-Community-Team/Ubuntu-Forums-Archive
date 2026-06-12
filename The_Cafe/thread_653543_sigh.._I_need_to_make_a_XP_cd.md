---
title: "sigh.. I need to make a XP cd"
date: 2007-12-30
forum: The Cafe
---

### Post by hhhhhx on 2007-12-30
ok, this is going to sound realy wrong, but i need to make a Windows XP boot disk.  Its not for me, its for my friend at work. His computer is getting way overboated and he needs to reinstall Xp, but he doesent have a disk.  I thaught about telling him about linux, but quite frankly i dont think that he is ready to move on to a new OS.  I have an XP disk i just need to make a copy of it for him. Is there anyway that i can do this in ubuntu?

P.S.  :  I'm sorry Tux  :(

---

### Post by lisati on 2007-12-30
Depending on how new his machine is, it might have come with a recovery partition or a recovery CD/DVD - is that an option?

---

### Post by Kingsley on 2007-12-30
Isn't that illegal?! :shock: :shock:
You may as well download and burn him a new copy. Just my $.02.

---

### Post by hhhhhx on 2007-12-30
The thing is that he is extreamly computer illiterate, so i figgure that its better to start from scratch than to have him try that

---

### Post by hhhhhx on 2007-12-30
> **Kingsley said:**
> Isn't that illegal?! :shock: :shock:
You may as well download and burn him a new copy. Just my $.02.

 Holy Heck, i dident even think of the legality part.  OMG.  I guess that i am just so used to everything bieng free and opensource i just forgot.[-X

---

### Post by lisati on 2007-12-30
If the OP's friend's machine has a recovery partition that's ina reasonably healthy condition, a CD might not be needed.....

---

### Post by hhhhhx on 2007-12-30
> **lisati said:**
> If the OP's friend's machine has a recovery partition that's ina reasonably healthy condition, a CD might not be needed.....

I highly dought it, even if it were healthy he wouldn't know what to do with it.  I figure that ill just lend him my XP boot disk

---

### Post by init1 on 2007-12-30
Making a copy of the disk is probably illegal, so make sure that you don't run this command:
```

dd if=/dev/cdrom of=illegalcopy.iso

```
to make the ISO and
```

cdrecord illegalcopy.iso

```
to write it. Other programs like K3B and Graveman can do this too so make sure that you don't use them either.

---

### Post by KiwiNZ on 2007-12-30
He needs to buy XP. If he has a legit key but has lost his media , contact Microsoft.
 
I am closing this thread now

---

