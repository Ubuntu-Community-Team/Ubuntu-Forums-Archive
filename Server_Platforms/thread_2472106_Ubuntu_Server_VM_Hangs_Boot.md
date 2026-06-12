---
title: "Ubuntu Server VM Hangs Boot"
date: 2022-02-17
forum: Server Platforms
---

### Post by ep3w on 2022-02-17
I am running Ubuntu Server in a VM on a Synology NAS. When I view the machines screen it always seems to be hung on some text and there is no command prompt. See below example. Seems like the text varies when i reboot. I am still able to access the machine via SSH and everything seems to work fine. Any suggestions? Thanks.

---

### Post by MAFoElffen on 2022-02-17
Will the VM boot an Ubuntu LiveCD ISO if mounted to the VM, where you can look at the logs of the installed VM system?

---

### Post by ep3w on 2022-02-17
I'm still able to SSH into it so I should be able to read any logs from there I'm guessing (I'm new to ubuntu server). If not, I'm sure I could get on a live CD. Any suggestions on where to start for logs?

I've tried hitting esc, Ctrl+c, etc with no effect. It's almost like it's the display hanging? I've troubleshooted xorg issues before but this is out of my wheelhouse.

---

### Post by kevdog on 2022-02-17
So does journalctl -b give you any hints whats hanging the system??  I don't think xorg is installed by default on the Ubuntu server distribution.

---

### Post by MAFoElffen on 2022-02-18
Wait... You say you can connect to it via SSH? So it it booting the kernel if SSH is up and working as a service... Please confirm.

If not then a USB boot of a LiveCD. Then post the result of 
```

sudo fdisk -l
sudo lsblk
sudo ls /dev/mapper/

```
From the posted results of that, then we can aid you with instructions to mount the drive(s), chroot into it, and check journalctl and/or dmesg.

---

