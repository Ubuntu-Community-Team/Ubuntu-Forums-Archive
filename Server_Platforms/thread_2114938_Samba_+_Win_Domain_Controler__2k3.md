---
title: "Samba + Win Domain Controler  2k3"
date: 2013-02-11
forum: Server Platforms
---

### Post by michasio on 2013-02-11
Hello,

May I ask You for help. I have some problem, I tried to find answer in internet but without any effects.
I have HP DL380 with installed Ubuntu, Samba and other. I want to configure Samba to keep users data, but not "My Documents".  For example: "Department share - Production Department, Warehouse Department, etc."
I don't known how to configure Samba server to protect department folder using Windows Domain users. 
I spent some time on manuals, but there was only information how to add Linux machine to Windows AD, and log in, and grant rights to user's folder. 
I don't want do this, I need create department folder and use domain accounts to protect. Of course I can add users in Linux and use this account in Windows to open some shares, but this not for me.
Next question is, where should I add permissions to some folders, from Linux console or by right clicking in windows, properties and security???
Maybe You have some manual which I can use? ;)

Many thanks for help
Regards
michal

---

### Post by koenn on 2013-02-11
>  spent some time on manuals, but there was only information how to add Linux machine to Windows AD, and log in, and grant rights to user's folder. 
because you want to use AD accounts (good choice, btw), that is exactly what you need ; join the samba server to the domain and do the required config to get the accounts from the 2k3 DC.

Then, in stead of "user flders", create shares (standard Samba procedure) and set access controll by  using the domain accounts

[https://help.ubuntu.com/10.04/serverguide/likewise-open.html](https://help.ubuntu.com/10.04/serverguide/likewise-open.html)
[https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html#samba-fileserver-configuration](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html#samba-fileserver-configuration)

using AD accounts means adding somthing like this
```
valid users = @"ADDOMAIN\\YourADGroup", @"ADDOMAIN\\YetAnotherADGroup"
```
to a share definition. You may need to look that up, I'm not 100% sure of the correct syntax

---

