---
title: "Access server from different vlan"
date: 2009-08-06
forum: Server Platforms
---

### Post by Sam Lars on 2009-08-06
I have a server plugged into a router on vlan 50. I can access the server from other machines on vlan 50, but I can't access the server from machines on other vlans (IP, hostname, won't even ping). Is this something that I need to change on the server or on the network switches?

---

### Post by HermanAB on 2009-08-06
It depends on whether the VLANs are managed by the router or by your server.

If the router is configured to strip the VLAN tags then you would need a second ethernet adaptor plugged into another router port.  If the switch doesn't strip VLAN tags, then you need to configure the VLANs on the server ethernet port.

---

### Post by Sam Lars on 2009-08-06
Thanks for your reply.

How would I know if the router is stripping the VLAN tags?

If it's stripping the tags, would I be basically giving the server an IP and an ethernet connection for every VLAN?
And if it's not stripping them, would I configure the VLANs like in this guide?
[http://ubuntuforums.org/showthread.php?t=703387](http://ubuntuforums.org/showthread.php?t=703387)

---

### Post by jamesrfla on 2009-08-06
If you want your server on VLAN 50 to be access in other VLAN's you need to setup ACL's.

---

### Post by Sam Lars on 2009-08-06
I'm not familiar with that...
I joined the domain using likewise-open, if that's relevant. I'm seeing stuff for ACL and Samba... is that what I need to set up?

---

### Post by jamesrfla on 2009-08-06
You need to setup Access Control Lists (ACL's) on the router so you can access your server from other VLAN's other than the VLAN the server is in.

---

### Post by Sam Lars on 2009-08-06
This is the only Linux server on the network... I checked, and I was able to access a Windows server between VLANs.

---

### Post by HermanAB on 2009-08-06
Hmm, if you are not aware of configuring VLANs on the server, then the switch is stripping the tags.  If you were configuring VLANs on the server yourself, then you would not be asking these questions, since then you'll know everything already.
:)

---

### Post by Sam Lars on 2009-08-10
Thanks for the help, it turns out that I needed to set the correct gateway in the interfaces file...

---

