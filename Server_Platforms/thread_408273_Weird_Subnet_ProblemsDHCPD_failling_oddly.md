---
title: "Weird Subnet Problems/DHCPD failling oddly"
date: 2007-04-13
forum: Server Platforms
---

### Post by BitHosts on 2007-04-13
Hey all,

I have a DHCP server that needs to be set up with the following subnet:

10.1.2.0 - 255.255.255.0

Except if its given that configuration it fails to start the dhcpd process.  If i change it and give it:

10.1.1.0 - 255.255.255.0

It works perfectly.  Anyone got an explanation/solution?

Cheers!

Felix

---

### Post by BitHosts on 2007-04-16
I take it that means no one has any ideas? ...poo

---

### Post by paul.maddox on 2007-04-16
Strange, there must be some other factors involved in this issue.

Has dhcpd outputed anything to the logs in /var/log?

Do you have any other DHCP servers within the 10.1.2.0?

Is 10.1.2.0 the only subnet that fails? What about if you try a few other random ones?

---

### Post by BitHosts on 2007-04-16
In all honesty I dont have access to this machine at the moment - it is the only one in the network though, but the plan was to intigrate it with another on a different subnet at a later date.  Ill have to have a play around - but thats going to be later.  Was wondering if anyone had an instant answer, but clearly its weirder than that.

Cheers anyway!

---

