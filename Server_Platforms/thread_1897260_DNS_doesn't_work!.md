---
title: "DNS doesn't work!"
date: 2011-12-18
forum: Server Platforms
---

### Post by Linux99 on 2011-12-18
hi..
i configure dns server to listen on server ip 192.168.1.1 only
but 
when i use nslookup command the result is loopback address with server ip address!!
what's wrong? and how to remove or disable loopback address?.

```
root@myserver:/etc/bind# nslookup mydomain.local
server: 127.0.0.1
address: 127.0.0.1#53

name: mydomain.local
address: 192.168.1.1
```

---

### Post by elico on 2011-12-19
check your /etc/resolve.conf file.

---

### Post by Linux99 on 2011-12-19
> **elico said:**
> check your /etc/resolve.conf file.
thanks elico..

i add dns address but it's overwritten! i try many times no benefit it's still empty.
also, i remove network-manager and replace it with WICD and remove looopback from interfaces file!

---

### Post by jonobr on 2011-12-19
Do you have the desktop installed?
If so and NM applet is running it will overwrite your configuration setting for /etc/resolv.conf

---

### Post by Linux99 on 2011-12-19
> **jonobr said:**
> Do you have the desktop installed?
If so and NM applet is running it will overwrite your configuration setting for /etc/resolv.conf

hi jonobr.

yes!
how can I resolve this problem? as i said i remove network manager and replace it with WICD but no thing changed!.

---

### Post by jonobr on 2011-12-19
Hey there


So using the likes of Wicd or network manager and modifying the configuration files is like having a dog and barking yourself.

Its going to overwrite any dns settings you have in there,
If there is nothing set in them they will still overwrite with nothing.

They consider that they are in wontrol of the networking settings and dont expect you to modify anything by hand.

Why not use the dns settings in the program your using?

Cheers

PS- My own preference is not to use any of these programs and modify config files myself, I find them undependable.
Thats historical for me and may not be the case today (once bitten twice shy:-) )

---

### Post by Linux99 on 2011-12-19
> **jonobr said:**
> Hey there


So using the likes of Wicd or network manager and modifying the configuration files is like having a dog and barking yourself.

Its going to overwrite any dns settings you have in there,
If there is nothing set in them they will still overwrite with nothing.

They consider that they are in wontrol of the networking settings and dont expect you to modify anything by hand.

Why not use the dns settings in the program your using?

Cheers

PS- My own preference is not to use any of these programs and modify config files myself, I find them undependable.
Thats historical for me and may not be the case today (once bitten twice shy:-) )

lol:D.. yes i fell because i'm beginner in Linux!
well,i use dns setting in WICD and Network manager before remove it and also configure bind files.
thanks for lovely replay.

---

### Post by jonobr on 2011-12-19
No Problem,

we are all learning ......
Cheers

jonobr

---

