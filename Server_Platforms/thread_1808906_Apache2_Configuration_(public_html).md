---
title: "Apache2 Configuration (public_html)"
date: 2011-07-20
forum: Server Platforms
---

### Post by SGT Awesomesauce on 2011-07-20
Hi, 
I have a new server installation which I am trying to get to run solely internally on my network, and host a personal directory for each user registered on the server.  Basically what I am looking for is a /home/<username>/public_html/ path refering to a localhost/<username> on the server. I have tried symlinks from within the /var/www directory, and the userdir module that comes with apache2 package.  

Each time, it gives me a 404 error, but only in the user's directory.  I have PhpMyAdmin installed and am able to connect fine and work with that from my desktop with no problems whatsoever.  I have tried chmod on the public_html directory, to no avail.  Even with a chmod 777 there was no success in achieving access to the directory.  

Errorlog from apache:

```
[Wed Jul 20 19:34:43 2011] [error] [client 192.168.0.13] (13)Permission denied: access to /~system denied
[Wed Jul 20 19:34:43 2011] [error] [client 192.168.0.13] File does not exist: /var/www/favicon.ico
```

those two lines were spammed across the entire log. 


Any help will be greatly appreciated, 
The SGT.

---

### Post by Ryan Dwyer on 2011-07-21
# Enable the userdir module and restart Apache
sudo a2enmod userdir
sudo service apache2 restart
# Create public_html and a test file for a user on your system
mkdir /home/bob/public_html
echo "Test" > /home/bob/public_html/index.html

Then use a client machine to browse to [http://192.168.0.1/~bob/](http://192.168.0.1/~bob/) (or whatever your server's IP is).

The favicon 404s are happening because the client's browser requests this file automatically. Create an icon and save it as /var/www/facicon.ico if you want to stop it from appearing in the error log. You can use a PNG image renamed to .ico.

---

