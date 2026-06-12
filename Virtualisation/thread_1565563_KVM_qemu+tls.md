---
title: "KVM qemu+tls"
date: 2010-09-01
forum: Virtualisation
---

### Post by J&#7885;hn on 2010-09-01
Hi All

Can anyone give me some steps in setting up virsh so that it will migrate a guest using passwordless qemu+tls?

I can successfully migrate my guests using

```
[COLOR=#000000]virsh migrate --live lucidtest qemu+ssh://john@vm/system[/COLOR]
```[COLOR=#000000]

But the password prompt prevents me from writing a heartbeat script.

All the docs I can find refer to TLS administration of guests, which isn't what I'm looking for. I guess what I need is actually less complex than that, i.e. just two servers who trust each other through TLS.

TIA

John
[/COLOR]

---

### Post by sh1ny on 2010-09-01
Option 1 : use ssh rsa keys for authentication. It won't ask for password :)

Option 2 : [http://wiki.libvirt.org/page/TLSCreateCACertSteps](http://wiki.libvirt.org/page/TLSCreateCACertSteps) . Note that this was pending a tech accuracy review a few days ago, but it should get you on the right track :)

---

### Post by J&#7885;hn on 2010-09-07
How'd I miss that doc? 

I used ssh keys but ran into problematic aspects of user permissions. Hopefully TLS will remove the user issue. Thanks for this I'll give it a go

---

