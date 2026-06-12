---
title: "ufw and ssh question"
date: 2011-09-22
forum: Server Platforms
---

### Post by TheGuvernor on 2011-09-22
If I change my ssh port and then run the ufw command:

sudo ufw allow ssh

Will ufw automatically detect the ssh port like it does when it's on its normal port 22 or should I just allow the port I changed it to instead?

---

### Post by gmargo on 2011-09-22
**ufw** performs no magic; hence you must give it the port number.

---

### Post by mikeym on 2011-09-22
My guess would be that it uses the value in /etc/services

---

### Post by Dangertux on 2011-09-22
> **mikeym said:**
> My guess would be that it uses the value in /etc/services

This is correct unless you change the port in /etc/services it will not be reflected in your firewall rules.

The easiest way would be

```

sudo ufw allow 2222

```

Where port 2222 is the new SSH port.

you could also be more specific by doing something like

```

sudo ufw allow from any to 192.168.1.5 port 2222 proto tcp

```

or 

```

sudo ufw allow from 192.168.1.0/24 to 192.168.1.5 port 2222 proto tcp

```

Depending on how restrictive you want to be.

---

