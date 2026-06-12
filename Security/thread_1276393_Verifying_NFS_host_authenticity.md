---
title: "Verifying NFS host authenticity"
date: 2009-09-27
forum: Security
---

### Post by m3pz on 2009-09-27
I have a network in which I can trust some of the hosts, but not others, and I have a filer that provides some mounts to the trusted hosts and some other mounts to the untrusted hosts.

How can I ensure that only the trusted hosts get access to some of the mounts? NFS's IP address restrictions isn't enough, since it's trivial to change the IP address on the untrusted hosts. Is there a way to verify the authenticity of hosts connecting to the NFS server, using some kind of certificate approach?

Thanks!

---

### Post by movieman on 2009-09-27
You can configure the machines to require an authenticated IPSEC connection; though setting that up is a bit of a pain.

---

### Post by bodhi.zazen on 2009-09-27
> **m3pz said:**
> I have a network in which I can trust some of the hosts, but not others, and I have a filer that provides some mounts to the trusted hosts and some other mounts to the untrusted hosts.

How can I ensure that only the trusted hosts get access to some of the mounts? NFS's IP address restrictions isn't enough, since it's trivial to change the IP address on the untrusted hosts. Is there a way to verify the authenticity of hosts connecting to the NFS server, using some kind of certificate approach?

Thanks!

Not exactly the solution you are looking for, but this is the reason I switched to Samba. Samba is, IMO, more secure then NFS and shares can be configured so as to require a password.

If you *must* use nfs, take a look at things such as Kerberos

[http://nfsworld.blogspot.com/2006/02/real-authentication-in-nfs.html](http://nfsworld.blogspot.com/2006/02/real-authentication-in-nfs.html)

[http://hell.org.ua/Docs/oreilly/tcpip2/fire/ch17_03.htm](http://hell.org.ua/Docs/oreilly/tcpip2/fire/ch17_03.htm)

[https://help.ubuntu.com/community/Samba/Kerberos](https://help.ubuntu.com/community/Samba/Kerberos)

[http://www.alittletooquiet.net/text/kerberos-on-ubuntu/](http://www.alittletooquiet.net/text/kerberos-on-ubuntu/)

---

### Post by scorp123 on 2009-09-27
> **bodhi.zazen said:**
>  Kerberos  That and sticking to NFSv4 ... But seriously: It's pain to setup. Only recommended if you really know what you do.

---

