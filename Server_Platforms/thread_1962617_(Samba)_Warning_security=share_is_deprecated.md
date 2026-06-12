---
title: "(Samba) Warning: security=share is deprecated"
date: 2012-04-21
forum: Server Platforms
---

### Post by jlacroix on 2012-04-21
Hi guys. I'm almost done with my new file server. One of the functions it provides is a share for Clonezilla via Samba that both Linux and Windows machines need to access, as I image all my desktops and laptops to this share.

I noticed when running "testparm" that it tells me that security=share is deprecated. So, I removed security=share from smb.conf, and my share for Clonezilla no longer functions, so I had to add it back.

My question is, how do I address security=share being deprecated but still retain the exact same functionality? My /images share needs to be accessible to all, regardless of the username, and should never ask for password. Here are the config files:

smb.conf:
```
[global]
server string = File Server
workgroup = LITTLEBIGPLANET
security = share
name resolve order = bcast hosts wins
client lanman auth=Yes
wins support = yes
include = /etc/samba/smbshared.conf

```

smbshared.conf:
```
[Images]
        path = /home/iris/HDD Images
        force user = iris
        read only = No
        guest ok = Yes

```

---

### Post by Morbius1 on 2012-04-21
The current equivalent for your purposes of "security = share" are the following 2 lines:

```
security = user
map to guest = Bad User
```The remote user name will be compared to the one found in the samba password database and if it doesn't find a match it will be tagged a "Bad User" and mapped to the guest account. 

The guest account by default is nobody:
```
testparm -sv /dev/null | grep "guest account"
```There are some peculiar and very rare bugs however that show up from time to time that can be worked around by using "security = share". The developers insist they will remove the "share" option in the very next update but they have been saying that for 4 years now so maybe Samba4 will finally remove it :wink:

**EDIT**: I should have also noted that is you don't add "map to guest = Bad User" it defaults to "map to guest = Never".
```
testparm -sv /dev/null | grep "map to guest"
```

---

### Post by jlacroix on 2012-04-21
> **Morbius1 said:**
> The current equivalent for your purposes of "security = share" are the following 2 lines:

```
security = user
map to guest = Bad User
```The remote user name will be compared to the one found in the samba password database and if it doesn't find a match it will be tagged a "Bad User" and mapped to the guest account. 

The guest account by default is nobody:
```
testparm -sv /dev/null | grep "guest account"
```There are some peculiar and very rare bugs however that show up from time to time that can be worked around by using "security = share". The developers insist they will remove the "share" option in the very next update but they have been saying that for 4 years now so maybe Samba4 will finally remove it :wink:

**EDIT**: I should have also noted that is you don't add "map to guest = Bad User" it defaults to "map to guest = Never".
```
testparm -sv /dev/null | grep "map to guest"
```
Ok, so I don't add map to guest to smb.conf, right?

---

### Post by Morbius1 on 2012-04-21
If you use "security = user" you must add "map to guest = Bad User".

---

### Post by jlacroix on 2012-04-21
> **Morbius1 said:**
> If you use "security = user" you must add "map to guest = Bad User".
Thank you, I'll start testing this right now.

Edit: So far, so good. Thanks!

---

### Post by freesbee on 2012-10-11
> **Morbius1 said:**
> If you use "security = user" you must add "map to guest = Bad User".
I'm sorry: there is something that I am missing.
I also need to setup a "public folder" writable by anybody without any passwd check. If I do not use "security = share" I get immediately asked for username/password when trying to browse the public folder.
Here is my smb.conf

```

[global]
 workgroup = MyWorkgroup
 server string = %h Samba Server
 security = user
 map to guest = Bad User
 obey pam restrictions = Yes
 pam password change = Yes
 passwd program = /usr/bin/passwd %u
 passwd chat = *Enter\snwe\s*\spassword:* %n\n *retype\snew\spassword:* %n\n *password\supdated\ssuccesfully* .
 unix password sync = Yes
 syslog = 0
 log file = /var/log/samba/log.%m
 max log size = 1024
 dns proxy = No
 usershare allow guests = Yes
 panic action = /usr/share/samba/panic-action %d

[public]
 path = /usr/pub/share
 browsable = Yes
 guest ok = Yes
 read only = No
 create mask = 0755
 directory mask = 0755
 force user = nobody
 force group = nogroup
```
Can anybody give me a hint in the right direction?

---

### Post by Morbius1 on 2012-10-12
> security = user
map to guest = Bad UserLet's take as an example a Windows client. The same thing will happen with a Linux client but you have to go out of your way to make that happen in Linux. In Windows the client's username and password is automatically sent when it browses for shares - this is done without the user's knowledge. That forces Samba to deal with the sent credentials even though it's a guest share that requires no authentication.

When that username is passed Samba will search through it's password database for that user:

* If there is no match to the username the client user is tagged a "Bad  User" and converted ( mapped ) to the guest account which by default is  "nobody".

* If it finds a match to the username and there is a samba password that matches the one sent by the Windows client then the Windows user automatically gains access although not as an anonymous user which is why you needed to add "force user = nobody" to your share definition.

* If it finds a match to the username but the samba password does not match exactly the password that's automatically sent by the Windows client then you will be prompted for a password - even for a guest share.

If all you have is that one guest share then check the samba password database:
```
sudo pdbedit -w -L
```If you have an entry for that remote user either make sure the samba password matches the remote users password exactly or simply remove the samba user from the database:
```
sudo smbpasswd -x user-name
```

---

