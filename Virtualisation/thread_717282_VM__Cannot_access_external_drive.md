---
title: "VM / Cannot access external drive"
date: 2008-03-06
forum: Virtualisation
---

### Post by stevegarriques on 2008-03-06
I created a VM and I have a backup drive connected to a windows machine in which I shared to the linux machine (Using Samba). 

Now as ROOT I can read and write to the share /media/backupdrive (actually on a windows server)

Now I need another user to have access to the drive / to have write access

I have tried chown, chmod, even found out how to give a regular user root access and can't figure out how to give a normal user access to the windows shared drive

Anyone know how I could resolve this?

---

### Post by fjgaude on 2008-03-06
Use this to add a Share password to the system:

```
sudo smbpasswd -a newusername
```

Enter their password when asked.

Seems like this should do the trick.

---

### Post by stevegarriques on 2008-03-10
Bit confused cuz I don't need a password when doing from root

I can mount the drive using any username but just can't write to it

Here is the command I use:

smbmount //Server/Share /media/Share -o username=WindowsDomain\\user,password=$MYPASS

that works, but can't get any user besides root to write to share

---

