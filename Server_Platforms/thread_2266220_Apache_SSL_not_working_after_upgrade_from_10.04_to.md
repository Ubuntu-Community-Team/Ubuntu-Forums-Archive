---
title: "Apache SSL not working after upgrade from 10.04 to 14.04"
date: 2015-02-21
forum: Server Platforms
---

### Post by Eric Howland on 2015-02-21
After upgrade from 10.04 through 12.04 and on to 14.04 Apache SSL is not working, but I can log onto the site with HTTP:// Even with loging turned up to debug I do not see an error in the log files

Chrome gives the error: ERR_SSL_PROTOCOL_ERROR
Firefox gives the error: ssl_error_rx_record_too_long


Solution:
[COLOR=#000000][FONT=Arial]Move the configuration file in /etc/apache2/sites-available from subdomain-ssl to subdomain-ssl.conf.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Then to remove the old soft link (subdomain-ssl) in /etc/apache2/sites-enabled and then run a2ensite subdomain-ssl.conf

The clue was that a2dissite would report that there was no such domain as subdomain-ssl.  I do not know why HTTP was working since subdomain did not have the .conf extension either. [/FONT][/COLOR]

---

### Post by theonlyandy on 2015-08-21
Yo thanks a lot!

Just upgraded and ran into the same problem.

Apache didn't ask for my passphrase when starting, because the virtual host didn't load at all.

---

