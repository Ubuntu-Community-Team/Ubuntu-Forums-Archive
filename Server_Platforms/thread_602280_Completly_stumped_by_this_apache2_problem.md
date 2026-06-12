---
title: "Completly stumped by this apache2 problem"
date: 2007-11-04
forum: Server Platforms
---

### Post by digitalzen on 2007-11-04
*******SOLVED Thanks all for the help**************
where is the option to put [solved] in the title?

Hey all,

Im pretty new to hosting a webserver, but I would like to think I'm not a total idiot also. But this has me 100% stumped.

So I was running along on Feisty Fawn and made the upgrade to Gutsy with no problems. I just got married and wanted to post my wedding pictures. I forgot how to change the default directory which apache2 points to for the index.html page, so i thought I might as well remove and reinstall apache2. And thats where things got weird. I removed it, and re installed it... but it still pointed to the old directory (var/www/). So i tryed removing it again, and went to check the localhost page, and the external page via dyndns.org and its the old webpage is still up and running!!! 

I can change the index.html in var/www/ and it changes, and if i go to a incorrect page it gives the 404 page not found error and the "Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server...". How can this be?

I also checked webmin, and webmin gives me the "The Apache root directory /etc/apache2 does not exist." error msg. I went to System>administraton>sevices and unchecked (should this not already be unchecked?) the Webserver from there and nothing changed.... What am I doing wrong?

Suggestions?

**I may be giving up for the night, if you have any suggestions and or tutorials for Apache2 on Gusty please let me know **

---

### Post by Railsbuntu on 2007-11-04
Hi,

I saw on my thread that for you, when issuing:
```
sudo /etc/init.d/apache2 stop
```
didn't work

What gets printed on screen. When I do it, it works and I get:
```
 * Stopping web server apache2                                           [ OK ]
```
And apache stops serving the pages.

Did you try:
```
sudo killall -9 apache2
```

My server was installed from scratch. probably some of your problems came from the upgrade.

---

### Post by k_grdn on 2007-11-04
Hi digitalzen,

You need to change the DocumentRoot directive in /etc/apache2/sites-available/000-default and restart apache.

Regards,

k_grdn

---

### Post by tkharris on 2007-11-05
```

skill -KILL apache2
apt-get --purge remove apache2 apache
apt-get install apache2

```

---

### Post by conjur3r on 2007-11-06
You may have more than one apache variant installed.  Can you output the following command:

# dpkg -l | grep apache

---

