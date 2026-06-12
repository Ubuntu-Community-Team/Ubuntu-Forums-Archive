---
title: "Can't recieve email"
date: 2009-10-16
forum: Server Platforms
---

### Post by kevin11951 on 2009-10-16
I have a fresh install of ubuntu 9.04 server, and a mail server via "tasksel install mail-server" and squirrelmail.  Everything is working and I can send emails all day long, but I cant receive any.

here is my bind dns configuration:

```
$ttl 38400
kviero.com.	IN	SOA	kviero.com. ksoviero.gmail.com. (
			1255658583
			10800
			3600
			604800
			38400 )
kviero.com.	IN	NS	kviero.com.
kviero.com.	IN	MX	10 192.168.2.2
kviero.com.	IN	A	192.168.2.2
*.kviero.com.	IN	A	192.168.2.2

```

---

### Post by Bachstelze on 2009-10-16
A MX record **must** be a hostname, not an IP address. Also you are aware that what you use here are private IPs and will be useless when you will try to communicate with the outside world, right?

---

### Post by kevin11951 on 2009-10-16
> **Bachstelze said:**
> A MX record **must** be a hostname, not an IP address. Also you are aware that what you use here are private IPs and will be useless when you will try to communicate with the outside world, right?

the dns server is inside my network, and is a dmz.

---

### Post by drumbug1 on 2009-10-16
For incoming e-mail troubleshooting, I find MX Toolbox is a handy site.  According to this site the problem is definitely with your DNS:

[http://www.mxtoolbox.com/SuperTool.aspx?action=mx%3akviero.com](http://www.mxtoolbox.com/SuperTool.aspx?action=mx%3akviero.com)

When that site does the lookup for your domain, it's reporting 0.0.0.0 - which obviously isn't going to get you anywhere.  I agree with Bachstelze that you need to define your MX as a hostname.  I think that's the root of your problem.

Regarding the fact that your DNS server is inside your network - that means that you can access it via it's private IP (because you're on the LAN I'm assuming), but the record that it reports (or 'serves') to the world needs to reflect your "public" IP..... otherwise no other mail servers can "find" you on the internet... right now you're telling everyone that if they look for kviero.com that it's at 192.168.2.2.... which doesn't mean anything unless they are on your LAN.

The only time that a DNS server configured like yours would work would be for an internal-only e-mail system... not internet e-mail like you're trying to do.

:)

---

### Post by kevin11951 on 2009-10-17
> **drumbug1 said:**
> For incoming e-mail troubleshooting, I find MX Toolbox is a handy site.  According to this site the problem is definitely with your DNS:

[http://www.mxtoolbox.com/SuperTool.aspx?action=mx%3akviero.com](http://www.mxtoolbox.com/SuperTool.aspx?action=mx%3akviero.com)

When that site does the lookup for your domain, it's reporting 0.0.0.0 - which obviously isn't going to get you anywhere.  I agree with Bachstelze that you need to define your MX as a hostname.  I think that's the root of your problem.

Regarding the fact that your DNS server is inside your network - that means that you can access it via it's private IP (because you're on the LAN I'm assuming), but the record that it reports (or 'serves') to the world needs to reflect your "public" IP..... otherwise no other mail servers can "find" you on the internet... right now you're telling everyone that if they look for kviero.com that it's at 192.168.2.2.... which doesn't mean anything unless they are on your LAN.

The only time that a DNS server configured like yours would work would be for an internal-only e-mail system... not internet e-mail like you're trying to do.

:)

I changed all my dns info to reflect my public ip, and now everything works!! thank you!

---

