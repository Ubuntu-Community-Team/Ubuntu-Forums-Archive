---
title: "Setting up a private domain for a network of 30+ computers (with wireless)"
date: 2008-07-02
forum: Server Platforms
---

### Post by Georgie.Mathews on 2008-07-02
Hey there Ubuntugurus

I stay in residence, we are thinking of setting up our own private network with IRC, a forum etc. There are about 30+ computers, about 10 are connected with a normal router and we are planning to ge a wireless router and maybe bridge the two so ppl can also connect the same network wirelessly. This network will NOT be connected to the internet for now.

I just got a copy of the Ubuntu 8.04 Server Edition. I would like know if its possible to do the following:

1. Create a virtual domain for the server, so that ppl can just put server.residence.org in their chat client to connect to the servers ircd.
2. Will ppl on the wireless router also be able use the domain mentioned in point 1?

Your help will be greatly appreciated...

Thanks

---

### Post by cdenley on 2008-07-02
If you run your own DNS server, and your clients are configured to use that DNS server, you can create whatever domains you want for your clients.
```

sudo tasksel

```
Alternatively, you can edit the hosts file for each client.

---

### Post by Georgie.Mathews on 2008-07-03
I would like the Ubuntu server to run the DNS server...

---

