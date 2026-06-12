---
title: "Error starting up 2nd instance of Apache on the same server (make_socket) on 12.04"
date: 2013-07-08
forum: Server Platforms
---

### Post by bsdux on 2013-07-08
Hello, all.

I am trying to set up 2 instances of Apache the same server on Ubuntu 12.04 64-bit using instructions found here /usr/share/doc/apache2/README.multiple-instances running on different ports.
But I could not start the 2nd instance due to a port conflict (make_socket) on port 61709. That is a strange port. I am not sure what part of Apache uses this port.
[ATTACH=CONFIG]244532[/ATTACH]

Please advise.


Thanks.

P.S: I tried posting this question earlier. Please pardon if it shows up twice.

---

### Post by DJ_Max on 2013-07-09
Apache only use ports you tell it to use. port 61709 isn't a commonly used port. 

So what ports did you tell Apache to use?

---

### Post by SeijiSensei on 2013-07-09
At a minimum you'll need a configuration for a virtual host like this:

```

<VirtualHost *:61709>
ServerName ...
</VirtualHost>

```

Note that this is for an IP-based virtual host.  If you also want to use name-based virtual hosts, the configuration is more complex.  In that case, you might want to clone /etc/apache2 into another directory and rewrite the configuration as needed.

One thing I've noticed with Apache is that if the interface and port you select are blocked by a firewall, you'll get the type of error you report, one that says Apache cannot bind to the port you selected.

---

