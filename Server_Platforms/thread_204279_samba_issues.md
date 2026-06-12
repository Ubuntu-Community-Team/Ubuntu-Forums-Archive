---
title: "samba issues"
date: 2006-06-26
forum: Server Platforms
---

### Post by involutaryhaxor on 2006-06-26
I need some help with getting samba to work, i don't have any windows systems to share with, but I know how to use Samba.

The two machines in question are my Ubuntu 6.06 LAMP server and my Ubuntu 6.06 laptop.

I have samba running on my server, I did this by using the following commands:
apt-get install samba
apt-get install smbfs

When I try to connect to the server using samba with my laptop, it asks me for my password again. I assume that this means that it thinks that i gave it incorrect credentials? I added the users and everything with the smbpasswd command, what did I do wrong?

---

### Post by scxtt on 2006-06-26
```
smbpasswd $USER
```is all i've ever needed to do ...

---

### Post by DarthMandeep on 2006-06-26
What happens if you give it your password again?

---

### Post by Iowan on 2006-06-27
[QUOTE=involutaryhaxor] I assume that this means that it thinks that i gave it incorrect credentials? [/QUOTE] Did you send the server a password?

---

### Post by involutaryhaxor on 2006-06-28
[QUOTE=DarthMandeep]What happens if you give it your password again?[/QUOTE]

The same thing repeats again

---

### Post by involutaryhaxor on 2006-06-28
[QUOTE=Iowan]Did you send the server a password?[/QUOTE]

yes

---

### Post by ahobbs on 2006-06-28
Does this link help?
[http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users)

Or this one?
[https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html)

---

### Post by gerbman on 2006-06-28
Post your smb.conf file if you're still having problems.

---

### Post by involutaryhaxor on 2006-06-29
[QUOTE=ahobbs]Does this link help?
[http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_network_users)

Or this one?
[https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html)[/QUOTE]

Thankyou, the first one didn't literally help, but it made me look at my smb.conf, while I was thumbing through my smb.conf, I realised that it said that the accound that I was trying to connect with was blocked, I unblocked it, and I was able to log in. I still have one problem though, I don't know how to specify a samba share. The folder that I see when I connect is completely blank. If I could get some help with this, I would be all set.

---

### Post by gerbman on 2006-06-29
[QUOTE=involutaryhaxor]I still have one problem though, I don't know how to specify a samba share.[/QUOTE]By "specify" do you mean set it up in your smb.conf file? If so, here is the part of my smb.conf file that shares my second hard drive:```
[hd2]
path = /mnt/hd2
available = yes
browseable = yes
writable = yes
guest ok = no
```The name in brackets is the name of the share, path is where the drive is mounted, and the rest should be clear. Help any?

---

### Post by involutaryhaxor on 2006-07-01
[QUOTE=gerbman]By "specify" do you mean set it up in your smb.conf file? If so, here is the part of my smb.conf file that shares my second hard drive:```
[hd2]
path = /mnt/hd2
available = yes
browseable = yes
writable = yes
guest ok = no
```The name in brackets is the name of the share, path is where the drive is mounted, and the rest should be clear. Help any?[/QUOTE]

Thankyou, you are my hero of the week!

---

### Post by gerbman on 2006-07-01
[QUOTE=involutaryhaxor]Thankyou, you are my hero of the week![/QUOTE]Haha, cool :)

---

