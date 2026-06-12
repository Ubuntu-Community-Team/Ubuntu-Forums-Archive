---
title: "USB Error in Virtualbox:("
date: 2008-11-24
forum: Virtualisation
---

### Post by freakinjonathan on 2008-11-24
i get this error while trying to load up Virtualbox on ubuntu intrepid

---

### Post by PropheticAngel on 2008-11-25
*Bump*

I have the same error, running a T60.  
I'm not using the OSE version and there is no 'magic' section in the config file for USB use.  

I would like to get USB working.

---

### Post by freakinjonathan on 2008-11-27
ok so i got it to work by editing the fstab file on the last few lines
in /etc/fstab.txt

open up this file and add this to the end of the document

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

save it and i think i had to restart the machine though.

---

