---
title: "no good on upgrade"
date: 2012-08-18
forum: System76 Support
---

### Post by porlaizquierda on 2012-08-18
i tried to do an upgrade fron 10.04 to 12.04 on my starling netbook. everything seemed to habe been going fine, but when i restarted all i got was a blank black sceen with a flashing icon. what is going on?? please let me know how i can fix this.

---

### Post by Carborundum on 2012-08-18
Can you type things at this screen, or is it completely unresponsive?

---

### Post by porlaizquierda on 2012-08-18
completely unresponsive...

---

### Post by porlaizquierda on 2012-08-19
i'm using a live cd. all my stuff is still there on the hard drive, but still can't get it to start up regularly. is there anything i can do from the live cd to get everything working from startup?

---

### Post by porlaizquierda on 2012-08-19
i tried boot repair and got this:

paste.ubuntu.com/1155432

---

### Post by isantop on 2012-08-20
> **porlaizquierda said:**
> i tried boot repair and got this:

paste.ubuntu.com/1155432

From the LiveCD, open up a terminal window, then run these commands:

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
grub-install --force /dev/sda
```

I'd recommend pulling this thread up from within the LiveCD, and copy-pasting.

---

