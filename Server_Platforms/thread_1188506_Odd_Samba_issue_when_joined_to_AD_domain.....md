---
title: "Odd Samba issue when joined to AD domain...."
date: 2009-06-15
forum: Server Platforms
---

### Post by medium_grade on 2009-06-15
So, I joined a Linux box to my AD domain and it appears to work beautifully except for one small thing. If I reference the server by it's netbios name, I get a message:

\\SERVER is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. Access is denied.

However, if I reference the same server by its IP address (\\192.168.1.26) or by its full domain name (\\SERVER.MYDOMAIN.COM) I can access it just fine. The file shares all seem to work correctly. What might cause this strange issue?

---

### Post by ghen on 2009-06-16
As a workaround you can try using a CNAME alias in DNS


SERVER CNAME SERVER.MYDOMAIN.COM

or if it doesn't like that due to name similarities just rename the server. (never tried shortening a FQDN in DNS before, so who knows)

SERVER2 CNAME SERVER.MYDOMAIN.COM

---

### Post by ZackM on 2009-06-16
Another route you can go is using likewise-open. I use that to join to AD here. 

[https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html) 

Unless, of course, you were content with using Samba instead of something else.

---

### Post by HermanAB on 2009-06-16
Likewise is based on Samba winbind, so it doesn't really matter whether you DIY with Samba or run the Likewise wizard.

---

### Post by medium_grade on 2009-06-16
Never mind. It seems to be working now. Go figure.

---

### Post by ghen on 2009-06-17
Sounds like it was a DNS replication issue.

---

