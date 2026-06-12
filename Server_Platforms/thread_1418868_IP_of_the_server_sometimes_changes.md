---
title: "IP of the server sometimes changes"
date: 2010-03-01
forum: Server Platforms
---

### Post by Dotan on 2010-03-01
Hi,

I am running a home server (my old laptop) and I want to be able to access it from a different network. the server is part of my LAN.

two questions:
how can I access it for a remote location, is there anyway to connect to my LAN? or should I establish a VIP network instead?

Question number two: is there anyway I can make my server to send me an E-mail with it's current ip? just to print the output of a specific command into an E-mail and send it?

Thanks,
Dotan.

---

### Post by stlsaint on 2010-03-01
> **Dotan said:**
> Hi,

I am running a home server (my old laptop) and I want to be able to access it from a different network. the server is part of my LAN.

two questions:
how can I access it for a remote location, is there anyway to connect to my LAN? or should I establish a VIP network instead?

Question number two: is there anyway I can make my server to send me an E-mail with it's current ip? just to print the output of a specific command into an E-mail and send it?

Thanks,
Dotan.

1)You need to setup [port forwarding]("http://en.wikipedia.org/wiki/Port_forwarding") via your router. Go in and forward your [SSH]("https://help.ubuntu.com/community/SSH") port to your server ip. That way you just connecto to your public ip and you will be forwarded to your server. Please view all the links on the ssh link i just provided, you will need all them and i strongly suggest you use key authentication over passwords when dealing with ssh.
2)There are some programs in synaptic package manager that should be able to help you with that.

---

### Post by Iowan on 2010-03-01
Have you considered setting up a static lease for your server in your DHCP server (based on MAC address)?

---

