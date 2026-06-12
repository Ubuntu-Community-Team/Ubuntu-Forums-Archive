---
title: "ssh manager for gnome?"
date: 2008-08-16
forum: The Cafe
---

### Post by bp1509 on 2008-08-16
d

---

### Post by Technoviking on 2008-08-17
You can the sshmenu-gnome applet.

---

### Post by Bachstelze on 2008-08-17
[http://packages.ubuntu.com/hardy/putty](http://packages.ubuntu.com/hardy/putty)

D'oh!

---

### Post by bp1509 on 2008-08-17
d

---

### Post by ssam on 2008-08-17
i recommend making a ~/.ssh/config file. there is a simple example at [http://lookherefirst.wordpress.com/2007/12/17/a-simple-ssh-config-file/](http://lookherefirst.wordpress.com/2007/12/17/a-simple-ssh-config-file/) and some info at [http://kimmo.suominen.com/docs/ssh/#config](http://kimmo.suominen.com/docs/ssh/#config) or in the ssh manpage.

I use one to get to 2 severs behind NAT. the router is set to forward port 23 to one of them, and 25 to the other
```

Host server1
Hostname 1.2.3.4
Port 23
HostKeyAlias server1

Host server2
Hostname 1.2.3.4
Port 24
HostKeyAlias server2

Host *
Compression yes
ForwardX11 yes
EscapeChar ~

```


sshmenu-gnome should use the info

---

### Post by bp1509 on 2008-08-17
d

---

### Post by JT9161 on 2008-08-17
Putty is available on Linux as well as in the repos

---

### Post by LookTJ on 2008-08-17
> **bp1509 said:**
> One last question, how would i go about creating a dynamic socks proxy to route all traffic pointed to a particular point on the localhost through my ssh connection via the config file.

typically this is rather easy but i can't find anything that would let me know how to do this on the config file.
ssh -D alias/user@host(whatever you use)? Does this work?

---

### Post by bp1509 on 2008-08-17
d

---

