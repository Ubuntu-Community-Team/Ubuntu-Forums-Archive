---
title: "How to configure WebDAV share via HTTPS"
date: 2010-03-07
forum: Server Platforms
---

### Post by TheForumDude on 2010-03-07
Looking for a good how-to on configuring Ubuntu Server to share a WebDAV share via HTTPS.

I've found a how-to on configuring Apache, and a how-to on configuring a self-signed certificate for HTTPS, and a how-to on configuring standard HTTP WebDAV, but nothing that integrates all three.

So I tried to just tackle each issue separately.  As a result, my web server is working using HTTP and HTTPS.  I also have a WebDAV share working via non-secure HTTP in digest mode (as opposed to basic authentication).  But when I try to connect to the WebDAV share from a Windows client by changing the URL from HTTP to HTTPS, I get an error saying, "The folder you entered does not appear to be valid.  Please choose another."  Removing the 'S' to go back to plain HTTP solves the problem and then Windows can connect.

Please advise, and thank you in advance for any assistance you can provide.

Thanks,
TheForumDude

---

