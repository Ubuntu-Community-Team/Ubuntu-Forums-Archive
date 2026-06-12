---
title: "Virtual Box unable to mount extra drives"
date: 2011-02-13
forum: Virtualisation
---

### Post by ve2 on 2011-02-13
I am running XP and have virtual box with Ubuntu as one of the box'es. I am unable to mount the C drive or my extra drive labeled D.

---

### Post by CharlesA on 2011-02-13
You won't be able to mount the drives on the Host inside the guest.

You can share folders on the host with the guest, but you can't directly mount the C or D drive inside an Ubuntu VM running on Windows.

---

### Post by ve2 on 2011-02-14
Ok I added the drives. I dont see them on Ubuntu... I added them in a VM of Windows XP and it worked.. any ideas?):P

---

### Post by CharlesA on 2011-02-14
Are you saying you have extra disks attached to the VM or are you trying to access the host's drives?

---

### Post by mciverza on 2011-02-16
The VirtualBox addons need to be installed in order for you to access the shared folders between Host (in your case Windows) and a guest OS (in this case Ubuntu)

Once you have installed the guest additions, a reboot of the guest will allow you to access the shared folders.

if the share is called "share" then in the guest, run this from a terminal

mount -t vboxfs share /mnt

then you should be able to browse the share with the file browser (nautilus)

---

