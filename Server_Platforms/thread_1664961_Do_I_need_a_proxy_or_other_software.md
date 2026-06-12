---
title: "Do I need a proxy or other software?"
date: 2011-01-11
forum: Server Platforms
---

### Post by R.Bucky on 2011-01-11
I would like to configure an Ubuntu box with the sole purpose of using the internet connection remotely. For instance, if I were away on a business trip and browsing the internet, I want my IP to show up as one of my static IP's, versus the hotel IP. I believe that squid can do this for me, however I am uncertain which configuration option would be appropriate. Can someone shed some light on the correct software and provide a configuration example?

---

### Post by sj1410 on 2011-01-12
Yes you need to have a proxy server. Tinyproxy would be a good choice. 

But you need to take care of security.

---

### Post by R.Bucky on 2011-01-13
Finally have it all figured out. Squid works for me. I did try tinyproxy, however a bug in the package makes the initial install unable to bind to an external static IP. Aside from the over 4000 lines of configuration file in Squid, it seems to work for my purposes.

---

