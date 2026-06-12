---
title: "Apache slow?"
date: 2009-04-23
forum: Server Platforms
---

### Post by happyhacker on 2009-04-23
I have installed Apache and a Drupal website. I find that it takes the system (server to XP laptop on the local network) about 5-8secs to deliver a page. I also have installed WAMP on the laptop and this takes about the same time to deliver a page to itself (if that helps any as a comparison). I want users on other PCs on the local network to access this website.

Has anyone any advice on why page delivery is slow (if that is the case) and how i might go about imnporving it (if that is possible)?

The server hardware is an old (2Ghz) PC used for backups (not running at the time). The network is eth. at 100Mb/s.

---

### Post by spynappels on 2009-04-23
Hi,
How are you accessing the server? Are you using a FQDN or the server name or the LAN IP?
You could try accessing it in a different way, (just LAN IP), to rule out DNS issues.
Try using a different Browser such as Google Chrome or Firefox to rule out browser settings or try disabling the Firewall on your XP machine if it is running to see if that makes any difference.

---

