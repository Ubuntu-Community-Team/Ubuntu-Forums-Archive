---
title: "Installation issue with Grub"
date: 2011-01-19
forum: Ubuntu Studio
---

### Post by fight2survive on 2011-01-19
i currently have opensuse dual booted with windows 7 on this system. i tried installing ubuntu studio along with it, but after installation i cannot boot into the OS, it's still the opensuse grubloader that appears, it's as if the ubuntu studio grub hasn't "taken over" as it was supposed to...
can anyone help me with this?

---

### Post by Pablo_F on 2011-01-20
Hi, 

Hi, I see two options. 

1) Grub loader in opensuse: I think opensuse uses legacy GRUB. If so, in Opensuse you can add the menuentry for ubuntustudio. 

2) Grub loader in ubuntustudio: 

(Ubuntustudio uses GRUB2)

You can boot in ubuntustudio if you use supergrub disk. Then open a terminal and do a:

sudo update-grub

and:

sudo grub-install /dev/sda

assuminig that your first harddrive is /dev/sda (check with *sudo fdisk -l*)

I think this will solve the issue,

Cheers, Pablo

---

### Post by fight2survive on 2011-01-20
i tried the second option, booted into ubuntu studio, did this but when i restarted i still had the same issue...

as for the first option, i don't really understand how to do this...sorry i'm fairly new at everything linux....
thanks

---

### Post by fight2survive on 2011-01-20
i tried the second option, booted into ubuntu studio, did this but when i restarted i still had the same issue...

as for the first option, i don't really understand how to do this...sorry i'm fairly new at everything linux....
thanks

---

### Post by fight2survive on 2011-01-20
i tried the second option, booted into ubuntu studio, did this but when i restarted i still had the same issue...

as for the first option, i don't really understand how to do this...sorry i'm fairly new at everything linux....
thanks

---

### Post by fight2survive on 2011-01-20
i tried the second option, booted into ubuntu studio, did this but when i restarted i still had the same issue...

as for the first option, i don't really understand how to do this...sorry i'm fairly new at everything linux....
thanks

---

### Post by fight2survive on 2011-01-20
i tried the second option, booted into ubuntu studio, did this but when i restarted i still had the same issue...

as for the first option, i don't really understand how to do this...sorry i'm fairly new at everything linux....
thanks

---

### Post by Pablo_F on 2011-01-20
Hi, 

When you are in ubuntustudio, can you give the terminal output of:

sudo fdisk -l

and 

sudo update-grub

?

---

### Post by Pablo_F on 2011-01-20
Maybe you have two hard disks... We need more info to give help. From ubuntustudio, please give the terminal outputs of:

sudo update-grub

sudo fdisk -l

Cheers, Pablo

---

### Post by oldfred on 2011-01-20
This also includes the fdisk output, but includes just about everything about all the systems on your drives.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

