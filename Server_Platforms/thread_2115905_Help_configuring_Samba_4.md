---
title: "Help configuring Samba 4"
date: 2013-02-14
forum: Server Platforms
---

### Post by cody1233 on 2013-02-14
OK, so I am a complete ubuntu server newb and I am running 12.04 LTS.  I am trying to get Samba 4 running only as a file sharing server with the users on the computer signing in as themselves.  I have tried manually editing the smb,conf, but I still can't get it to show up on my windows computers.  There are no network problems between the computers, so it has to be the config.  (and yes, I restarted the program after updating the config)

Can anybody help me with the options I need to enable or a place where there is a newb tutorial :P

Thanks in advance!

---

### Post by volkswagner on 2013-02-14
Samba 4 does not support browsing via NetBIOS names.  You will need to manually type the server address to access the shares.

I suggest using SAMBA 3 for a home network.  Unless you need Active Directory features, SAMBA 3 is the sane choice.

If you are really wanting SAMBA 4, the [wiki]("http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO") is the best place for help.

---

### Post by ranger12 on 2013-02-14
I have a simple home lan setup and I am using 12.04.2 server lts and Samba 3 with it setup as a PDC. I do not know how different the smb.conf in Samba 3 would be compared to Samba 4 but maybe if you can post your smb.conf file then you might get some more help.

Did you try here
[https://wiki.samba.org/index.php/Samba4/HOWTO](https://wiki.samba.org/index.php/Samba4/HOWTO)

---

### Post by cody1233 on 2013-02-14
Thanks guys!

Now have samba 3 running and it works like a charm!

---

