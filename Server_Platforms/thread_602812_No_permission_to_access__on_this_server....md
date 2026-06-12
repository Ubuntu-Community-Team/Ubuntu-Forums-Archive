---
title: "No permission to access / on this server..."
date: 2007-11-04
forum: Server Platforms
---

### Post by Enissay on 2007-11-04
Hello,
I worked in generating html pages from xml-xsl....
When i got this error "Warning: XSLTProcessor::transformToUri(save.xml) [function.XSLTProcessor-transformToUri]: failed to open stream : : Permission denied in '/var/www/dvd.php'"
I looked for solution on google, And I found this "chmod 744 /var/www/" to modify acces permissions, ....
After i got this error!!!!
> Forbidden

You don't have permission to access / on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80

I don't know what happen...
Thks for helping me

---

### Post by Enissay on 2007-11-04
I did this too > chmod a+r /var/www/
But with no result

---

### Post by Enissay on 2007-11-04
It works with 
> chmod 755 /var/www/
THks

---

