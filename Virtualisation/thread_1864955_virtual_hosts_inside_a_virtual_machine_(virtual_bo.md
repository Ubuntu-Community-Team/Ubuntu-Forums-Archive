---
title: "virtual hosts inside a virtual machine (virtual box)"
date: 2011-10-19
forum: Virtualisation
---

### Post by bks07 on 2011-10-19
I'm using virtual box for my web server. I always accessed it via IP-address but now I'm trying to setup some virtual hosts and I do not know how to access them from the host system.
Ehm... and maybe if this is from importance I'm using a bridget network adapter and iInside my virtual box I can ping my virtual hosts.

Thanks for your help,
bks07

---

### Post by collisionystm on 2011-10-19
> **bks07 said:**
> I'm using virtual box for my web server. I always accessed it via IP-address but now I'm trying to setup some virtual hosts and I do not know how to access them from the host system.
Ehm... and maybe if this is from importance I'm using a bridget network adapter and iInside my virtual box I can ping my virtual hosts.

Thanks for your help,
bks07

Your trying to run virtual inside of a virtual?

---

### Post by CharlesA on 2011-10-19
You'd have to set up [name-based virtual]("http://httpd.apache.org/docs/1.3/vhosts/name-based.html") hosts and point that name to the ip address via /etc/hosts or a local dns server.

---

### Post by bks07 on 2011-10-19
> **collisionystm said:**
> Your trying to run virtual inside of a virtual?

No, I'm just using an apache web server on my guest system.
Host is Ubuntu 11.10, guest is Ubuntu 10.04 LTS.

---

### Post by bks07 on 2011-10-19
> **CharlesA said:**
> You'd have to set up [name-based virtual]("http://httpd.apache.org/docs/1.3/vhosts/name-based.html") hosts and point that name to the ip address via /etc/hosts or a local dns server.

Yeah, I think what I need is a local DNS. I will try this [http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/](http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/)

Thank you. :)

---

### Post by CharlesA on 2011-10-19
> **bks07 said:**
> Yeah, I think what I need is a local DNS. I will try this [http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/](http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/)

Thank you. :)
IMHO, you don't need a full blown BIND server. I use dnsmasq myself.

---

