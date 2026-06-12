---
title: "modified the file /etc/nssswitch.conf ... now no local users can be recognized"
date: 2009-07-04
forum: Server Platforms
---

### Post by ythaaa on 2009-07-04
Hi,

Ok I have a big problem here and need help....~~~~

i have server running on NIS. i have a client which i accidentally modified the file /etc/nssswitch.conf such that now no local users can be recognized. not even root. i cannot use keyboard or mouse or anything. 

i can only go to grub and i can type in grub. is there anyway i can use grub to modify my file so that i can go back to my lovely linux. i backup my file so as long as i can  go to the file and modify it.

really need help. thanks~~~~~~~~

---

### Post by ibutho on 2009-07-04
Hi. 

If you have physical access to the machine, boot from a live cd or live usb. Mount your Ubuntu root partition and edit the file.

---

### Post by Tibuda on 2009-07-04
Can you log into recovery mode from grub? If so you'll be able to edit that file using a root terminal. If you can't, then try ibutho suggestion.

---

### Post by ythaaa on 2009-07-04
hi i managed to download live cd and burn it and fixed my problem. thanks a lot....

however just for my knowledge, how to get into recovery mode with grub?

thanks

---

### Post by carml on 2009-07-04
If you installed only Ubuntu,just press ESC when you boot to access to the menu of kernels and select the recovery mode of the kernel you want to use.
If you installed in a dual boot,just follow the last part of the previous phrase. :)

---

