---
title: "E-mail errors, sometimes...!"
date: 2021-05-10
forum: Server Platforms
---

### Post by af-crm on 2021-05-10
We're a small company with some 15 employees. Our e-mail server didn't connect properly. When using the web-browser the user were redirected to a cloud service (as we also host).
Here's a list of running services. Where's a good place to start the research!?

```
$ service --status-all
 [ + ]  acpid
 [ + ]  apache2
 [ - ]  apparmor
 [ ? ]  apport
 [ + ]  atd
 [ ? ]  console-setup
 [ + ]  cron
 [ - ]  dbus
 [ ? ]  dns-clean
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ ? ]  kmod
 [ + ]  memcached
 [ ? ]  mysql
 [ ? ]  networking
 [ ? ]  ondemand
 [ - ]  postfix
 [ ? ]  pppd-dns
 [ - ]  procps
 [ ? ]  rc.local
 [ + ]  resolvconf
 [ ? ]  rng-tools
 [ - ]  rsync
 [ + ]  rsyslog
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ + ]  ssh
 [ - ]  sudo
 [ + ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ - ]  x11-common
```

---

### Post by volkswagner on 2021-05-10
You haven't provided much information.

I would start with postfix logs and run health checks at mxtoolbox.com.
Check firewall is configured correctly and make sure your provider
isn't blocking any ports.

---

### Post by TheFu on 2021-05-10
Check the system logs for errors and warnings.  You first need to determine if this is a server issue or a client issue.  What sort of monitoring and alarming is setup on the server?

---

### Post by perlporter on 2021-05-11
Could you explain your problem better ?
More information will make it easier to help :-)

---

### Post by LHammonds on 2021-05-11
> **af-crm said:**
> Our e-mail server didn't connect properly.
Not sure what you mean by "did not connect"

> **af-crm said:**
> When using the web-browser the user were redirected to a cloud service (as we also host).
Hmmm...by "did not connect" earlier, were you talking about using a web browser to access the web-client on the mail server?  Is this a server accessibility issue or an issue with a service such as mail, webserver or DNS?

What is the address you are trying to reach when inside the web browser?  Is it an IP address or DNS name?   If DNS name, your DNS server may not be working correctly if its resolving the name to a different server.   If re-directed to a different server, where did you end up?

> **af-crm said:**
> Where's a good place to start the research!?
It is best if you clarify exactly what the problem is with us in more detail...or check various logs.

LHammonds

---

### Post by SeijiSensei on 2021-05-12
Does the server contain all the mailboxes, e.g, files like /var/spool/mail/username? If so, I don't see an instance of dovecot in that list of running processes. Postfix is the program than handles incoming and outgoing messages. Dovecot provides the IMAP or POP interfaces required to read the mail stored on the server.  See [https://ubuntu.com/server/docs/mail-dovecot](https://ubuntu.com/server/docs/mail-dovecot)

If your organization uses "Maildir" rather than the default "mbox" mailbox format, then you need to make changes to some of Dovecot's configuration files as described in the piece cited above.

---

