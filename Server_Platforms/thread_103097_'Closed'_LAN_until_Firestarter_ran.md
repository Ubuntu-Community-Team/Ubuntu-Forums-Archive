---
title: "'Closed' LAN until Firestarter ran"
date: 2005-12-13
forum: Server Platforms
---

### Post by DaveBentham on 2005-12-13
Hi

[Originally posted on Server Talk forum...]

I have a simple network: My Breezy PC - which connects to the internet AND the small LAN - serving various things (squid proxy, fetchmail/postfix/dovecot email, ssh, samba file shares) to my wife's Win2K box, which she uses for email, WWW and some shared folders on the Breezy box.

On the Win2K box, Email via Outlook Express, ssh client and SAMBA shares are all denied by the Breezy PC. WWW is fine. After I run Firestarter, the email, ssh and shares burst into life.

I do not understand this, as I thought FS was just a front-end, but here, simply running it up changes (opens) the network firewall. The only job I require of the firewall is between the Breezy PC and the internet; nothing should be blocked within the LAN, which is how I configured it within FS.

Any ideas?

Thanks
Dave

---

