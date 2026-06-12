---
title: "Samba PDC, bind9, SRV and XP"
date: 2006-08-28
forum: Server Platforms
---

### Post by gertmul on 2006-08-28
I have a Samba PDC (192.168.11.12) and a DNS server (bind9, 192.168.11.2) and a WindowsXP machine that does not want to join the domain: "A domain controller for the domain xyz could not be contacted", and under "details" it claims that the "DNS name does not exist" and "the query was for the SRV record for _ldap._tcp.dc._msdcs.xyz"

Does anyone know how to do this SRV record in bind9, since there are no examples on the web about this.

Thank you

Gert

---

### Post by elias@cpaefs.com on 2006-08-28
Make sure that bind point de domain (example.lan) to the Ubuntu server

---

### Post by gertmul on 2006-08-29
Can you be a little more specific on how to do this please?

---

### Post by gertmul on 2006-08-29
Can someone with an Ubuntu PDC maybe post what the bind zone file should look like? Maybe it was added automatically with DDNS?

Thank you

Gert

---

