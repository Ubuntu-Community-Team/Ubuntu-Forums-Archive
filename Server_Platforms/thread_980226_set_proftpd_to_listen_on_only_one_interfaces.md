---
title: "set proftpd to listen on only one interfaces?"
date: 2008-11-12
forum: Server Platforms
---

### Post by vitalyb on 2008-11-12
I'm running proftpd on Ubuntu 8.04.  Currently proftpd listens on port 21 for both interfaces.  I want to change proftpd to listen only on my internal network interfaces.  I can’t seem to find any options to set the listening interface.

Any help would be appreciated.  Thanks

---

### Post by vitalyb on 2008-11-13
any thoughts on this?

---

### Post by Philio on 2008-11-13
I assume you haven't looked at the manual (or google)? :)

[http://www.proftpd.org/docs/directives/linked/config_ref_DefaultAddress.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultAddress.html)

---

### Post by oneloveamaru on 2008-11-13
By default it binds to the IP that is realted to the "hostname". I'm sure there is a way, I am running it on a production server, give me a few minutes.

---

### Post by oneloveamaru on 2008-11-13
> **Philio said:**
> I assume you haven't looked at the manual (or google)? :)

[http://www.proftpd.org/docs/directives/linked/config_ref_DefaultAddress.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultAddress.html)

Well there is your fast answer! Now I know too!

---

### Post by vitalyb on 2008-11-14
Thanks for your replies.  

I've added the DefaultAddress line and set it to my internal address and get the confirmation "setting default address to 10.8.0.3" when I restart proftpd.  

However, when I do netstat -l, ftp service is still listening on all interfaces and I can still ftp on external interface.  Any ideas?

---

### Post by vitalyb on 2008-11-17
any ideas on what I am doing wrong?
Thanks.

---

### Post by hictio on 2008-11-17
Mmmhmh... Perhaps not a real reply to this, but, on the mean time, why don't you close/ limit the access to the FTP service using the internal (iptables) firewall?
Do you have it enabled on your server? Is it an option? 

The syntax would be something like this:

```

sudo ufw allow proto tcp from your.net to internal.ip.ftp.server port 21

```

Is it a passive FTP server? If so, you'll have to add the dynamic range for the ports on the 'PassivePorts' from your config file.

[b]
As always, if you only have remote access to your box, be sure to check and double and triple check before enabling/ editing/ starting the internal firewall.
[/b]

---

