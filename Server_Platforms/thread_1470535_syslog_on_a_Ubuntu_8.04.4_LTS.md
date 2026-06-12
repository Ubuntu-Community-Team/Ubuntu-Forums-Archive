---
title: "syslog on a Ubuntu 8.04.4 LTS"
date: 2010-05-02
forum: Server Platforms
---

### Post by boondocks on 2010-05-02
On this Ubuntu 8.04.4 LTS server, I want to log the messages from a Linksys router.

So I made this change to "/etc/init.d/sysklogd"
SYSLOGD="-r"

Then in "/etc/syslog.conf" I added the following to the top of the file:

```
if $fromhost isequal 'Linksys' then /var/log/Linksys.log
& ~

```

Then I rebooted the server.

But there is no "/var/log/Linksys.log" file.

What am I doing wrong?

---

### Post by tgalati4 on 2010-05-03
Is Linksys in your /etc/hosts file?

---

### Post by boondocks on 2010-05-03
> **tgalati4 said:**
> Is Linksys in your /etc/hosts file?

No Linksys is not in the /etc/hosts file.
How does that apply?

---

### Post by volkswagner on 2010-05-03
> **boondocks said:**
> No Linksys is not in the /etc/hosts file.
How does that apply?


It will tell your server where "Linksys" is.  Unless you are running a DNS server, or possibly winbind (I think).  Linux does not resolve host names without additional configuration.

---

### Post by tgalati4 on 2010-05-03
Try putting the IP address of Linksys in /etc/hosts.

---

