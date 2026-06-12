---
title: "Bind9 as a secondary AD DNS"
date: 2008-05-05
forum: Server Platforms
---

### Post by Rever75 on 2008-05-05
OK,
  I am running Bind9 as my slave DNS server for my AD domain. I can successfully perform a zone transfer from my Windows 2003 Master server. However, when I try to log into the Domain from a computer who has the bind9 server as it primary DNS server it fails to find our Domain. I can do an nslookup on all the computers and in the zone file I have all our SRV records. Not sure what is going wrong here. This is on a Hardy Server with Bind9 from the repo.

---

### Post by Rever75 on 2008-05-14
Can anyone help me out here. I am not sure what is going on but some clients seem to authenticate OK while others do not. Any and all help on testing this or troubleshooting this would be great.

---

