---
title: "Set Complete FTP Access"
date: 2017-11-13
forum: Security
---

### Post by luigimdg on 2017-11-13
Hi..
On Ubuntu 16.04 Server I've created a new user, setted *username ALL=(ALL:ALL) ALL* in the *sudoers *and sudo privileges and installed and configured the firewall (*UFW*)..
But now I've a problem with specific folders with the new user..!
I want complete FTP access with this user to manage all folders and files..
How to do this? :roll:

---

### Post by cariboo on 2017-11-13
It would be much safer to use ssh as ftp is not very secure. I use it and sftp to manage a couple of servers and two raspberry pi's.

Just install openssh-serve on the system you want to access, and follow [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") to set up private key access.

---

### Post by luigimdg on 2017-11-13
Yes.. I've OpenSSH with public key and I want to set all access for added user and disable the PermitRootLogin..

---

### Post by luigimdg on 2017-11-16
[COLOR=#333333][FONT=Ubuntu]I can connect with another user, but I can't edit files.. I've try to login with *root* but they take to me *access denied*.. I've installed *vsFTPd* to manage access and setted */etc/vsftpd.conf*: 
> local_enable=YES
write_enable=YES
chroot_local_user=YES[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I've delete *root* from file */etc/ftpusers* but no success.. All is equal of before installing *vsFTPd*.. I've launched a *restart*..[/FONT][/COLOR]

---

### Post by cariboo on 2017-11-17
Use sudo once you have logged on to your remote system.

---

### Post by luigimdg on 2017-11-18
> **cariboo said:**
> Use sudo once you have logged on to your remote system.
Use sudo?
I'm trying to connect with FTP, not with SSH...

---

### Post by cariboo on 2017-11-18
I suggested using ssh, as FTP is insecure, even more so if you try to log in as root. Once anyone logs in a root, they can do what they want. I'd suggest disabling FTP, and use ssh/sftp for everything.

---

