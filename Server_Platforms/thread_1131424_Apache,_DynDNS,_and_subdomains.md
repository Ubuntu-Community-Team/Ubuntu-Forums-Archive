---
title: "Apache, DynDNS, and subdomains"
date: 2009-04-20
forum: Server Platforms
---

### Post by cmwslw on 2009-04-20
I have successfully configured my server with DynDNS and it works great. My domain is clustur.com. I really want to have subdomains, though. I've looked at many tutorials, but I'm so confused because every tutorial I find is different to my situation. The fact that Ubuntu's apache has a split httpd.conf doesn't help either. Here's what I've tried so far.
[LIST=1]
[*]I've commented out NameVirtualHost in /etc/apache2/ports.conf
[*]I've created clustur.com.conf in /etc/apache2/sites-available:
```
<VirtualHost *>
ServerName www.clustur.com
DocumentRoot /var/www
</VirtualHost>

<VirtualHost *>
ServerName nxtpp.clustur.com
DocumentRoot /var/www/nxtpp
</VirtualHost>

```
[*]Made the symlinks:
```
sudo a2ensite clustur.com.conf
```
[*]Restarted apache
[/LIST]

I get "Firefox can't find the server at nxtpp.clustur.com." whenever I try to access the nxtpp subdomain. I have index.php in the /var/www/nxtpp folder. Do I need to a2dissite default? What am I doing wrong?

Thanks in advance,
-Cory Walker

---

### Post by MaindotC on 2009-04-20
When I try I get "Welcome to SIXLA".

---

### Post by cmwslw on 2009-04-20
> **strAlan said:**
> When I try I get "Welcome to SIXLA".

Well I have no idea why you got that (wrong url maybe?). Should I have wildcard enabled on my DynDNS settings? I already tried enabling it and it makes any subdomain direct to my /var/www folder.

---

### Post by Thirtysixway on 2009-04-20
It's working for me.  Displays a page with 4 links on it.

---

### Post by cmwslw on 2009-04-20
> **Thirtysixway said:**
> It's working for me.  Displays a page with 4 links on it.

That's /var/www/index.php. I need nxtpp.clustur.com to display /var/www/nxtpp/index.php.

EDIT: I'm making progress. I followed Tchalvak's post at [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/268868](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/268868), and now when I visit nxtpp.clustur.com, I am redirected to [http://nxtpp.clustur.com/nxtpp/index.php](http://nxtpp.clustur.com/nxtpp/index.php). The problem is, this is actually referring to /var/www/nxtpp/nxtpp/index.php instead of /var/www/nxtpp/index.php. How can I fix this so I am redirected to just nxtpp.clustur.com/index.php?

---

### Post by cmwslw on 2009-04-20
Nevermind! The problem described in my post above was actually due to the $ScriptPath variable in my wiki that needed to be updated as a result of the new subdomain. Before it needed to be "/nxtpp" and now it just needs to be set at "". Well thanks guys for all the.. eh.. visiting pages. ;)

-Cory

---

### Post by Kareeser on 2009-04-21
Looks good! I was before the time of Mindstorm units, and I've outgrown Lego now, but it looks like a lot of fun!

---

