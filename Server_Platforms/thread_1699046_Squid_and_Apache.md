---
title: "Squid and Apache"
date: 2011-03-03
forum: Server Platforms
---

### Post by Zitan on 2011-03-03
This is my Squid configuration

```

http_port 3128 transparent
acl work src 192.168.16.0/24
acl websites dstdomain "/etc/squid/blocked_websites.acl"
acl files urlpath_regex "/etc/squid/blocked_files.acl"
acl boss src 192.168.16.12
acl it_user src 192.168.16.5
acl WindowsUpdate dstdomain -i “/etc/squid/windowsupdate.acl”
no_cache deny WindowsUpdate
http_access allow it_user
http_access allow boss
http_access deny files
http_access deny websites
http_access allow WindowsUpdate
http_access allow work


```

I need access to a web server, phpmyadmin, phpldapadmin, etc.  from Internet. How to change squid configuration

---

### Post by mciverza on 2011-03-03
Are you trying to access resources on your Local Area Network from the internet?

Or trying to access internet resources from your LAN? (which is what squid is usually used for)

---

### Post by Zitan on 2011-03-03
I want to have access to a web server (port 80) on the local network (at work), from my house.

---

### Post by mciverza on 2011-03-03
> **Zitan said:**
> I want to have access to a web server (port 80) on the local network (at work), from my house.

Then you don't need squid for that. 

Can you describe your network layout, or better -- draw it.
Is it something like:

NET --+router+----server
                   +
                    |
        your pc

---

### Post by Zitan on 2011-03-03
lan=(Router --> eth0 --> SERVER + Apache and some other  --> eth1 --> Masquerade --> 15 Users

Squid is used to block some websites for users, but on same server there is also phpmy admin, phpldapadmin, ocsinventory and few more. My router is configured for dynamic DNS. Unfortunately Squid is also blocking access to localhost for computers outside of network. One more time in difrent way this time, on my LAN when I go to 192.168.16.1 everything is working OK, but in my house when i go to [http://mysicredipadress.com](http://mysicredipadress.com) Squid shows up with "This site is blocked for security reasons contact witch admin" this is the same information like for blocked sites in my network... why???

---

### Post by SeijiSensei on 2011-03-03
As always, logs are your friends.

Look at access.log for squid and see what IP address generates this error.  In your rules, only machines in 192.168.16.0/24 can pass through the proxy.  Depending on how your router forwards traffic back to the server, it might be using its own address, which is presumably in the same subnet, or it might be passing through the unmodified external source address, which will be blocked.

---

