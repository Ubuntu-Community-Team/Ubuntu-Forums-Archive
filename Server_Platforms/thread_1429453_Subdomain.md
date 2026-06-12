---
title: "Subdomain"
date: 2010-03-14
forum: Server Platforms
---

### Post by cliftonbazaar on 2010-03-14
I have set up my ubuntu 9.1 server and I am now succesfully running 6 web sites, all with their own Vhost file.  Now I have tried to get a subdomain working but I can't get it too work.

Below is my Vhost file for the subdomain that I trying to get working but it doesn't :(

```
<VirtualHost *:80>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin koala@koalacomics.com.au
  ServerName  cricket.cliftonbazaar.com
  ServerAlias www.cricket.cliftonbazaar.com

  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.htm default.htm index.php default.php
  DocumentRoot /home/www/websites/www.cricket.cliftonbazaar.com

  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/www/websites/errors/cricket.cliftonbazaar.log
  CustomLog /home/www/websites/logs/cricket.cliftonbazaar.log combined

</VirtualHost>
```

Please note that this is a direct copy of my other vHost files so I know it works, it's just the word 'cricket' that is the only difference between this one and the [www.cliftonbazaar.com](www.cliftonbazaar.com) file.

---

### Post by Ryan Dwyer on 2010-03-14
Your server is configured fine. You just need to set up a DNS A/host record so cricket.cliftonbazaar.com will resolve to your server's IP.

---

### Post by cliftonbazaar on 2010-03-15
Thanks for that, I have it working now :)

---

