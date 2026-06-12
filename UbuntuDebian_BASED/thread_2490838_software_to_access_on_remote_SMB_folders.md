---
title: "software to access on remote SMB folders"
date: 2023-09-18
forum: Ubuntu/Debian BASED
---

### Post by WhiteTigerIT on 2023-09-18
I'm looking for a "Debian-Based" software to access remote Samba SMB folders.
I don't want to use Nautilus, but something independent that, if necessary, I can also install on other distributions without thinking about integration with the operating system.
Users use Ubuntu, Xubuntu, Debian and Raspberry. This tool has to be something independent that I can install anywhere and that everyone knows how to use in the same way.


Thanks in advance for the help.

---

### Post by TheFu on 2023-09-18
How remote?  On the same LAN is fine.  Over the internet is not.  CIFS isn't safe over the internet. You need encryption for that, which is something CIFS does well.

You can use **smbclient**.

If you want to do this the LInux way, use **sftp** or **sshfs** or NFS.  NFS does work at the kernel level, so it probably doesn't meet your needs. sftp is probably already installed on both sides and **sshfs** is a tool that let's users remotely mount storage accessible by ssh.  Then it looks like local storage, until umounted.

[https://askubuntu.com/questions/975818/how-do-i-specify-ssh-options-for-sshfs](https://askubuntu.com/questions/975818/how-do-i-specify-ssh-options-for-sshfs) explains, but most of the time, to use sshfs
```
cd ~
mkdir remote
sshfs pete@192.168.33.10:/path/to/directory   ~/remote
```
Then use the "~/remote" directory like it was local.
When done, don't forget the umount the storage ... or just shutdown the computer.
```
fusermount -u ~/remote
```
Any programs can access the mounted storage and use it like it was local. Obviously, if the storage is across the country, the performance will reflect that difference.  On a LAN, it is fast.  Oh ... and something that should go without saying, but the user needs to have ssh access to the remote storage.

---

### Post by WhiteTigerIT on 2023-09-18
Yes, they are both on the same local network.
I need it with GUI, not to use it with command line (as the File Explorer in Windows).

---

### Post by Morbius1 on 2023-09-18
The closest thing I can think of that comes close to your use case is an application called Gigolo.

```
sudo apt install gigolo
```

It can do both SMB and SSH and a few other things. It can even be set up to automount.

It uses the same bakend as Nautilus, Caja, Nemo, Thunar ... so I don't know how it would fit in with a KDE system.

---

### Post by TheFu on 2023-09-18
Beware that almost all GUI tools that will connect to CIFS will have dependencies that are almost the same as what Nautilus has. 
> gigolo is frontend to manage connections to remote filesystems using GIO/GVfs

Short of writing your own front-end to **gio** CLI commands, I don't know how to get a self-contained solution. 
On KDE/LXQt systems, I'd bet they use **kio** [https://api.kde.org/frameworks/kio/html/](https://api.kde.org/frameworks/kio/html/). 

> The KDE manual app KHelpCenter has a KIOSlaves section that lists the available protocols with a short description of each.
See also

    GIO and GVfs &#8211; provides equivalent functionality for GNOME, XFCE and Cinnamon

---

### Post by SeijiSensei on 2023-09-18
If all your users are running flavors of Linux, don't use CIFS unless the shared files are on a Windows server. If they are on a Linux server, you should be using NFS. 

Install the nfs-kernel-server package on the server, and nfs-common on the clients. Then add the directories you want to export to /etc/exports, and start the server. On the clients, add entries to /etc/fstab to mount the remote directories into the local file system when the system boots. Then you can access the remote directories using ordinary file browsing tools like dolphin.

Do some searching for "ubuntu nfs". You'll find lots of help.

---

