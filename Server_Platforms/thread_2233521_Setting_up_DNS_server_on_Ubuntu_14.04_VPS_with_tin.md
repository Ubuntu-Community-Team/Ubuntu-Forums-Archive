---
title: "Setting up DNS server on Ubuntu 14.04 VPS with tinydns/djbdns?"
date: 2014-07-09
forum: Server Platforms
---

### Post by AussieGuy on 2014-07-09
So - I have a brand new VPS running Ubuntu 14.04, and a domain name (registered to another company).  I need to set up a DNS server on my VPS, so that my new domain name is happily available to the outside world.  Now, although I have a lot of experience of desktop usage, I am a complete tyro at networking and web services.  So I'm in the dark here.

Just for example:

New domain name:  mybrandnewdomain.net

My current /etc/networking/interfaces file looks something like this:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 125.10.20.30
 netmask 255.255.255.0
 gateway 125.10.20.254
 dns-nameservers 115.115.115.100  115.115.115.200
#

```

and those nameserver addresses are written to resolv.conf on booting or restarting the network.  There are plenty of general guides about, but I'm totally confused about private and public IP addresses, and what should go where.   Can anybody point me in the direction of a tinydns guide suitable for ubuntu 14.04?  Or give me some helpful advice?

I am using webmin as a control panel, so if there's a module for that I could use it.  (There is a BIND module, but I understand that BIND uses a lot of memory, and with my cheap VPS I have only 1Gb.)

Thanks,
-A.

---

### Post by SeijiSensei on 2014-07-09
I'd first check to see whether your registrar will host your DNS records.  It would be a lot simpler for you than trying to set up and maintain a name server.  Moreover, you need to maintain two DNS servers to comply with Internet standards. Let your registrar do that.

---

### Post by AussieGuy on 2014-07-09
Yes, I'm trying to do that at the moment... we'll see how we go with it!  Gosh but this whole DNS business is confusing....

---

### Post by SeijiSensei on 2014-07-09
All you need right now is an "A" record that points [www.example.com](www.example.com) to your server's IP address, and maybe an MX record if you are going to run a server to handle mail for the domain.  The registrar will handle everything else.

---

