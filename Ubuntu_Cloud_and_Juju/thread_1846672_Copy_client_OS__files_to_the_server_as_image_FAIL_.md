---
title: "Copy client OS  files to the server as image FAIL !"
date: 2011-09-19
forum: Ubuntu Cloud and Juju
---

### Post by refz on 2011-09-19
i'm trying to make a image of my client OS files but fail. this is result :
> server@server-VGN-CR35G-W:~$ sudo mount -t nfs -onolock 192.168.2.10:/nfsroot /mnt
mount.nfs: Connection timed out 

what should i do?

my server has run dhcp server, and that ip on client.

---

### Post by refz on 2011-09-19
i'm taking a tutorial from this site :

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

please help me...

---

### Post by kim0 on 2011-09-21
maybe make sure the nfs service is up on the server side
make sure no firewall is blocking the connection ...etc

---

