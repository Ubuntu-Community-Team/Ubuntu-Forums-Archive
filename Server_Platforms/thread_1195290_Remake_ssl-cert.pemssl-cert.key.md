---
title: "Remake ssl-cert.pem/ssl-cert.key"
date: 2009-06-23
forum: Server Platforms
---

### Post by curvedinfinity on 2009-06-23
Hey,
My Ubuntu server just changed domains, and I need to remake the self-signed certificate that ssl-cert automatically generated for my dovecot-postfix install. If I purge all of dovecot/postfix's packages and delete the cert files, it will successfully regenerate the cert, but with the old domain. I've changed hostname and /etc/hosts. Where is it drawing the old domain from?

Thanks!

---

### Post by curvedinfinity on 2009-06-23
According to this website:
[http://packages.debian.org/changelogs/pool/main/s/ssl-cert/ssl-cert_1.0.23/changelog](http://packages.debian.org/changelogs/pool/main/s/ssl-cert/ssl-cert_1.0.23/changelog)

ssl-cert uses hostname -f for the "snakeoil" cert. When I run that command, it returns the new domain.

---

### Post by curvedinfinity on 2009-06-23
Sorry for the post, I just resolved it -- I wasn't purging ssl-cert. Just to document how to perform a domain name change for dovecot-postfix:

Without the TLD (no .com):
```

sudo hostname newdomain

```

Make sure the new domain is the first host listed for your IP:
```

sudo pico /etc/hosts

```

Reinstall everything:
```

sudo rm /etc/ssl/certs/ssl-mail.pem
sudo rm /etc/ssl/private/ssl-mail.key
sudo apt-get purge dovecot-common dovecot-imapd dovecot-pop3d dovecot-postfix postfix ssl-cert
sudo apt-get install dovecot-postfix

```

---

