---
title: "Apache 2.0  Problems"
date: 2007-08-31
forum: Server Platforms
---

### Post by ctlw83 on 2007-08-31
Hey All,

Ok, here is what is going on.  I have been trying every forum and/or Apache tutorial I can find with no success.  I have written my httpd file several times using both webmin and manual configuration, neither with success.

I want to run a name-based virtual host, using zone edit as my dynDNS group.  I have gotten one of my sites to show up on local host, but when I type in my external IP, I get nothing, server not found.  So I tried putting a static IP on the computer and DMZing the IP so it was outside of my router.  Still no luck.

I tried removing the default Virtual Host, which has now resulted in PHPMyAdmin not working despite its own virtual host entry.

I tried manually configuring the httpd file according to Apache 2's website documentation with no change.  So, right now, 1 site is serving to local host but not anywhere else, and PHP My admin can not be accessed because I removed the default virtual host.  Any ideas as to

1. Why typing in my external IP brings up nothing
2. How to add the default back in so my phpmyadmin entry is accessible again.


Thanks,
Chris

---

### Post by dmizer on 2007-09-01
most routers are unable to loop back your request to the server if you type in your external ip.  if you have your router forwarding the port correctly, then your site is probably visible.

on your client, edit your /etc/hosts file and add your server's local ip and domain like so:
```
192.168.1.2 yourdomainhere.com
```

---

### Post by ctlw83 on 2007-09-04
Thanks,

Will give that a try today and keep you posted...

---

