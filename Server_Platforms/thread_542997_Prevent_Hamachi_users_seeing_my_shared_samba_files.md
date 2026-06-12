---
title: "Prevent Hamachi users seeing my shared samba files?"
date: 2007-09-04
forum: Server Platforms
---

### Post by Johnsie on 2007-09-04
Hi, I want to use Hamachi to join a network. I want to protect my samaba shares from strangers:

My local network->read/write access

Hamachi users->No access


Is this possible and how would I do it?  Is there an option in Hamachi for Linux to prevent file sharing? 

I know I could probably do it using smb.conf or file permissions, but is there a way I could just switch off file sharing  in hamachi?

---

### Post by Brazen on 2007-09-04
IIRC, hamachi is just a vpn software.  It should create a virtual adapter on your machine, so just use your firewall to block ports on that adapter.

---

### Post by Johnsie on 2007-09-04
Can I block ports from all ip ranges except 192.168.x.x? or have a whitelist of friendly ips? I still want my local machines to be able to access it.

How would I go about setting up a firewall to do that?

---

### Post by Brazen on 2007-09-04
> **Johnsie said:**
> Can I block ports from all ip ranges except 192.168.x.x? or have a whitelist of friendly ips? I still want my local machines to be able to access it.

How would I go about setting up a firewall to do that?

You absolutely can do that.  Just create a rule to block everything and then create rules for what ips you want to allow.  You can do an allow everything rule to a single ip or range of ips or even by subnet.

You would probably want to use firestarter to do this.

---

### Post by Johnsie on 2007-09-04
cheer,s I'll give thata shot :-)

---

