---
title: "LDAP server configuration"
date: 2011-03-25
forum: Server Platforms
---

### Post by suresh_vandiyur on 2011-03-25
Hi All,

I need some clarification. if i setup LDAP server i need DNS server or no need DNS server. What are thing needed for setup LDAP server. Just go through the below link Please help me
[https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html)

Thank you,

Regards,
Suresh

---

### Post by headvampyre@hotmail.co.uk on 2011-03-25
Are you trying to configure with Kerberos? Youll need DNS if you are. If not - DNS would be useful, but its not essential, you can always access LDAP by the IP address.

Oh - what version of ubuntu are you using? Desktop/Server, 9.04, 9.10, 10.04, 10.10? They made changes and the package maintainers became lazy in 9.10, so after that youll need to do extra configuration.

---

