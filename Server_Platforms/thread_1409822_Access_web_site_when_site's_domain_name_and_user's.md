---
title: "Access web site when site's domain name and user's local server's domain name r same"
date: 2010-02-18
forum: Server Platforms
---

### Post by alikthename on 2010-02-18
Hello!
In the office there is a local network with samba+openldap PDC. The local domain name is company.net. The company desided to create a corporate Website on a remote hosting and desided that the site's domain should be company.net which is same as local network's domain name. So now it is not possible to reach that corporate website from within the company's local network because, as I guess, bind9 which is installed on above menioned PDC looks for company.net on a local webserver. Is there a possibility to let people from this local network browse the remote site?

Thanks in advance.

---

### Post by HermanAB on 2010-02-18
Howdy,

Do some googling for 'split horizon dns'.

---

