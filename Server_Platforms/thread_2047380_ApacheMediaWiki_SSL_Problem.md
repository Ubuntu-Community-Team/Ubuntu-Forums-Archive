---
title: "Apache/MediaWiki SSL Problem"
date: 2012-08-24
forum: Server Platforms
---

### Post by Hans83VT on 2012-08-24
Hi there,

I've set up Ubuntu Server 12.04.1 with an Apache server running MediaWiki 1.19.1.  The wiki is the only web content on the server.  Everything works great, and now I'm trying to add SSL.

I got an SSL certificate from a CA and installed it in the /etc/ssl/certs and /etc/ssl/keys directories.  Then I modified the default-ssl file in /etc/ssl/sites-available to point to the crt and key file, and ran the commands "sudo a2enmod ssl" & "sudo a2ensite default-ssl" to enable SSL.

When I go to the site in a browser (tried both IE and Firefox), it says that only some content is secure.  This appears in IE to only be the text on the page - the rest of it does not show up until I click the "Show insecure content" button.

What do I need to do in Apache (or in MediaWiki?) to get force SSL for ALL content on the site?  Thanks in advance for your help!

---

### Post by sandyd on 2012-08-25
Check your LocalSettings.php
```
$wgServer
```
should point to **https**://your-site.com

---

### Post by Hans83VT on 2012-08-27
Perfect! Thank you.

---

