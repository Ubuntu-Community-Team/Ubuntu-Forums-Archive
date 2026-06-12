---
title: "apache2: localhost responds only when connected to internet"
date: 2010-05-12
forum: Server Platforms
---

### Post by Devakishor on 2010-05-12
Hi All,

I am on Ubuntu 10.04 LTS. Installed LAMP yesterday using: ```
sudo tasksel install lamp-server
``` Tested Apache, PHP, MySQL then, all worked fine. 

But today when I tried to access localhost, and other sites saved at '/var/www/' even though apache2 was running fine..... until I connected to the internet(through Wi-fi). I figured out the connection between the Wi-Fi and the problem by accident. 

Another thing that I noticed was, when I tried to restart apache2, I got the error.> apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Not sure if this is the cause of the problem but.. note the '127.0.1.1' instead of the normal '127.0.0.1' in the error message.

This error messaged has now been fixed by running ```
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
```

but the problem still persists.

Even when apache2 is running fine, I cannot access localhost(tried [http://127.0.0.1](http://127.0.0.1) and [http://127.0.1.1](http://127.0.1.1) also), or any site saved at '/var/www/ when I am not connected to the internet through Wi-fi.

Can anyone help me out. I am a noob.

---

### Post by Devakishor on 2010-05-12
Problem solved. Turns out Chrome(and my stupidity) was the culprit.

It seems, Chrome does not load local pages without net connection.

*facepalm*

---

