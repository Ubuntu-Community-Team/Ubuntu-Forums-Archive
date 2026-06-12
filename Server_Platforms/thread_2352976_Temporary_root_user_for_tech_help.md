---
title: "Temporary root user for tech help"
date: 2017-02-17
forum: Server Platforms
---

### Post by Heeter on 2017-02-17
Hi all,

I am having issues with my ubuntu16.04 LAMP with iredmail server. It was working fine until letsencrypt cert manual renewal caused my websites to stop pulling up on the browser, am pretty sure it is an apache issue.

Anyways, I have been working at this for three days and I think that it is time that I ask for a tech's assistance.

I would like to know how to create a temporary user & root user/password for the tech to use through ssh, then when they are done, I can easily delete them.

Regards

---

### Post by darkod on 2017-02-17
Create standard user and add him to the sudo group. That will give it sudo rights. After that simply delete it or dosable its password.

Of course to create the new user and change his group membership you will need to use your current admin user:
```
sudo adduser <newusername>
sudo usermod -aG sudo <newusername>
```

---

### Post by Heeter on 2017-02-17
Great thank you

Now to find someone that I can trust and won't charge me and arm and a leg.

Regards

---

### Post by Habitual on 2017-02-18
I saw another thread here about with iRedMail and similar complaints? 
Is that yours?

If it is, perhaps you won't need a sysadmin? (suggesting new host with fresh ired install here)
from [http://www.iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://www.iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)
```
iRedMail is designed to be deployed on a **FRESH** server system, which means your server does **NOT** have mail related components installed, 
e.g. MySQL, OpenLDAP, Postfix, Dovecot, Amavisd, etc. iRedMail will install and configure them for you automatically. Otherwise it may override your 
existing files/configurations althought it will backup files before modifying, and it may not be working as expected.
```
It'd be a shame to have to pay someone (**and** *trust*, sheesh, scary) just to read the instructions and charge you for doing it?

Good Luck.
and darko's tip is a Keeper.

---

