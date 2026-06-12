---
title: "SAMBA question -- XP w/no password"
date: 2006-06-06
forum: Server Platforms
---

### Post by peter1632 on 2006-06-06
I have three PCs on our home network.  All are
XP Pro.  None use passwords (house rules!).  I've
also got a Linux box running (obviously) Ubuntu
Dapper LTS.

When setting up SAMBA, is it necessary that the XP
boxes have passwords set?  If not then in the [FONT="Courier New"]smb.conf[/FONT]
in the [FONT="Courier New"][global][/FONT] section do I set
[FONT="Courier New"]encrypt passwords = no[/FONT]
or leave it blank?  and can I skip the
[FONT="Courier New"]# smbpasswd -a <whomever>[/FONT]
steps?

With thanks...

---

### Post by puelly on 2006-06-06
open the /etc/samba/smb.conf file and go to the Authentication section.  Search for the line that has "security = user" and change it to "security = share".  This will allow you to access samba shares without passwords.

---

### Post by cyracks on 2006-06-07
[quote=peter1632]
When setting up SAMBA, is it necessary that the XP boxes have passwords set?  
[/quote] No
[quote=peter1632]
If not then in the [FONT=Courier New]smb.conf[/FONT] in the [FONT=Courier New][global][/FONT] section do I set
[FONT=Courier New]encrypt passwords = no[/FONT]
or leave it blank? 
[/quote] It is better to leave it as it is (yes) if you decide in the future to use passwords. This option does not prevent you using a blank passwords it just encrypts the password when it is send from on computer to another and windows XP support that option.
[quote=peter1632]
 and can I skip the
[FONT=Courier New]# smbpasswd -a <whomever>[/FONT]
steps?
With thanks...[/quote] No, you need to add every user to the samba registry, except if you use "security = share"

---

### Post by Ixzat on 2006-06-07
Hi there, my first post here...

I have just set up a ubuntu dapper server and started fiddling with samba aswell. I have the same setup, passwordless that is. However samba prevents me from writing to the shares i have. Reading and browsing the shares works like a charm though. I have modified the [E] section to start with, but i cant get it to work.

Heres my smb.conf with comments removed:
```
[global]
   workgroup = MSHOME
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = share
   encrypt passwords = true
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY


[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
   create mask = 0664
   directory mask = 0775
   wins support = no

[E]
path = /mnt/E
comment = E Disken
available = yes
browseable = yes
public = yes
writable = yes
force user = nobody
force group = nogroup
create mask = 0777
directory mask = 0777

[F]
path = /mnt/F
comment = F Disken
available = yes
browseable = yes
public = yes
writable = yes

[G]
path = /mnt/G
comment = G Disken
available = yes
browseable = yes
public = yes
writable = yes

[H]
path = /mnt/H
comment = H Disken
available = yes
browseable = yes
public = yes
writable = yes

```

---

### Post by cyracks on 2006-06-07
[quote=Ixzat]
```

[E]
path = /mnt/E
comment = E Disken
available = yes
browseable = yes
public = yes
writable = yes
force user = nobody
force group = nogroup
create mask = 0777
directory mask = 0777

```[/quote] Try this and then test if you can write to /mnt/E
```

sudo chown nobody.nobody /mnt/E
or 
sudo chmod 777 /mnt/E

```

---

### Post by Ixzat on 2006-06-07
Worked like a charm with chown, however it should be nobody.nogroup, not nobody.nobody.

Thanks alot!

---

