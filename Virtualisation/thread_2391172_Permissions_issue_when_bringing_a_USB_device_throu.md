---
title: "Permissions issue when bringing a USB device through to a Ubuntu guest in VirtualBox"
date: 2018-05-06
forum: Virtualisation
---

### Post by thekoolestip on 2018-05-06
Host: Ubuntu Desktop 16.04
Guest: Ubuntu Server 18
Virtualbox: latest version (I just installed it)

I've  got an Arduino plugged in to the host and it's available at  /dev/ttyACM0.  I've got a python script that kicks some info out to the  Arduino via PySerial and it works just fine on the host.  I  want to bring the Arduino to my Ubuntu Server guest machine.  I mapped  serial port in VirtualBox on the guest to /dev/ttyACM0 on the host.  Now  I see /dev/ttyS0 in the guest but when my script tries to access it I  get permission denied.  Does anyone know where I have to change the  permission?  Guest?  Host?  Do I add my user account to a group or  something?

Thanks for reading.

Edit: I fixed this by adding my user account to the dialout group on my Ubuntu guest machine. sudo gpasswd --add username dialout

---

### Post by wildmanne39 on 2018-05-06
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by ju2wheels on 2018-05-11
>  I mapped serial port in VirtualBox on the guest to /dev/ttyACM0 on the host.

Can you provide more detail on what you mean by that?

If you had done a proper USB attachment to the guest, it would show up as /dev/ttyACM0 on the guest and not be available on the host. You need to identify the Android device USB id via the output of lsusb, and then attach the right USB id to the guest.

---

