---
title: "Should I uninstall SSH for security?"
date: 2011-07-10
forum: Security
---

### Post by nrundy on 2011-07-10
Far as I understand it, SSH provides an encrypted way of establishing connections with remote desktops? I don't connect to any remote desktops.

Assuming this is all SSH is good for, would I enhance my security by uninstalling SSH from my box?

---

### Post by Irihapeti on 2011-07-10
The SSH that is part of a default desktop install is a _client_ only. No one can connect to it.

As I see it, removing it would make no difference at all to your security.

If you've installed SSH server, that's a different matter. In that case, it's a good idea to remove it if you don't need it.

---

### Post by dirtrider1 on 2011-07-11
> **nrundy said:**
> Far as I understand it, SSH provides an encrypted way of establishing connections with remote desktops? I don't connect to any remote desktops.

Assuming this is all SSH is good for, would I enhance my security by uninstalling SSH from my box?

SSH allow's you to do many thing's but yes it's basic use allow's you to login to a remote terminal. Theoretically disabling any service that allows an outside connection to connect to it will enhance security , but in practical term's it just depends on what you are trying to do with it and how secure you set it up. Using SSH to securely administrate remote headless servers is common practice when using Linux and it can be made very secure, but at the same time SSH would be one of the worst services you could have running if it is not setup securely.

---

