---
title: "How to remove a entry from grub?"
date: 2010-12-20
forum: Server Platforms
---

### Post by cbarron on 2010-12-20
i need to remove an entry from my grub boot loader does anyone have a simple way to do this?

---

### Post by wojox on 2010-12-20
Probably, but you would need to tell us what. Is it old kernels?

---

### Post by brettg on 2010-12-20
If you are using grub (not grub2) then edit

```
/boot/grub/menu.list
```

Find the appropriate section and remove it.

---

### Post by gtdaqua on 2010-12-20
Or if u r using 10.10, which is what it says on ur profile, the grub file is located here:
```
/boot/grub/grub.cfg 
```

As a good practice, remark the lines with "#" (making them begin with a #) rather than removing them completely (unless you really want to remove it).

---

### Post by garvinrick4 on 2010-12-20
#Go to synaptics and remove offending kernel there:
In upper right hand corner type in kernel like 2.6.32-25 or
similar and remove:
#This tells you what is in grub menu.
```
grep menuentry /boot/grub/grub.cfg
```
After you remove kernel go to terminal and:
```
sudo update-grub
```
## In grub2 The /boot/grub/grub.cfg file will go back to way it was if you edit it
     when the update-grub is ran. No reason to mess with it at all.

---

### Post by cbarron on 2010-12-20
Thanks for all the input. I should have been a little bit more speciffic this is for Ubuntu Server 10.04 and it is grub not grub2.

---

### Post by wojox on 2010-12-20
Telling us what you want removed is really going to help. There is a right and wrong way to do this and doing it wrong can land you in a world of hurt. 

You said Server. With no gui? you will need 

```
sudo nano
```

to edit anything.

What does this say:

```
grub-install -v
```

---

