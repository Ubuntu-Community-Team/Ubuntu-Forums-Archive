---
title: "Iptables question"
date: 2008-07-28
forum: Security
---

### Post by Mumbly on 2008-07-28
I have an SMTP server (Postfix) setup that is accepting incoming connections for my domain. I have port 25 open to the internet in order to accomplish this. I have verified that the system is not acting as an open relay through various testing methods such as [http://www.abuse.net/relay.html](http://www.abuse.net/relay.html) and others.

The problem is that port 25 is responding to scan requests like Shields Up!, and I'd like to stop that from happening.

My question is this: Can I setup iptables on the server to drop ICMP requests, and still have it accept SMTP and other requests (Samba, Apache, etc.)? Is ping required in order for these connections to work?

Thanks in advance for the help!

---

### Post by The Cog on 2008-07-28
Ping is not required for email to work. But shields-up doesn't scan your ports with ping - it scans them by trying to connect to them. The only way you can stop it from responding is to stop it accepting connections from the internet.

You can of course confgure your firewall so that only certain pre-defined IP addresses can connect to your mail server, but that is only feasable if you know in advance where your incoming mail will come from.

---

