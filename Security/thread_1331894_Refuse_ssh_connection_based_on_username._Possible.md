---
title: "Refuse ssh connection based on username. Possible?"
date: 2009-11-19
forum: Security
---

### Post by microft on 2009-11-19
Hello.
This question came from a discussion between myself and a work colleague.

Is it possible to deny connection (get a "Connection refused" error on the client) based only on the username used in the connection?
I'm not just talking about sshd configuration, but also iptables/firewalls or even QoS stuff.

Other questions that my help clarify this are:
- is the username sent when the initial connection is made?
- is the username sent in plain text?

Thanks! :KS

---

### Post by Seraphim x on 2009-11-19
I do not believe the main question is  possible. The "Connection Refused" is due to the protocol port request being dropped (in this case port 22). This may be filtered by IP address or Host name *but the user name is not in the initiating packets. ** Out of the box, the user name **is** sent in plain text.

Hope this helps ;)

---

### Post by FuturePilot on 2009-11-19
I'm pretty sure this will do what you want. It's basically a whitelist. Anyone not on the list won't be able to login.

Add to your sshd_config
```
AllowUsers user1 user2 user3
```

Separate the users with a space.

---

### Post by cdenley on 2009-11-20
> **FuturePilot said:**
> I'm pretty sure this will do what you want. It's basically a whitelist. Anyone not on the list won't be able to login.

Add to your sshd_config
```
AllowUsers user1 user2 user3
```

Separate the users with a space.

This will prevent them from authenticating. They can still establish a TCP connection and attempt authentication. As Seraphim x said, you can't determine the username they are attempting to use until the TCP connection was already established and their client sends the username they wish to authenticate as. The authentication will either succeed or fail depending on the server's configuration and the user's credentials. This authentication attempt is logged in /var/log/auth.log. You can then use fail2ban to prevent further connections from the user's IP based on this logged event, if you wish.

---

### Post by kadeous on 2009-11-20
As CD said above, use Fail2ban. It's extremly easy to configure and checking my log files show's it's working rather well. I've been using Ubuntu for a week now so I'm still rather new, if I can do it you can! :p

---

### Post by hictio on 2009-11-21
I'm not completely sure, but I **guess** that you might accomplish this using the [pf firewall](http://en.wikipedia.org/wiki/PF_%28firewall%29).
I know that it can do OS fingerprinting, so there might be a module, or way of doing what you want.

---

### Post by The Cog on 2009-11-21
It is not possible to refuse connections based on the username because until the connection has been accepted, the client can't tell the server what the username is. The best the server can do is to drop the connection once it has been told the caller's username.

---

