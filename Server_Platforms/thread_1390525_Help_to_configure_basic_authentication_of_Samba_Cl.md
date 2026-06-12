---
title: "Help to configure basic authentication of Samba Client"
date: 2010-01-25
forum: Server Platforms
---

### Post by frenchn00b on 2010-01-25
Hello

I have a running server samba. The problem now is to configure the login/password database of the client/workstations to this unique samba password/user samba server. 

So the configuratino of hte client:

```
[global]
   guest account = nobody
   invalid users = root
   encrypt passwords = yes
   security = server
   password server = 192.168.10.10
   workgroup = WORKGROUP
   server string = %h server (Samba %v)
   preserve case = yes
   short preserve case = yes
[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = no

```
is that right?

nsswitch.conf
```
passwd: compat 
group: compat
shadow: compat
```

which packages shall I install?
I do : 
> su french00b
 and it says on the client : no id
since it has apparently looked on server samba, which has my username :(
ANY HELP PLEASE?

---

