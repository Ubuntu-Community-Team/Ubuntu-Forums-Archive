---
title: "Prevent Proxy Bypass"
date: 2010-02-11
forum: Security
---

### Post by momo971 on 2010-02-11
Hello !
I have a couple of questions concerning Proxies security.
In regard to this article:
[http://polishlinux.org/apps/ssh-tunneling-to-bypass-corporate-firewalls/ ]("http://polishlinux.org/apps/ssh-tunneling-to-bypass-corporate-firewalls/")

Is there any way to effectively block unwanted outgoing SSH traffic from an enterprise network to the Internet ?

It seems to me that proxy-firewall bypassing is always possible even in paranoïd security policies.

To resume the situation :

No filtering ? > port 22
Port 22 blocked ? > port over 49152 or 443
HTTPS blocked ? > corkscrew to http
http_connect disabled ? > double tunnel (httptunnel + ssh)
everything blocked ? > Not possible in my company !

Any help would be appreciated.
Thank you.

---

### Post by Sarmacid on 2010-02-11
I don't think you could effectively block it for good, there would always be a way to get around, however you've mentioned ways to make it harder on them. I haven't seen a company block corkscrew yet, even while having Websense deployed.

---

### Post by OpSecShellshock on 2010-02-13
This is where it helps to also have administrative controls in place. As long as it violates security policy and your IDS is looking for any outbound SSH traffic, you can find people who are doing it and tell them politely to knock it off. Granted, once the session has been established the communication will be encrypted, but I think there are ways to look for the actual session establishment.

Oh also: users should not have sufficient permissions to install anything themselves. Also also, you should consider having a local software repository that only contains approved applications and libraries in the first place, rather than using the defaults that come with the installation (at home it's fine, but in the enterprise you should have one controlled by the enterprise admins). This also helps in that it will enable you to test updates prior to deployment. It's like a mantrap except for software.

Mostly, though, just watch all outbound connections and flag anything that doesn't match the baseline.

---

