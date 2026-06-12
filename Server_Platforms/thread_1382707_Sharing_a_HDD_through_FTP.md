---
title: "Sharing a HDD through FTP"
date: 2010-01-16
forum: Server Platforms
---

### Post by stacked on 2010-01-16
I installed ubuntu 9.10 on a spare computer for misc. backups through ftp. I successfully setup up ftp and logged as an account from the server. Also I mounted the larger hardrive to a folder in my home directory.

I am able to successfully write and read to the partition in which the operating system is installed through ftp, but I am only able to read from the larger HDD through ftp.

Does anyone know how I can become able to write to the mounted drive through ftp?

At the moment when I try accomplishing this task it sends an error stating "Operation Failed".

---

### Post by bsh on 2010-01-16
what ftp server is that?
you are logging in to the ftp server with your local user on the machine running the ftp server?
if yes, than that user has no write permissions for the mount point where the hard disk is installed, or the disk was mounted read only.

---

### Post by stacked on 2010-01-16
> **bsh said:**
> what ftp server is that?
you are logging in to the ftp server with your local user on the machine running the ftp server?
if yes, than that user has no write permissions for the mount point where the hard disk is installed, or the disk was mounted read only.

I am using **vsftpd** as recommended in the ubuntu server manual.
Yes I am logging on as a local user, also I will check the write permissions.

I hope this works.

Thank you BSH. The command below did the trick.

```
sudo chmod o+w ~/stash
```

---

### Post by Lars Noodén on 2010-01-18
> **stacked said:**
> I am using **vsftpd** as recommended in the ubuntu server manual.

OH! That's where that is coming from.  I had been wondering where people were getting encouragement to use FTP.  Did you get it from section "*13. File Servers: FTP Server*" in the 9.10 manual?

[https://help.ubuntu.com/9.10/serverguide/C/](https://help.ubuntu.com/9.10/serverguide/C/)

If not, where?

---

