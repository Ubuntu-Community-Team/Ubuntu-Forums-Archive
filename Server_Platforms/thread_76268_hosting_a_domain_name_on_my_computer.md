---
title: "hosting a domain name on my computer"
date: 2005-10-14
forum: Server Platforms
---

### Post by stuffradio on 2005-10-14
Hi, I've seen several posts on people hosting there own domains. I have apache2 setup. I have two problems including not knowing how to configure DNS. When I try and go to a php based website that isn't phpmyadmin, it makes me download. To see what I mean go to [http://stuffhosting.dyndns.org](http://stuffhosting.dyndns.org)
So any help is appreciated.

---

### Post by adwait on 2005-10-14
Configuring DNS isn't much of a big deal......just point your domain to your IP address in the control panel of your domain, which will be provided by the people through whom you registered your domain.
If the php pages on your site are offered for download instead of show in the browser, you probably don't have php installed/installed correctly.

---

### Post by pingswept on 2005-10-15
[QUOTE=adwait]If the php pages on your site are offered for download instead of show in the browser, you probably don't have php installed/installed correctly.[/QUOTE]

Check /etc/mime.types?

---

### Post by Jad on 2005-10-15
Try this it's really cool if you don't have static IP address.
[http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip)

---

