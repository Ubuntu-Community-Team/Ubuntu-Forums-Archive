---
title: "client &gt; HTTPS &gt; Squid &gt; www."
date: 2009-06-25
forum: Security
---

### Post by SlugSlug on 2009-06-25
I'm wondering if it's possible to configure Squid (and a browser) so that the client makes the connection to the proxy over HTTPS even though the final web server connection is only HTTP (or HTTPS).

I would like to run a proxy server on my linux box at home and then use that as a proxy from other places.

can I configure squid (or even a browser for that matter) to connect with something like:
Browser client => HTTPS => squid proxy => www.

---

### Post by Trebaruna on 2009-06-25
Wouldn't it be easier to setup an SSH tunnel to act as a proxy and direct your traffic over it?

See: [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic%20port-forwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic%20port-forwarding)

---

### Post by SlugSlug on 2009-06-28
> **Trebaruna said:**
> Wouldn't it be easier to setup an SSH tunnel to act as a proxy and direct your traffic over it?

See: [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic%20port-forwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic%20port-forwarding)

yer it would be easier - much easier - but wheres the fun in that?

---

