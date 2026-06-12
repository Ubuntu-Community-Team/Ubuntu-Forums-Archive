---
title: "Securely allow ssh from desktop to laptop and vice versa"
date: 2011-05-24
forum: Security
---

### Post by krumpy on 2011-05-24
I want to set up my laptop to allow ssh access from my desktop and vice versa.  I've set both up to use rsa tokens and disabled password access in sshd_config.  My firewall wouldn't allow me to connect so I used to **ufw allow from 192.xxx** and everything worked fine.  Is there anything else I should do in order to make things secure?  Or is anything I mentioned above not the ideal way to go about things?

---

### Post by papibe on 2011-05-24
It sounds good.

I would make sure that both machines get the same LAN IP every time they connect to your network. Either by assign them static IPs or by checking that the router has "memory", and remember their MACs and always gave them the same addresses.

Just an idea.
Regards.

---

### Post by CharlesA on 2011-05-25
+1 to using the same IP. If the IP changes, ssh will complain about a new key or that the host key has changed.

Other then that, you should be good. :)

---

### Post by Lars Noodén on 2011-05-25
The static IP address is the better way to go.  There is the option of fiddling with the **known_hosts** file and allowing [multiple keys for an address](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Key-based_Authentication#Multiple_keys_for_a_host.2C_multiple_hosts_for_a_key_in_known_hosts) and multiple addresses for a key.  This a manual way to override the one-to-one mapping that occurs automatically when connecting.

---

### Post by krumpy on 2011-05-25
I'm pretty sure the IPs are static.  My router allows for DHCP reservation, so I just reserved those to IPs for my laptop and desktop.

---

### Post by CharlesA on 2011-05-25
> **krumpy said:**
> I'm pretty sure the IPs are static.  My router allows for DHCP reservation, so I just reserved those to IPs for my laptop and desktop.
That'll do it. :)

---

