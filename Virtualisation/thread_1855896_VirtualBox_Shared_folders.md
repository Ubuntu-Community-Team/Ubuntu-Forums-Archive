---
title: "VirtualBox Shared folders"
date: 2011-10-07
forum: Virtualisation
---

### Post by gtrennert on 2011-10-07
Hello,
Ubuntu-10.04.3-server (french)
VirtualBox-4.1.4-74291-Win.exe
I have installed Ubuntu server as guest on a windows XP system
Now I need to get access to a shared folder between the 2 systems.
dkms is installed
I added the vboxguestadditions (but I can't see any effect of this one)

But I allways get an error on the 2 following instructions :

sudo mount -t vboxsf Shared /mnt/shared : "mount : type inconnu de systeme de fichier 'vboxsf'" , means unknown filesystem vboxsf

sudo mount.vboxsf Shared /mnt/shared : Command not found

Can somebody help me to get this work ?

---

### Post by matt_symes on 2011-10-07
Hi

Does this help ?

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

Did you reboot ?

Kind regards

---

### Post by gtrennert on 2011-10-07
Thanks for your help !
I don't know very much about the linux filesystem

I tried both :

cd /cdrom ok, but the sh command : sh: can't open VBoxLinuxAdditions-x86.run

and in /media, there is nothing (ls)

So I wonder if there is anywhere the vbox iso 
I checked in the VB menu : under devices / CD-Ropm : I see that VBoxGuestAdditions.iso is checked

I must have missed something, but what !

---

### Post by Morbius1 on 2011-10-07
Open up VBox then: Devices > Install Guest Additions

This will mount the Additions iso. It should run automatically but if it doesn't it should be under /media/VBOXADDITIONS.....

So:
cd /media/VBOXADDITIONS.....
sudo sh VBoxLinuxAdditions.run

Once you install it you no longer have to do any manual mount it's automatically mounted at:
> /media/sf_*share-name*You may get an error because you are not a member of the vboxsf group so you will need to add yourself:
```
sudo gpasswd -a username vboxsf
```Then logout and login again.

---

### Post by matt_symes on 2011-10-07
Hi

Do you have it as a module ?

What do these return ?

```
modprobe -l vboxsf
```

That is a small L above.

... and this ...

```
lsmod | grep vboxsf
```

and this..

```
cat /proc/filesystems
```

Kind regards

---

### Post by gtrennert on 2011-10-07
> Open up VBox then: Devices > Install Guest Additions

This will mount the Additions iso. It should run automatically but if it doesn't it should be under /media/VBOXADDITIONS.....
This is what I did but there is nothing at all in /media !

> modprobe -l vboxsf
Nothing

> lsmod | grep vboxsf
Nothing

> cat /proc/filesystems
see attached png file

---

### Post by CharlesA on 2011-10-07
I seem to recall that the guest additions require a DE to install.

Also, Ubuntu server doesn't auto mount like Ubuntu desktop does from what I remember. So you'll have to mount the iso manually and then try to install it that way.

---

### Post by gtrennert on 2011-10-07
Sorry but what is DE ?

Can you tell me how mount the iso manually ?

---

### Post by CharlesA on 2011-10-07
> **gtrennert said:**
> Sorry but what is DE ?

Can you tell me how mount the iso manually ?
DE = Desktop environment.

Just mount the ISO in virtualbox then mount it somewhere using mount:

```
sudo mount /dev/cdrom /path/to/somefolder/
```

---

### Post by gtrennert on 2011-10-07
OK - here's what I got - in the end something got wrong "...failed"

---

### Post by gtrennert on 2011-10-07
on modprobe -l vboxsf I now get :
updates/dkms/vboxsf.ko

on lsmod | grep vboxsf I now get :
vboxsf       35947 0
vboxguest   196072 2 vboxsf

on cat /proc/filesystems I now get 2 more lines :
        iso9660
nodev   vboxsf

---

### Post by CharlesA on 2011-10-07
Try connecting to the share manually - it should work now.

```
mount -t vboxsf sharename /path/to/mountpoint
```

---

### Post by matt_symes on 2011-10-07
Hi

> **gtrennert said:**
> on modprobe -l vboxsf I now get :
updates/dkms/vboxsf.ko

on lsmod | grep vboxsf I now get :
vboxsf       35947 0
vboxguest   196072 2 vboxsf

on cat /proc/filesystems I now get 2 more lines :
        iso9660
nodev   vboxsf

That looks a lot better. Follow CharlesA's advice and manually mount and you should be good to go.

Kind regards

---

### Post by gtrennert on 2011-10-08
OK Nice - thank you so much :) - so I followed your new advice :
mount -t vboxsf partagevb /mnt
(I don't know if /mnt is a good idea but Idon't know very much about the linux filesystem)
I thought that now I would find the shared folder in /mnt, but there is only 'cdrom' - which seems to be empty

When I have a look at mount I see this entry at the end :
partagevb on media/sf_partagevb type vboxsf (gid=1001,rw)

But :
cd /media/sf_partagevb => Permission non accordée
sudo cd /media/sf_partagevb => cd : command not found
sudo ls /media/sf_partagevb => Here I can see the file that I have copied in windows in the shared folder

So I think the shared folder is there, I only don't know how to get easy access to this folder (for exemple to decompress the file etc)

cd /media

---

### Post by CharlesA on 2011-10-08
uid and guid should be 1000.

---

### Post by Morbius1 on 2011-10-08
> So I think the shared folder is there, I only don't know how to get easy  access to this folder (for exemple to decompress the file etc)
Are you or are you not using a desktop environment on this server - Gnome?
> **CharlesA said:**
> uid and guid should be 1000.
VBox starting with Version 4 will automatically mount these shares to "/media/sf_*whatever*" with root as owner and group as vboxsf. The gid of vboxsf is 1001. There is no longer any need to mount these shares manually or through fstab.

---

### Post by CharlesA on 2011-10-08
> **Morbius1 said:**
> 
VBox starting with Version 4 will automatically mount these shares to "/media/sf_*whatever*" with root as owner and group as vboxsf. The gid of vboxsf is 1001. There is no longer any need to mount these shares manually or through fstab.

Oh thanks. Good to know.

---

### Post by gtrennert on 2011-10-08
There is no desktop environment installed on this server - should I ?
Now my question is how to easily access the shared folder on the command line ...

---

### Post by Morbius1 on 2011-10-08
We all do seem to be avoiding that question don't we.

Well in this universe it would be something like this:
```
 cd /media/sf_partagevb
```But when you do it you get this:
>  cd /media/sf_partagevb => Permission non accordéeWhich I believe is "Permission denied"

So my guess is that you are not a member of the vboxsf group. To fix that:
```
sudo gpasswd -a your-user-name vboxsf
```Then you will have to logout ( of the VBox guest ) and login again for the group membership to take affect.

---

### Post by gtrennert on 2011-10-08
Thanks for all your help !
Now I can go on to other subjects ... :)

---

