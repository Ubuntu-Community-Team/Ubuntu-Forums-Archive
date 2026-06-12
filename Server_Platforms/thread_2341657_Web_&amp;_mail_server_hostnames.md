---
title: "Web &amp; mail server hostnames"
date: 2016-10-30
forum: Server Platforms
---

### Post by thanuntu on 2016-10-30
Hello!

I am running a web server using Ubuntu 12.04 LAMP server edition, using a VPS with a static IP, and I am hosting my website at mydomain.org.

I recently decided to install a Mail Transfer Agent (e.g. Postfix) so that my Drupal installation can use PHP to send emails from the contact form to [email]info@mydomain.org[/email] through the SMTP server of a mail hosting service (Google Apps, Zoho, etc). So my web server will need need to double as a mail server, not a fully fledged one, but one that just forwards emails to a host's SMTP server.

I have done quite a lot of reading, but still am not clear about this. What I need is to properly set the /etc/hosts and /etc/hostname files.

Currently they are:

/etc/hosts
```
127.0.0.1 localhost mydomain.org
XXX.XXX.XXX.XXX mydomain.org
```

/etc/hostname
```
mydomain.org
```

and my web services work just fine (though I'm still having trouble with the mail server)

From what I understand I should rename my VPS as e.g. myserver.mydomain.org (by putting that in /etc/hostname) and then add a few lines in the /etc/hosts file:

```
127.0.0.1 localhost myserver.mydomain.org
XXX.XXX.XXX.XXX mail.mydomain.org mail
XXX.XXX.XXX.XXX web.mydomain.org web
```

Do I also need to add a 127.0.1.1 entry?

Sorry if the questions are really basic, but I haven't managed to understand this despite a lot of reading around.

Thanks!

---

### Post by TheFu on 2016-10-30
Support for 12.04 ends in a few months. Time to move to a newer release.  I'm doing the same here for my last few servers still on it.

You can put multiple names on the same IP line.  ```

XXX.XXX.XXX.XXX mail.mydomain.org mail  web.mydomain.org web
```

Also, don't put the public name on the 127.0.0.x lines. Only put the hostname there, not the FQDN for internet servers.
The value returned by `hostname` only matters a little, but not for mail or web servers.  Don't confuse a hostname with a DNS name.  It is often convenient to have those match, but not always and not required (unless some software requires it, often due to a lazy programmer or someone trying to simplify things). The OS doesn't care.

The only thing that might care about the hostname and IP are certs for email and HTTPS, though I've not had issues.

Having just the domainname in the /etc/hostname file isn't a good idea.  There can be issues.

---

### Post by thanuntu on 2016-10-30
Thanks a lot TheFu!

>  Support for 12.04 ends in a few months. Time to move to a newer release. I'm doing the same here for my last few servers still on it.

Yes, I know, but I dread the thought of something breaking during upgrade so I have been putting it off... but of course it must be done at some point!

Thanks for the rest of the pointers.

So, if I understand your suggestions correctly, a correct setup would be:

/etc/hosts
```

127.0.0.1 localhost myserver
XXX.XXX.XXX.XXX mail.mydomain.org mail  web.mydomain.org web
```

/etc/hostname
```
myserver
```

Regarding hostname, I have had different outputs (as my previous setup was) for the following commands:
```
hostname
mydomain.org
```
and
```
hostname -f
hostname
```

Do I need to restart some service to propagate the changes I make in /etc/hostname ?

---

### Post by TheFu on 2016-10-30
Some services have the hostname inside their config files. You might want to change those places too.
Which services should be reloaded, restarted, or rebooted isn't something I can answer. Don't know what you are running and I'm not an expert on some of those, I'm certain.

I would migrate to a new server, not do an upgrade.  Think of all the security things you've learned over these 4+ years?  Plus a clean install should be more stable for longer than an upgrade which leaves cruft behind.  In theory.

---

