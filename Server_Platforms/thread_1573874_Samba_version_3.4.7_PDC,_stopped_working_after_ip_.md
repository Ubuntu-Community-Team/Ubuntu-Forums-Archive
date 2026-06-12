---
title: "Samba version 3.4.7 PDC, stopped working after ip change"
date: 2010-09-13
forum: Server Platforms
---

### Post by LarsEriksson on 2010-09-13
I run Samba version 3.4.7 as a Domain server for our company, and recently we reorganized our IP-addresses. And the Samba server also got a new IP-address. (192.168.1.60 -> 192.168.1.22)

However, now new computers can not join the domain, and old ones can not connect to it correctly (they get a temp profile).

Windows XP gets a temp profile when connecting, and when trying to join a domain i get this error "A domain controller for the domain HAWAR3 could not be contacted.
    Ensure that the domain name is typed correctly.
    If the name is correct click Details for troubleshooting"

When trying to connect Windows2008R2(allready a member) it says "There are currently no logon servers available to service the logon request."


My guess is that is is some problem with WINS or something.

Can anyone help out here ?

---

### Post by junke1990 on 2010-09-13
did you edit the DNS value's as well? to set to the new  IP address?

---

### Post by LarsEriksson on 2010-09-13
Yes, and i can ping the hostname of the samba server perfectly
I can connect to \\192.168.1.22\share
and \\hostname.domain
But not \\hostname

---

