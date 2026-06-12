---
title: "IRC hostname"
date: 2011-11-02
forum: Server Platforms
---

### Post by Checkeroogle on 2011-11-02
Hello,
I am setting up an IRC server, but all these clients are telling me I need a hostname. Can't I just use my public IP? What is a hostname? Do I have to register a domain to connect to my server?
Thanks

---

### Post by Checkeroogle on 2011-11-02
bump

---

### Post by jonobr on 2011-11-02
Your hostname (i guess) will be the address of the IRC server you setup.

If its a public IP address, I guess just enter the public IP address.
If its behind a Nat you will have to port forward to the server hosting the IRC server.


If you were totally on an internal network, you could enter IP address of the server, or set up naming service (or modify your host file) to point to the IRC server by name

The good thing about having hostname resolution is that you dont have to remember IP addresses and also, it allows devices to connect to the same machine by name even if the IP address may have changed (that would be done on DNS)
But I cant imagine that it would need a name as opposed to IP address (could always be wrong on that depending on the client)

---

### Post by Checkeroogle on 2011-11-03
> **jonobr said:**
> Your hostname (i guess) will be the address of the IRC server you setup.

If its a public IP address, I guess just enter the public IP address.
If its behind a Nat you will have to port forward to the server hosting the IRC server.


If you were totally on an internal network, you could enter IP address of the server, or set up naming service (or modify your host file) to point to the IRC server by name

The good thing about having hostname resolution is that you dont have to remember IP addresses and also, it allows devices to connect to the same machine by name even if the IP address may have changed (that would be done on DNS)
But I cant imagine that it would need a name as opposed to IP address (could always be wrong on that depending on the client)
Thanks, but the IP didn't work. I forwarded port 6666 which it said to do, but it still doesn't work. The only way it works is when I connect to localhost on the server itself with port 6666.

---

### Post by jonobr on 2011-11-03
can you connect from a different machine on the same lan with IP address?

If no, then It sounds like a configuration or access issue on your server,

---

### Post by Dangertux on 2011-11-03
What IRCD are you using?

You define your hostname in your ircd.conf , it doesn't have to be a FQDN (unless you want to do reverse lookups).

Hope this helps.

---

