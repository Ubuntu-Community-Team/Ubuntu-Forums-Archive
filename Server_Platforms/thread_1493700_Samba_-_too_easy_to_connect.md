---
title: "Samba - too easy to connect?"
date: 2010-05-26
forum: Server Platforms
---

### Post by ottadini on 2010-05-26
Hi, I've got Ubuntu Server 10.04 on a static ip in my office. It has Samba.
I have a desktop linux box, Ubuntu 9.10.
I use several Windows boxes around the office as well. Some of them are joined to a domain, and some aren't. I don't fully understand the Windows domain setup!

I have configured Samba on the server to share out one directory. I have set ```
security = user
``` in smb.conf, and these lines for the share:
```
[public]
    comment = data
    path = /media/beta/test
    valid users = ben
    read only = No
    browseable = No
```To connect from a Windows box I use the "Map Network Drive" feature, and connect as a "different user", by specifying the username 'ben'. 

It doesn't matter what I set the "workgroup" parameter to (in the [globals] section of smb.conf), I can connect from Windows regardless.

Great! But why? I don't get it. I thought the workgroup parameter mattered. 

As background, I don't want anyone else to be able to access the share right now, just me. So I'm happy with it like it is, but just a bit confused.

ben.

---

### Post by Ryan Dwyer on 2010-05-26
I believe the workgroup is used by Windows for the auto-discoveration of network services.

---

### Post by Morbius1 on 2010-05-26
Having all the workgroup names match is a samba myth. I have 4 workgroups in my little home network and although browsing is a little awkward, since the machines don't all show up in one neat listing, everything works fine.

---

### Post by ottadini on 2010-05-26
> **Morbius1 said:**
> Having all the workgroup names match is a samba myth. I have 4 workgroups in my little home network and although browsing is a little awkward, since the machines don't all show up in one neat listing, everything works fine.

Is that because all your machines share a subnet?
Do you just set your share to have 'browseable = yes', and Windows networking sees them? Regardless of workgroup? Some of the PCs in my place are joined to a domain, think it's the same? 

Do you have to specify a WINS server in your smb.conf?

ben.

---

### Post by capscrew on 2010-05-26
> **ottadini said:**
> Is that because all your machines share a subnet?
Do you just set your share to have 'browseable = yes', and Windows networking sees them? Regardless of workgroup? Some of the PCs in my place are joined to a domain, think it's the same? 

Do you have to specify a WINS server in your smb.conf?

ben.

Browsing for samba shares has nothing to do with authenticating to a AD or Samba PDC domains.  Think of the term domain as "*a collection of like objects*".  The Browse Domain is just that, a group of objects (samba resources) with the same umbrella name (MyWorkgroupName).  You can have as many of these workgroups as you want.

I believe that you will find that the problems that folks are having with seeing and connecting to these resources is due to a lack of consistent naming services in their networks.  Windows clients provide their own COMPUTER names (broadcast) but Linux hosts do not.  Samba can provide  names this way or can use WINS or can use DNS.  Take you pick, but you need to use something.  I personally use DNS for my entire network, but I still see the NetBIOS broadcasts of names from my Windows hosts (Vista and XP).

Once the name services are set up the Browse Master in Samba will see the hosts by name and find out what the IP address is.

---

