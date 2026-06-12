---
title: "Virus Wall"
date: 2013-02-15
forum: Server Platforms
---

### Post by createdcreature on 2013-02-15
I want to set up a server that will block out viruses from traffic that passes through it, therefore eliminating viruses from any Windows PCs connected to the network. How would I do it?:confused:

---

### Post by chrisguk on 2013-02-15
I don't see why you would want to do this.  Even in large networks the virus software is loaded onto the client.  Plus I believe it would put extra unnecessary load on the server too.

---

### Post by haqking on 2013-02-15
> **chrisguk said:**
> I don't see why you would want to do this.  Even in large networks the virus software is loaded onto the client.  Plus I believe it would put extra unnecessary load on the server too.

In the vast majority of large and commerical networks AV/Anti Malware solutions reside on a server first of all aside form the client side solution.

Most firewalls/email servers will do active scanning using the same solutions as client side but optimised for servers or enterprise environments.

Juniper
Barracuda
Checkpoint 

etc etc all offer or are usually configured with a AV solution to filter out this type of stuff before it hits the client.

One example: [http://www.kaspersky.com/anti-virus_checkpoint_firewall](http://www.kaspersky.com/anti-virus_checkpoint_firewall)

---

### Post by lykwydchykyn on 2013-02-15
You could set up Squid as a proxy server, then set up scanning with clamav.  I think there are some projects out there that have this all setup, like [http://squidclamav.darold.net/](http://squidclamav.darold.net/).

Clamav isn't a great AV engine, but maybe you can integrate other AV engines with squid.

---

