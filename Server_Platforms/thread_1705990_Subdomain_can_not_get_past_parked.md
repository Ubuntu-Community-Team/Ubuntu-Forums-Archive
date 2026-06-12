---
title: "Subdomain can not get past parked"
date: 2011-03-13
forum: Server Platforms
---

### Post by Kozley on 2011-03-13
Hi,

I do not understand why does not works of my apache configuration for subdomains. All of subdomains is still parked when I try to create subdomain.
Sorry, I cannot show parked site to you that parked site is on swedish, if you do understand swedish and I'ill pm you with the address.

Here's httpd.cf:
```
NameVirtualHost *:80

<VirtualHost *:80>

DocumentRoot /var/www
<Directory />
Options FollowSymLinks
 AllowOverride None
</Directory>
</VirtualHost>

<VirtualHost *:80>
ServerName forum.mydomain.com
DocumentRoot /var/www/forum
</VirtualHost>

<VirtualHost *:80>
ServerName static.mydomain.com
DocumentRoot /var/www/static
</VirtualHost>
```
Error of NameVirtualHost 80 after restart apache2 is fixed.

/etc/hosts:
```
192.168.1.2    mydomain.com    # Added by NetworkManager
127.0.0.1    mail.mydomain.com    mydomain.com    localhost.localdomain    localhost
::1    mydomain.com    localhost6.localdomain6    localhost6

127.0.0.1    forum.mydomain.com
127.0.0.1    static.mydomain.com

192.168.1.2    forum.mydomain.com
192.168.1.2    static.mydomain.com

#::1    mydomain.com    localhost6.localdomain6    localhost6
#127.0.1.1    mydomain.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Anyone have idea to solve the subdomain problems?
Please, do not send howto links or weird sentence!

---

### Post by mimor on 2011-03-13
Why did you put it in your hostfile?
They're all on your local machine?

---

### Post by Kozley on 2011-03-13
> **mimor said:**
> Why did you put it in your hostfile?
They're all on your local machine?

I did found it from howto site. Yes, they're all on my local machine.

---

### Post by volkswagner on 2011-03-13
Did you add appropriate DNS entries (A Record) for each subdomain?

I prefer having virtual hosts as separate files under /etc/apache2/sites-available as in the [Apache2 documentation]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") for virtual hosts.

---

### Post by Kozley on 2011-03-14
> **volkswagner said:**
> Did you add appropriate DNS entries (A Record) for each subdomain?

I prefer having virtual hosts as separate files under /etc/apache2/sites-available as in the [Apache2 documentation]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") for virtual hosts.

I didnt add DNS entries for each subdomain but I should call to my web hosting and check if it's needed otherwise vhost.

UPDATE: Now it works. Thanks you for the help!

---

