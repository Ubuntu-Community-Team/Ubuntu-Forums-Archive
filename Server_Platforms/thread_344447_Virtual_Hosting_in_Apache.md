---
title: "Virtual Hosting in Apache"
date: 2007-01-22
forum: Server Platforms
---

### Post by hammonjj on 2007-01-22
I'm trying to set up a couple of websites on my new server using virtual hosting, but I am having no luck.  After viewing multiple websites on how to enable virtual hosting I have modified my httpd.conf file to look like this:

NameVirtual Host *

<VirtualHost *>
ServerName [www.jones-hammondwedding.com](www.jones-hammondwedding.com)
DocumentRoot /var/www/jones-hammondwedding.com/htdocs
</VirtualHost>

<VirtualHost *>
ServerName hammonjj.mine.nu
DocumentRoot /var/www/hammonjj.mine.nu/htdocs
</VirtualHost>

Everytime I try to load the server I get the message:

Could not determine server's fully qualified domain name...

AND

[warn] NameVirtualHost *:0 has no virtualhosts

Can anyone tell me where I am going wrong?  I've tried multiple methods of working virtual hosting, but none seem to be working.  I'm sure I'm missing something dumb too.

Also, is there a way to avoid using port 80 for http, yet set it up in such a way that visitors to my website won't notice?

Thanks
James

BTW I'm using Ubuntu 6.10 Desktop

---

### Post by Wim Sturkenboom on 2007-01-23
Try to add a line like this to /etc/hosts
```

172.18.32.111           www.jones-hammondwedding.com
172.18.32.111           hammonjj.mine.nu
```

If you have a nameserver running (dns), add something that achieves the same to it's config.
Replace the IP address by the address of your box.

---

### Post by hammonjj on 2007-01-23
I'm still getting the exact same error message.

James

---

### Post by chrisfay on 2007-01-23
Apache 1 or 2? If 2, why are you editing httpd.conf instead of apache2.conf?

Also if 2, you should place your virtual sites in sites-available and use a2ensite to symlink them into sites-enabled.

> [warn] NameVirtualHost *:0 has no virtualhosts

You're NameVirtualHost should look like:

```
NameVirtualHost *:
```
not
```
NameVirtualHost *
```

---

### Post by hammonjj on 2007-01-23
I changed what you said, but I still am getting the same error messages, plus I get Name or Service not known: Cannot resolve host name *: ---ignoring.

I moved the stuff in httpd.conf to two seperate config files, one for each site, and created symbolic links to sites-enabled.



In which file should:

NameVirtualHost *:

go?

apache2.conf or the configuration file of the website?

---

