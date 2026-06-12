---
title: "How to ensure a smooth transition to Let's Encrypt SSL Cert?"
date: 2016-10-02
forum: Server Platforms
---

### Post by Grigoriy on 2016-10-02
Hello!

I've got LAMP running on Ubuntu 14.04 and almost a year ago I installed  SSL (TLS 1.2) certificate for my web server, so my site would only run  under HTTPS protocol. On October 8 the certificate expires. And from now  on I want to install and use Let's Encrypt. They have pretty good  tutorials on how to use Let's Encrypt, so (hopefully) I won't have any  issues with it. But I don't know what to do now. Must I wait till after  my old cert expires? Or should I go ahead and proceed with Let's Encrypt  installation ASAP? If the latter, then another question arises. How to  get rid of the old cert? I mean, it's probably NOT a good idea to use  two of them side by side. In short, too many things I don't understand.

---

### Post by TheFu on 2016-10-03
You can replace the cert at any point.

For apache2 systems, they've made it really simple.  I just setup 2 of my personal sites with LE a few days ago.  My notes:
```
sudo apt install letsencrypt python-letsencrypt-apache
sudo letsencrypt --apache --agree-tos --email webmaster@example.com -d www.example.com
sudo vi /etc/apache2/sites-available/nextcloud.conf ## Add LE stuff
sudo systemctl reload apache2

```

Then add a crontab entry to run **letsencrypt** before the cert expires - every 75 days?  Certs are for 90 days and can only be renewed after 30. I'd prefer to swap in a new cert 2 weeks early, so if there is any issue, I've got 2 weeks to solve it.  Being lazy, like I am, every other month is the root crontab.
```
# m h  dom mon dow   command
6 1 2 2,4,6,8,10,12 * /usr/bin/letsencrypt  renew
8 1 2 2,4,6,8,10,12 * /bin/systemctl reload apache2

```  That's even months, on the 2nd at 01:06a. Reload apache 2 min later.
Good enough?  Yes, the even months can be */2 instead.  Why on the 2nd and not the first?  If you are like me, lots of things happen on the 1st already. Don't need something like this too.  Why 6 min after 1am?  Enough things happen exactly at :00 with crontabs.  My system monitoring happens every min and data is centralized every 5 min ... picking an odd time helps. Another way would be to use a script and delay the start for 30 seconds to get a half minute delay. Anyway, that's my thought process.

Wish the LE script handled nginx as easily. I only run toy websites under apache. My important stuff is under nginx and using nginx as a reverse proxy.  I'll probably switch those over to LE this week.  Need to deal with an email cert too which will be very manual process.

---

### Post by Grigoriy on 2016-10-03
Ok, thanks!

---

### Post by TheFu on 2016-10-03
> **Grigoriy said:**
> Ok, thanks!

Those things returned an A- in the SSL test. To get an A+, I think encryption other than RSA needs to be used. Some of the elliptical methods. Figured I'd start with the easy answers and after a month, move to those.

LE checks that the domain is controlled by you and maps to the server you are running.  That means it needs to be on the internet already. Don't know if SSL has to be working (self-signed) prior or not. I had a self-signed cert.

For non-Apache webservers, I think they check a specific location for ".well-known" to ensure that the server <--> domain match. Make sure DNS resolves correctly.

---

