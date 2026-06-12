---
title: "[SOLVED] Unable to install VirtualBox Addons on Ubuntu 6.06"
date: 2008-02-06
forum: Virtualisation
---

### Post by Vadi on 2008-02-06
> vadi@vadi-laptop:/media/cdrom$ ls
AMD_PCnet    driver  os2                     VBoxLinuxAdditions.run
AUTORUN.INF  gina    VBoxGuestAdditions.exe
vadi@vadi-laptop:/media/cdrom$ sudo ./VBoxLinuxAdditions.run
Password:
sudo: unable to execute ./VBoxLinuxAdditions.run: Permission denied
vadi@vadi-laptop:/media/cdrom$ chmod +x VBoxLinuxAdditions.run
chmod: changing permissions of `VBoxLinuxAdditions.run': Read-only file system
vadi@vadi-laptop:/media/cdrom$ sudo ./VBoxLinuxAdditions.run
sudo: unable to execute ./VBoxLinuxAdditions.run: Permission denied
vadi@vadi-laptop:/media/cdrom$ ./VBoxLinuxAdditions.run
bash: ./VBoxLinuxAdditions.run: /bin/sh: bad interpreter: Permission denied
vadi@vadi-laptop:/media/cdrom$


Someone help please?

---

### Post by Jose Catre-Vandis on 2008-02-06
Are you sure you have correctly mounted the VBoxGuestAdditions.iso within your Ubuntu guest? (this iso is located on your hard drive on your host) Does your user have permissions to run sudo? You won't be able to change permissions for files on the iso if loaded.

---

### Post by Vadi on 2008-02-06
I don't know. I just used the "Install VirtualBox Addons" option on top, and it loaded the iso.

Is there anything I can check?

---

### Post by FrostiEE on 2008-02-07
First, mount the iso file by going to the Devices menu(In VirtualBox) and then choosing "Install Guest Additions". Then cd to /media/cdrom in Ubuntu.
Then try this command:
```
sudo sh VBoxLunuxAdditions.run
```

---

### Post by Nimmirraj on 2008-08-14
I was having the same issue with Feisty.  The resolution I found was to use the command: "sudo sh /media/cdrom/VBoxLinuxAdditions.run"

Hope this helps....

---

