---
title: "Shared folders problem"
date: 2012-01-29
forum: Virtualisation
---

### Post by claude1984 on 2012-01-29
Virtualbox, host Ubuntu 10.04 guest is also Ubuntu 10.04.

Guest additions are installed. Only that was quite an adventure.... 

Added a shared folder with the VirtualBox manager.

When I open the machine.... of course..... it doesn't work. Would be to easy.. Why make things simple :(](*,)

Shared folder doesn't appear in /media/..... Or anywhere else.. 

So.... what complicated terminal sudo bla bla bla line is missing ?

---

### Post by claude1984 on 2012-01-29
Found this with the help of Google:

"
If you've used the GUI tool to share a folder with your Ubuntu guest  machine, you probably are confused why it's not showing up anywhere. 
The problem is that you need to run a command to make it show up.  First, create a mount point, and then use the special mount syntax to  actually "map" the folder to the shared VirtualBox folder. 
 sudo mkdir /media/vboxshared  Now you can map the folder using the share name that you setup earlier in VirtualBox 
 sudo mount -t vboxsf SHARENAME /media/vboxshared "





Because things are never simple with Linux, it doesn't work!! Driving me insane...

Now, in media, the folder appears, but when I enter it, it's empty..... uuuugggh..

---

### Post by japzone on 2012-01-30
If you continue to have problems, one solution is to use SMB(Windows File Share) file sharing to share files between Host and Guest which you can install by entering in Terminal:
```
sudo apt-get install samba
``` and then Right-Click the Folders you want to share and Click Sharing Options, and then access them via "Network-->Windows Shares-->WORKGROUP"

Or you can setup an FTP server on the Host/Guest you want to access and then use an FTP Client on the Host/Guest you're on to Copy and Move files between the Two(Switching the Network Adapter in the VM settings to "Bridged" makes this easier as your Guest will appear on your Home Network like a Real PC)

---

### Post by Morbius1 on 2012-01-30
What version of VirtualBox are you using? Since V4 VBox automatically mounts the shared folder you created at:
> /media/sf_sharename
The "sf_" indicating the VBox shared folder.

Maybe something got discombobulated with the guest additions.

---

