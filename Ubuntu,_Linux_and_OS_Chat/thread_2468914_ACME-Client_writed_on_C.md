---
title: "ACME-Client writed on C"
date: 2021-11-14
forum: Ubuntu, Linux and OS Chat
---

### Post by baytuch on 2021-11-14
I and my girlfriend are working on debianizing acme-client application

[https://github.com/baytuch/acme-client](https://github.com/baytuch/acme-client)

/etc/acme-client.conf:
```

authority letsencrypt {
  api url "https://acme-v02.api.letsencrypt.org/directory"
  account key "/etc/acme/letsencrypt-privkey.pem"
}

authority letsencrypt-staging {
  api url "https://acme-staging-v02.api.letsencrypt.org/directory"
  account key "/etc/acme/letsencrypt-staging-privkey.pem"
}

domain example.com {
  alternative names { example.com [www.example.com]("http://www.example.com") }
  domain key "/etc/ssl/example/private/privkey.pem"
  domain certificate "/etc/ssl/example/cert.pem"
  domain full chain certificate "/etc/ssl/example/chain.pem"
  sign with letsencrypt
  challengedir "/var/www/acme"
}

```


/etc/apache2/conf-available/acme.conf:
```

Alias /.well-known/acme-challenge /var/www/acme/

<Directory "/var/www/acme/">
    Options -Indexes
</Directory>

```

Enable conf for acme client:
```

sudo a2enconf acme

```


reissue script example
certs_reissue.sh :
```

#!/bin/sh

rm -f /etc/ssl/example/chain.pem
rm -f /etc/ssl/example/cert.pem

acme-client -Fv example.com || exit 1

rm -f /etc/apache2/SSL/example/private/privkey.pem
rm -f /etc/apache2/SSL/example/cert.pem
rm -f /etc/apache2/SSL/example/chain.pem
cp /etc/ssl/example/private/privkey.pem /etc/apache2/SSL/example/[COLOR=#000000][FONT=&amp]private/[/FONT][/COLOR]privkey.pem
cp /etc/ssl/example/cert.pem /etc/apache2/SSL/example/cert.pem
cp /etc/ssl/example/chain.pem /etc/apache2/SSL/example/chain.pem

systemctl stop apache2
systemctl start apache2

```

crontab:
```

5       2       1       *       *       /usr/lib/vps/certs_reissue.sh >/dev/null 2>&1

```

Create pkg:
```

sudo apt-get install build-essential
sudo apt-get install fakeroot dh-make
sudo apt-get install bison
sudo apt-get install autoconf
sudo apt-get install libssl-dev
sudo apt-get install libbsd0 libbsd-dev
git clone [https://github.com/baytuch/acme-client.git](https://github.com/baytuch/acme-client.git)
cd acme-client/
dpkg-buildpackage -rfakeroot -b --no-sign

```


[https://github.com/baytuch/acme-client/releases/download/0.2.3/acme-client_0.2.3_18.04_amd64.deb](https://github.com/baytuch/acme-client/releases/download/0.2.3/acme-client_0.2.3_18.04_amd64.deb)
[https://github.com/baytuch/acme-client/releases/download/0.2.3/acme-client_0.2.3_20.04_amd64.deb](https://github.com/baytuch/acme-client/releases/download/0.2.3/acme-client_0.2.3_20.04_amd64.deb)

---

### Post by TheFu on 2021-11-15
openbsd isn't Ubuntu.  Was that added to the title incorrectly or should this be moved to a different sub-forum?

---

### Post by QIII on 2021-11-15
Regardless of the OS, this reads like an answer to a question not asked.  What is your purpose?

---

### Post by baytuch on 2021-11-15
[COLOR=#000000]title fixed[/COLOR]

---

### Post by QIII on 2021-11-15
And what is the purpose of your thread?

---

### Post by TheFu on 2021-11-15
So ... is this a port of some BSD program to linux?  I've barely touched BSD the last 20 yrs.

We are in the "Chat" sub-forum, so I'm chatting.

Installation using .deb files is about 5th on the 'best' ways to install software on Ubuntu systems.  A PPA would really make a huge difference ( #2 on the priority list).  Some .deb files will add their PPA and keys to the system as part of the install process so updates are automatic. Most don't seem to do that, however.

Any plans to support flatpak, appimage or snap packages?  For something like getting new LE certificates and renewals, a snap might be nice for some people - especially those using Ubuntu Core (the IoT OS [https://discourse.ubuntu.com/t/using-core/19805](https://discourse.ubuntu.com/t/using-core/19805) ), which is basically a snap-only platform. [https://discourse.ubuntu.com/t/snaps-in-ubuntu-core/19730](https://discourse.ubuntu.com/t/snaps-in-ubuntu-core/19730)

I've been using acme.sh to keep this stuff simple.  Failed to get the other, popular, tool to work for my renewal needs.  I have to drop most of our firewall rules on port 80/443 so LE will renew.  Also, I'd rather NOT even have port 80 open to the internet all all - ever, but LE seems to use that for renewals. I've never understood why.

---

### Post by baytuch on 2021-11-16
Project added to PPA:

sudo add-apt-repository ppa:baytuch/acme-client
sudo apt-get update

sudo apt-get install acme-client

---

