---
title: "Problem With Samba Share on uBuntu 10.10 Server"
date: 2010-11-06
forum: Server Platforms
---

### Post by NightFlyer_ on 2010-11-06
Hello Everyone.

I have successfully installed Samba on my Ubuntu 10.10 server edition.

But I am having some problems with accessing the created share via Windows.

My smb.conf is:

[global]
workgroup = lan
os level = 65
wins support = no

[share1]
comment = Test Share1
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755

I can see the ubuntu computer (hostname is ubuntu) under windows network, but when I click on it to go the shares, I get a prompt requesting username and password.

Is it possible to access the shares on the ubuntu server without inputting user/pass ?

Any help or ideas would be very much appreciated.

Wish you a continuous pleasant weekend,

Martin.

---

### Post by littlegreiger on 2010-11-06
If I want the share to be open to everyone I usually use ```
 guest only = yes 
``` instead of ```
guest ok = yes
``` This forces everyone to access the share as a guest, which means you shouldn't have to enter a password.

---

