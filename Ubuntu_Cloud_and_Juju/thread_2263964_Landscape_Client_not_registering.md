---
title: "Landscape Client not registering"
date: 2015-02-04
forum: Ubuntu Cloud and Juju
---

### Post by Leo_Dano on 2015-02-04
Hello all,

I spun up two Ubuntu VM's.  I can register the client on one but not the  other.  I followed the set up instructions the same on both, but can't  get the client to register on the Landscape server.

Message says:

Please wait... We were unable to contact the server. Your internet  connection may be down. The landscape client will continue to try and  contact the server periodically.

Any suggestions I can try?

Thanks,
Leo

---

### Post by Leo_Dano on 2015-02-05
Wow, 100 views and not 1 reply.

---

### Post by lawton1985 on 2015-03-02
I agree, we need more feedback as to why this isn't work for us.

Please help!

---

### Post by wikityler on 2015-03-31
Have either of you been able to resolve this? Having the same issue here too.

---

### Post by wikityler on 2015-03-31
This solved my problem:
Registering clients with a self signed certificate:

The quickstart package installs a self-signed certificate that is generated on-the-fly.

    Grab this file from the server: /etc/ssl/certs/landscape_server_ca.crt
    Copy it somewhere on the client, for example, /etc/landscape/landscape_server_ca.crt
    Change /etc/landscape/client.conf to include this line, pointing at the file you just copied: ssl_public_key = /etc/landscape/landscape_server_ca.crt

Then try to register again. (Thanks to panlinux for figuring this out)

From: [http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use](http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use)

---

### Post by Leo_Dano on 2015-04-14
> **wikityler said:**
> This solved my problem:
Registering clients with a self signed certificate:

The quickstart package installs a self-signed certificate that is generated on-the-fly.

    Grab this file from the server: /etc/ssl/certs/landscape_server_ca.crt
    Copy it somewhere on the client, for example, /etc/landscape/landscape_server_ca.crt
    Change /etc/landscape/client.conf to include this line, pointing at the file you just copied: ssl_public_key = /etc/landscape/landscape_server_ca.crt

Then try to register again. (Thanks to panlinux for figuring this out)

From: [http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use](http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use)

Sorry for not following up on this post, but yes that worked great.  Thanks!

Leo

---

