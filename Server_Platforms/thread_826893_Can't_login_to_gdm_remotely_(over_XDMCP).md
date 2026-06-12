---
title: "Can't login to gdm remotely (over XDMCP)"
date: 2008-06-12
forum: Server Platforms
---

### Post by diska on 2008-06-12
Hey there,

my problem in short: 
Logging in on GDM on the physical console of the machine works fine. Over XDMCP it doesn't. Who has an idea what's causing this?

Longer version:
I'm trying to get an Ubuntu Hardy terminal server running using XDMCP with GDM, but can't get it to work.

I configured GDM to allow XDMCP using gdmsetup. I switched remote logins to look the same as the local display (this enabling XDMCP). I also removed the checkmark to allow TCP.

When I try to connect to GDM using Xnest on another machine, I get to see the GDM loginscreen I configured, thus confirming that XDMCP itself appears to work.

However, I can't login using any account, no matter if it's a local account or an LDAP account (we have LDAP auth setup using libnss-ldap).
When logging in on the physical console everything works properly, both local and ldap accounts.

Regards,

Diska

---

### Post by airowolf on 2008-06-16
I have the same problem too. thx

---

### Post by airowolf on 2008-06-16
i was able to login by going to another ubuntu computer directly connected over ethernet and on the login screen in options and connect xdmpc it worked for me. not sure if that helps.

---

### Post by Rui Pais on 2008-06-19
Same here. Both Ubuntu and Xubuntu.
On Hardy XDMCP don't seems to work :(

---

### Post by Rui Pais on 2008-06-28
Uff, after a lot of trial and experiments i discovered that the only way i can make XDMCP works, it's by put DNS IPs on /etc/resolv.conf file!

Don't know why... or what DNS servers had to do with with a protocol used on a intranet (in most cases even without an Internet connection...)

Anyone interested to try need either to set static IPs or add to /etc/dhcp3/dhclient.conf a line:

```
prepend domain-name-servers ***dns.primary.server.ip***, ***dns.secondary.server.ip***
```
To workaround resolv.conf overwritten by dhcp server.

The DNS IPs can be the OpenDNS ones (208.67.222.222, 208.67.220.220) or the ones your internet providers use (check DNS section of your router)

hope that helps.

---

### Post by Scunge on 2008-08-22
I'm afraid that didn't work for me, assuming I did the right thing.

==========

[i]Moved the bulk of this post to what is, I feel, the more relevant [[color=blue]Desktop Environments[/color]](http://ubuntuforums.org/forumdisplay.php?f=329) forum...
[**[color=blue]http://ubuntuforums.org/showthread.php?t=910058[/color]**](http://ubuntuforums.org/showthread.php?t=910058)
...but the following bit may still be relevant here:[/i]

==========

Finally, I added the following line to the end of /etc/dhcp3/dhclient.conf:

```
prepend domain-name-servers 208.67.222.222 208.67.220.220
```

as advised above and restarted the remote machine. Again, no change.

Have I missed anything from what is suggested here? Is there anything else to try or options that I have omitted to set?

Thanks.

---

### Post by Scunge on 2008-09-04
[i]Moved post to what is, I feel, the more relevant [[color=blue]Desktop Environments[/color]](http://ubuntuforums.org/forumdisplay.php?f=329) forum...
[**[color=blue]http://ubuntuforums.org/showthread.php?t=910058[/color]**](http://ubuntuforums.org/showthread.php?t=910058)[/i]

---

