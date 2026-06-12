---
title: "Question of samba in ubuntu 9.10"
date: 2009-11-12
forum: Server Platforms
---

### Post by cpthk on 2009-11-12
I just upgraded to ubuntu 9.10. I found that in samba, They updated the smb.conf with some minor changes. I have noticed they updated the:
```
encrypt passwords = no
```
I remember in 9.04, this value should be true.
I don't really understand why they do that. For windows newer than 2000, the passwords should be encrypted. Anyone know why they change to no?

Thanks.

---

### Post by lykwydchykyn on 2009-11-12
This doesn't seem to be the case for me.  Encrypt passwords is set to "true", and I believe my smb.conf is default.

Encrypting passwords is a question during the configuration of samba-common, which I believe defaults to true.

---

### Post by cpthk on 2009-11-13
But even I copy default one from /usr/share/samba/, it is still no be default. Or is it possible that /usr/share/samba/smb.conf is not really default?

---

### Post by capscrew on 2009-11-13
> **cpthk said:**
> But even I copy default one from /usr/share/samba/, it is still no be default. Or is it possible that /usr/share/samba/smb.conf is not really default?

In most cases if you leave out any parameter in the smb.conf, the default is what is used

All of the parameter defaults are listed in the man pages for smb.conf.  See ```
man smb.conf
```

Here is the relevant portion of the man pages on my host for this issue```
 encrypt passwords (G)
          This boolean controls whether encrypted passwords will be negotiated
          with the client. Note that Windows NT 4.0 SP3  and  above  and  also
          Windows  98 will by default expect encrypted passwords unless a reg&#8208;
          istry entry is changed. To use encrypted passwords in Samba see  the
          chapter "User Database" in the Samba HOWTO Collection.

          MS  Windows  clients  that  expect Microsoft encrypted passwords and
          that do not have plain text password support enabled will be able to
          connect  only  to a Samba server that has encrypted password support
          enabled and for which the user accounts have a valid encrypted pass&#8208;
          word.  Refer  to  the  smbpasswd  command  man  page for information
          regarding the creation of encrypted passwords for user accounts.

          The use of plain text passwords is NOT advised as support  for  this
          feature  is  no  longer maintained in Microsoft Windows products. If
          you want to use plain text passwords you must set this parameter  to
          no.

          In  order  for  encrypted  passwords  to work correctly smbd(8) must
          either have access to  a  local  smbpasswd(5)  file  (see  the  smb&#8208;
          passwd(8) program for information on how to set up and maintain this
          file), or set the security  =  [server|domain|ads]  parameter  which
          causes smbd to authenticate against another server.

          [COLOR="Red"]**Default: encrypt passwords = yes**[/COLOR]

```

---

