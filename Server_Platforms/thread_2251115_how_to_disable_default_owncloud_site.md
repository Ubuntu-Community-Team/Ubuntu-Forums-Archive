---
title: "how to disable default owncloud site"
date: 2014-11-02
forum: Server Platforms
---

### Post by blue-eagle2 on 2014-11-02
I just installed owncloud 7 and it works fine, but I want it on a virtual IP.  So, I created the virtual IP and a virtual host and while it is working, the default where it was originally also works and I would  like to disable that site somehow and I can't seem to figure out how.  By default I mean the [physical IP address of network card]/owncloud that was originally set up when owncloud was first installed.

No, I tried disabling the owncloud config with a2disconfig owncloud, but that just disabled both sites.

:confused:

---

### Post by Thirtysixway on 2014-11-02
Sounds like you need to modify the vhost settings

Can you run   cat /etc/apache2/conf-available/owncloud.conf  and paste the output here?

---

### Post by blue-eagle2 on 2014-11-02
> **Thirtysixway said:**
> Sounds like you need to modify the vhost settings

Can you run   cat /etc/apache2/conf-available/owncloud.conf  and paste the output here?

owncloud.conf:
```

Alias /owncloud /var/www/owncloud
<Directory /var/www/owncloud/>
  AllowOverride All
</Directory>

```

---

### Post by koenn on 2014-11-03
start by commenting out that alias, because it is what makes [http://rserver](http://rserver)**/owncloud** work.

If that's not enough you'll also need to do something about the default site.

---

### Post by blue-eagle2 on 2014-11-03
> **koenn said:**
> start by commenting out that alias, because it is what makes [http://rserver](http://rserver)**/owncloud** work.

If that's not enough you'll also need to do something about the default site.

Unfortunately, all that did was to make it so I could not get to either site.  The web pages displayed Not Found.

---

### Post by koenn on 2014-11-04
That means the the vhost config that you made is not correct.

---

### Post by volkswagner on 2014-11-04
Why do you want to break availability of [physical IP address of network card]/owncloud?

The implementation you are trying to accomplish would require one of the following fixes.

1. Setup Apache2 so all virtual hosts specify the listening ip address, (no sites can have <VirtualHost *:80>), You'll need to add listen directive for each virtual and real ip in apache's config (usually ports.conf)
2. Change the default root for apache, this will allow you to break browsing server by ip/folder
3. physically move your owncloud webroot above or even with Apache2's webroot
4. use namebased virtual hosting and setup dns or hostfiles on your router/dns server for vhosts to match servername directive to hosts/dns entries.

---

