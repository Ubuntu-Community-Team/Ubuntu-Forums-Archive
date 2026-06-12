---
title: "SITE not available!"
date: 2008-06-21
forum: Server Platforms
---

### Post by amai on 2008-06-21
Have created 3 wesites
xxxx12.com(FIRST SITE to be CREATED)
yyyy34.com
zzzz56.com

My PC is directly connected to the server 192.168.1.13.
When I type 192.168.1.13==i got the list of all my websites

When I type 192.168.1.13/xxxx12.com==from the pC=== I get correct website
When I type 192.168.1.13/yyyy24.com==from the pc=== I get correct website
When I type 192.168.1.13/zzzz56.com==from the pc=== I get correct website

Issues.

1) When I do the command
sudo a2ensite www.xxx12.com===>works fine
BUT
sudo a2ensite www.yyyy43.com===>SITE not available
sudo a2ensite www.zzzz56.com===>SITE not available
WHY do I get SITE not available for the other two sites created later.
HENCE if I do the command
var/www# ls 
all three sites are list

2)I cant get nano to open the configure to edit the site
-sudo nano [www.xxxx12.com](www.xxxx12.com)
brings nano with black blank screen, same as well if I use VI.
this is happening on all three sites. How do I get to the configure so i could make some changes.
(Have searched on the net but all i could get was how to change the settings but not how to get there)
What command to use.

3)The site have been created as follows:


1)  cd /etc/apache2/sites-available/

2)  sudo cp default [www.xxxx12.com](www.xxxx12.com)

3)THEN i did edit the config(was able to get to it only once per site, but not anymore)

NameVirtualHost *:80

<VirtualHost *:80>

ServerAdmin webmaster@localhost

DocumentRoot /var/www/xxxx12

ServerName [www.xxxx12.com](www.xxxx12.com)

4) Created the website directory /var/www/xxxx12.com

5)sudo chown -R www-xxxx12 /var/www/xxxx12.com

***

I then followed the same steps from 1 to 5 creating other two sites(just changing the name)

Ta..

---

### Post by amai on 2008-06-21
Tried 
/etc/apache2/httpd.conf 

still no go

---

### Post by mbeach on 2008-06-21
In order for virtual hosts to work, apache needs to know which host you are requesting.  If this is all internal, the easiest way to do that is to amend your hosts file
Windows:
c:\windows\system32\drivers\etc\hosts
Linux
/etc/hosts

You want to have a couple of lines in your pc's hosts file like:
```
192.168.1.13   www.xxx12.com
192.168.1.13   www.yyyy43.com
192.168.1.13   www.zzzz56.com
```

Then in your browser on your pc navigate to: [www.zzzz56.com](www.zzzz56.com)

Not sure why you are changing the ownership on the files.  If need be, you probably want to be using:
```
sudo chown -R www-data:www-data /var/www/xxxx12.com
```
unless you have apache doing something very different than the default setup.

Also, if you 
```
cd /etc/apache2/sites-available
ls -la
```
you should see the list of files available as sites.  If you indeed have them named as you say, you should be able to:
```
vi www.yyyy43.com
```
If not, I'd look to make sure they have a filesize greater than zero, perhaps change the ownership to www-data by
```
sudo chown www-data:www-data /etc/apache2/sites-available/www.yyyy43.com 
```
or try copying from the default again, and making necessary changes.
```
cd /etc/apache2/sites-available
sudo cp default www.yyyy43.com

```

Good luck,
mb

---

