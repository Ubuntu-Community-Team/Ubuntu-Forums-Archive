---
title: "Upgrading Servers"
date: 2009-12-09
forum: Server Platforms
---

### Post by Neil_948 on 2009-12-09
Hi all,
        I have just recently bought a new server everything is installed on my old one still but need to transfer the files for my web site and everything else to the new one does anyone know what i need to do as this would save me hours of having to manually changing and installing the new software again

thanks in advance

---

### Post by HighCommander540 on 2009-12-10
> **Neil_948 said:**
> Hi all,
        I have just recently bought a new server everything is installed on my old one still but need to transfer the files for my web site and everything else to the new one does anyone know what i need to do as this would save me hours of having to manually changing and installing the new software again

thanks in advance

All you need to do is go and back-up the .conf files. Then just replace them in the proper places on the new server. And make sure the permissions are all set right.

Then for your website files. Just tar.gz the /var/www/ directory. ANd move it over to the other server as well. If you are running MySQL or something. Just login to the databases and export them and then import them on the never server.

There really isn't an automated way to do this (like cmd "ubuntu server move").

---

### Post by munky99999 on 2009-12-10
Pretty much everything commander said.


Something you might try is to transfer all the files via a network. Using rsync or scp or sftp.

Or possibly this.

[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)

Personally havent tried this. But it appears to be a powerful one. Sadly it's still in development and not considered very stable.

---

