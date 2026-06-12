---
title: "DHCP Server Question - Where do I put dhcpd.conf ?"
date: 2011-05-28
forum: Server Platforms
---

### Post by novafluxx on 2011-05-28
I've recently rebuilt my server that was running Fedora 14 with Ubuntu 11.04.

I have my configuration files for most of my services, but I'm having a problem with dhcpd.conf

The DHCP server that was contained in Fedora 14 is ISC DHCP, that's Fedora's default install when you install dhcpd.

In Fedora 14 I'd put dhcpd.conf in
```

/etc/dhcp/dhcpd.conf

```

Where do I place it in Ubuntu 11.04?

I read in the release notes for Ubuntu 11.04 that "Default dhcpd server updated from dhcp3 to isc-dhcp (version 4)"

So how do I install this and where do I place the configuration file?

The server guide tells me to install version 3, which doesn't make sense per the release notes...

Please help!

---

### Post by novafluxx on 2011-05-28
Apparently the package name is just ... wrong?

When I installed dhcp3-server is actually installs ISC DHCP version 4...

Sorry, the strange naming conventions used in Ubuntu threw me off...

---

### Post by Lars Noodén on 2011-05-29
Glad it's solved.  I'd also recommend taking a look at dnsmasq if you run into further issues.  It's much easier to configure and includes a lot of nice features.

---

### Post by novafluxx on 2011-06-04
Thank you. I will take a look.

---

### Post by amitdudhbade on 2011-07-25
Thanks for this post.

---

