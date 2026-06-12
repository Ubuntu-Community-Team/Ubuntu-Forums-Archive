---
title: "Disable 80 &amp; Run 443 only"
date: 2019-03-05
forum: Server Platforms
---

### Post by linus_leung on 2019-03-05
I have installed Apache2 in Ubuntu 16.04. Can I disable port 80 and only run 443 in the web server?

---

### Post by mastablasta on 2019-03-05
you can use UFW for that:
[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04)
[https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)

---

### Post by linus_leung on 2019-03-05
> **mastablasta said:**
> you can use UFW for that:
[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04)
[https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)

Thank you so much for your reply! Technically, I can block port 80 or forward port 80 to 443 by firewall. But I wonder if port 80 must run or not.

---

### Post by mastablasta on 2019-03-06
no, i think you can actually route apache through a different port. for example: [https://www.ostechnix.com/how-to-change-apache-ftp-and-ssh-default-port-to-a-custom-port-part-1/](https://www.ostechnix.com/how-to-change-apache-ftp-and-ssh-default-port-to-a-custom-port-part-1/)

---

### Post by SeijiSensei on 2019-03-06
If all you want is to force all connections through port 443, there's another way that is more transparent to the enduser.

In /etc/apache2/sites-enabled/000-default.html, add this line above "</VirtualHost>" at the bottom of the file:

```

Redirect permanent / https://your.server.name/

```

Now any HTTP requests for your site will be automatically redirected to the HTTPS port.

---

