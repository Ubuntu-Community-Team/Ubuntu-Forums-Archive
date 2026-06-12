---
title: "http to https redirect"
date: 2014-10-26
forum: Server Platforms
---

### Post by rcdunnii on 2014-10-26
Ive got ubuntu saucy 13.10 with apache 2.4.6 running on aws. I've enabled ssl and want to redirect http->https. Best way?
Thanks in advance

---

### Post by nerdtron on 2014-10-26
You may get replies, but 13.10 is already End-of-Life and is no longer supported. Please install a new server version, preferably the Long-Term-Support Ubuntu Server 14.04

---

### Post by rcdunnii on 2014-10-27
Thanks @nerdtron. I've upgraded to 14.04..1 LTS, set up iptables to accept 22, 80, 433, added fail2ban filter because of endless ssh attempts. How does one force https connection, with apache2 or by .htaccess, or other means? Appreciate any help...

---

### Post by nerdtron on 2014-10-27
Setup a redirection vhost
```

<VirtualHost *:80>
ServerName  www.example.com
Redirect / https://secure.example.com/
</VirtualHost>

```

Be sure that you have another entry for the secure vhost in port 443.

---

### Post by nerdtron on 2014-10-27
If you are starting from scratch, you can try this: [https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)

---

### Post by bapoumba on 2014-10-27
*Thread moved to **Server Platforms**.*

---

### Post by rcdunnii on 2014-10-27
Perfect, thanks so much!

---

