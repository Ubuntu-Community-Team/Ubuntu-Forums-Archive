---
title: "Fail2ban 0.9.3 email notifications ?"
date: 2015-11-10
forum: Server Platforms
---

### Post by rhandy2 on 2015-11-10
Fail2ban 0.9.3 have very diferent configuration files.

I can´t find where I can change setup > action = %(action_)s  to > action = %(action_mwl)s for ALL filters.

---

### Post by Habitual on 2015-11-10
You looked in /etc/fail2ban/jail.conf?

---

### Post by rhandy2 on 2015-11-10
I found it!!! using search.

But if I change to > [COLOR=#000000]*action = %(action_mw)s*[/COLOR]

It works!!

But if change to > [COLOR=#000000]*action = %(action_mwl)s*[/COLOR]

Error = > Job for fail2ban.service failed because the control process exited with error code. See "systemctl status fail2ban.service" and "journalctl -xe" for details.



---

### Post by TheFu on 2015-11-11
That error looks like a systemd error.  I don't run any Ubuntus with systemd, so haven't seen the fail2ban start/stop/restart or other handlers that systemd-compliant programs should have.

Hopefully someone will post the exact answer here for folks like me that wait for LTS releases + 2 months. I hope.  Fail2ban is important to our security. Even with ssh on strange, high ports, we see hundreds of attempts daily from hundreds of different IPs.

---

### Post by rhandy2 on 2015-11-12
I can run fail2ban but only with > *action = %(action_mw)s*

Fail2ban works and ban attacks!;)

---

### Post by mastablasta on 2015-11-12
> **TheFu said:**
> Hopefully someone will post the exact answer here for folks like me that wait for LTS releases + 2 months. I hope.  Fail2ban is important to our security. Even with ssh on strange, high ports, we see hundreds of attempts daily from hundreds of different IPs.

I wonder what the upgrade will do with fail2ban in these cases. I think I will stay on 14.04 for some time until stuff is ironed out. at least on server.

---

### Post by rhandy2 on 2015-11-12
I upgrade to 15.10 but without intension. 

Donwgrade is not so easy.

---

