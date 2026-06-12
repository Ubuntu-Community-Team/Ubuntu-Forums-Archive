---
title: "Active Directory Integration, DNS issue"
date: 2016-10-19
forum: Server Platforms
---

### Post by braven36 on 2016-10-19
My servers are multihoned. They have two network interfaces.  I only want to register Interface One in Windows DNS and not register interface two.  I have created a static entry on Windows DNS server using Interface One's IP.  But since the servers are part of Active Directory, they can up date their DNS record and the servers are randomly updating DNS with Interface TWO's IP. I would like to know if I can prevent the servers from updating DNS with Interface TWO's IP.

---

### Post by SeijiSensei on 2016-10-19
If you are using DHCP to configure interface TWO, I suspect the answer is no.  But if you use a static IP on that address, then Active Directory may not create a DNS entry for that interface.  Give it a try.

If that doesn't work, you may be able to configure the Active Directory server to ignore the interface.  I think trying to solve the problem from the Windows side will be more successful than making changes to Linux.

---

### Post by braven36 on 2016-10-20
We ran a network trace on our Domain Controller. We set the IP of interface ONE in DNS. We then rebooted the server.  After the server was complete powered on. We refresh our DNS view and the IP had to changed interface TWO. In the network capture we can see where the server deleted it DNS entry and then updated it's DNS entry.   Could this be something to do with SSSD and Active Directory?

---

### Post by SeijiSensei on 2016-10-20
My only encounters with Active Directory come through discussions with clients. I think it is a bit strange that the address would switch though.  Even if you're using DHCP, the IP address should be tied to the MAC address of the interface.  Can't you just use static addressing on the multi-homed box and make corresponding entries in Active Directory?

---

### Post by braven36 on 2016-10-20
I think we figured it out. We needed to add this dyndns_update=false to /etc/sssd/sssd.conf file

---

### Post by Vegan on 2016-10-22
I have used SAMBA for integration into NT Active Directory, look into that package, might be of some use

---

