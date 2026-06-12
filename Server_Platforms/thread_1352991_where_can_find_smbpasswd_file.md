---
title: "where can find smbpasswd file"
date: 2009-12-12
forum: Server Platforms
---

### Post by OYY on 2009-12-12
I'm sorry about it..because i try to add user to samba server.. with smbpasswd command it succesful add the user but the problem are i couldn't find out the smbpasswd file in directory /etc/samba/. i don't know why it doesn't exit at there..version of ubuntu i use is 9.04.

---

### Post by Tr1p on 2009-12-12
is this a real question ?????

locate it then our make one

---

### Post by Muttley99 on 2009-12-12
[HTML]sudo find / -name smbpasswd
[/HTML]

---

### Post by OYY on 2009-12-12
i try already to created the smbpasswd file by myself with command pico smbpasswd in /etc/samba/. but the samba paasword still doesn't write to this file.. i don't know what happen..hope you all can give me a hand... to solve this.

---

### Post by Iowan on 2009-12-13
My samba server doesn't list */etc/samba/smbpasswd* either - yet it works. The binary is at */user/bin/smbpasswd*.  My smb.conf file suggests tdbsam as the password file.

I found [this]("http://ubuntuforums.org/showthread.php?t=23616") related thread.

---

### Post by koenn on 2009-12-13
> **Iowan said:**
> My samba server doesn't list */etc/samba/smbpasswd* either - yet it works. The binary is at */user/bin/smbpasswd*.  My smb.conf file suggests tdbsam as the password file.

makes sense 
[http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/18_passdb_21.html](http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/18_passdb_21.html)

---

