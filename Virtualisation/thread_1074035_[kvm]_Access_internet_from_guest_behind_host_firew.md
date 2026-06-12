---
title: "[kvm] Access internet from guest behind host firewall"
date: 2009-02-18
forum: Virtualisation
---

### Post by gecka on 2009-02-18
Hello,

If you have correctly set up your firewall, a libvirt (KVM) guest cannot access the internet.

To allow guest to access internet you cannot use ufw (will not work) from command line, you should edit /etc/ufw/before.rules and add for each guest (assuming the guest ip is 10.0.0.1)

```

-A FORWARD -d 10.0.0.1 -j ACCEPT
-A FORWARD -s 10.0.0.1 -j ACCEPT

```

And then restart ufw service:

```
sudo service ufw restart
```

Hope that helps. 

Note: if someone has an automatic way to do this just tell me!

---

### Post by tc7 on 2009-03-10
Great post - exactly what I was after.

The symptom: guest os can only access host.
Denied access logs fill host os /var/log/messages

I found the following did the trick:
# allow access from kvm guest
-A FORWARD -d 10.1.1.0/24 -j ACCEPT
-A FORWARD -s 10.1.1.0/24 -j ACCEPT

---

### Post by gecka on 2009-03-10
> **tc7 said:**
> Great post - exactly what I was after.

The symptom: guest os can only access host.
Denied access logs fill host os /var/log/messages

I found the following did the trick:
# allow access from kvm guest
-A FORWARD -d 10.1.1.0/24 -j ACCEPT
-A FORWARD -s 10.1.1.0/24 -j ACCEPT

I should have thought about that /24 .... :o

Thks

---

