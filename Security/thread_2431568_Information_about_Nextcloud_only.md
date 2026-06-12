---
title: "Information about Nextcloud only"
date: 2019-11-18
forum: Security
---

### Post by crip720 on 2019-11-18
Thought a few might be interested in this.  [https://soylentnews.org/article.pl?sid=19/11/18/0740201&from=rss](https://soylentnews.org/article.pl?sid=19/11/18/0740201&from=rss)  Ramsomware for nextcloud servers.

---

### Post by TheFu on 2019-11-18
A better known publisher:
[https://www.bleepingcomputer.com/news/security/new-nextcry-ransomware-encrypts-data-on-nextcloud-linux-servers/](https://www.bleepingcomputer.com/news/security/new-nextcry-ransomware-encrypts-data-on-nextcloud-linux-servers/)
> We've been looking into the reports on the forum and source of the virus. We are confident that the attack vector was the nginx+php-fpm security issue that hit the web some time ago.

Daily, versioned, "pulled", backups fix any malware issue, provided someone sees the problem before the versioned backups expire. 
Another solution is to use read-only NFS mounts for most files inside nextcloud.
Setup a reverse proxy that can filter bad/bogus requests - like base64 encoded data.
Only allow access to nextcloud over a VPN or ssh-based SOCKS proxy.
Of course, staying patched is critical.

I've been running nextcloud for a few years now and employ each of those techniques.  The VPN required alone should be sufficient for most nextcloud deployments.  We require VPN to access email too.

---

