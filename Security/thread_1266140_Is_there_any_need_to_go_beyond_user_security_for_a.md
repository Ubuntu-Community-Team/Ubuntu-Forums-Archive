---
title: "Is there any need to go beyond user security for a local MySQL database?"
date: 2009-09-14
forum: Security
---

### Post by Vunutus on 2009-09-14
I run a small office network or about 5 computers which all rely on one MySQL database for our production software. I'm wondering what kind of security I really need here.

So far, beyond the installation defaults, the only thing I've done is add a root password and make sure that user security is tight (users only allowed to connect from their specific workstation and granted only the bare minimum privileges they need to function). For a small network database that is not exposed to the internet (at least our router firewall is set to block its port), do I really need more security?

Assuming all users on the local network are trustworthy (and all wireless connections are shut down), what possible ways could an external attacker gain access to our database? The only service allowed to pass through our firewall is SSH, and I've already taken numerous steps to secure that (even beyond basic stuff like disabling password logins).

It may be a small database but it has some confidential information like customer SSNs and such, so we could be in legal trouble if it gets hacked.

---

### Post by falconindy on 2009-09-14
As long as your passwords are strong enough (and unique), it sounds like you're on the right track.

I presume the box that hosts the MySQL database is locked down properly as well? You say you've disabled password access through SSH... Does that mean you only allow keyfiles as auth? Did you change the port on the sshd?

What about the user workstations? Are they prompted for password entry to access the database? If so, are these passwords cached? Are machines locked down when employees aren't around (at night, at lunch, etc.)?

---

### Post by movieman on 2009-09-15
> **Vunutus said:**
> It may be a small database but it has some confidential information like customer SSNs and such, so we could be in legal trouble if it gets hacked.

In that case you should probably talk to a lawyer and/or investigate industry best practices for storing such data to ensure you won't get into legal trouble if it does somehow get hacked.

---

