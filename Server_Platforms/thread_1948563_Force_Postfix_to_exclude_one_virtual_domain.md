---
title: "Force Postfix to exclude one virtual domain"
date: 2012-03-28
forum: Server Platforms
---

### Post by toyota_f1 on 2012-03-28
10.04.3 Server

Maybe this is a strange question, but I'm using EHCP as a control panel for simple hosting on my server.  In the setup of this it sets postfix to look at all the domains listed in the domains table of the EHCP database as local.

One of my domains has all of their mail managed by Google Apps.  With the right MX records this is not a problem except when they try to use contact forms.  Postfix looks at it's list of domains, sees that this domain is listed as a virtual domain, and then tries to send mail locally.  It never looks for DNS info because it is always looking at the mysql-virtual-domains.cf file which looks up the active domain list for the control panel.

Is there any way to force postfix to not look at one domain as local?  Any help would be appreciated.

Isaac

---

### Post by toyota_f1 on 2012-04-02
Here's what I did to make postfix use mx records instead of local for a specific domain...

Edit the following file

```
nano /etc/postfix/main.cf
```

Update your transport maps if it's not set.
I added hash:/etc/postfix/transport

transport_maps = hash:/etc/postfix/transport, proxy:mysql:/etc/postfix/mysql-virtual_transports.cf 

made the MX changes to domain for google apps

make the following addition in your /etc/postfix/transport file.

```
nano /etc/postfix/transport
```
mydomain.com smtp:

It'll force postfix to look at your MX records rather than trying to deliver the mail internally.

Run the following command to hash your transport file.
```

postmap /etc/postfix/transport
```

Reload your postfix configuration

```
postfix reload
```

---

