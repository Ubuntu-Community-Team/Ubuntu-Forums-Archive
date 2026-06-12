---
title: "Issues Creating Virtual Hosts: Ubuntu Linux 11.04"
date: 2012-06-05
forum: Server Platforms
---

### Post by nowashburn on 2012-06-05
I was having an issue creating virtual hosts where no matter how many virtual hosts I created, every domain still only displayed one of the virtual hosts, which was the first one I created. Note that it wasn't displaying var/www but rather /var/www/vhosts/firstvirtualhost.com. So i assume that it was somehow recognizing that there were virtual hosts in a sense.

After some tooling around and some trial and error I couldn't correct the problem so I decided to take a look at another server setup that I had up and running and compare the two. The server that was working correctly had the following in /etc/apache2/ports.conf:

NameVirtualHost *:80
NameVirtualHost xxx.xx.xx.xxx
Listen 80
Listen xxx.xx.xx.xxx

As opposed to the non working server:

NameVirtualHost *:80
Listen 80

I copied the config form the working server, updated the ip address, restarted apace, and it's now working :)

As it is probably obvious, I am fairly new at this and would like to know what exactly this changed to get things working correctly and also if this is even the correct way to setup virtual hosts. Thanks in advance for any insightful input!

---

### Post by volkswagner on 2012-06-05
It is likely you have specified an ip address at the head of you vhost file.

The heading of your vhost ie: <VirtualHost *:80> needs to have a matching entry in ports.conf.

Possible headings could be:
<VirtualHost *:80>
<VirtualHost *>
<VirtualHost 192.168.1.1:80>
<VirtualHost 192.168.1.1>

I hope this clears things a little.

---

### Post by nowashburn on 2012-06-05
> **volkswagner said:**
> It is likely you have specified an ip address at the head of you vhost file.

The heading of your vhost ie: <VirtualHost *:80> needs to have a matching entry in ports.conf.

Possible headings could be:
<VirtualHost *:80>
<VirtualHost *>
<VirtualHost 192.168.1.1:80>
<VirtualHost 192.168.1.1>

I hope this clears things a little.

That would make sence and thanks for your suggestion, but I don't think this is the case. I have three virtual host conf files:

/etc/apache2/sites-available/default:
<VirtualHost *:80>

/etc/apache2/sites-available/virtualhost1.com.conf
<VirtualHost virtualhost1.com>

/etc/apache2/sites-available/virtualhost2.com.conf
<VirtualHost virtualhost2.com>

:/

---

### Post by CharlesA on 2012-06-05
It looks like you didn't set up your virtual hosts correctly.

See here:

[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

---

### Post by nowashburn on 2012-06-06
> **CharlesA said:**
> It looks like you didn't set up your virtual hosts correctly.

See here:

[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

Thanks for the tutorial. After reading it through though I don't see where I have anything setup wrongly. The virtual hosts only seem to work if I add the ip address of the server to ports.conf ex: NameVirtualHost xx.xx.xx.xxx . Again, I'm not sure if this is the correct way of doing things though.

---

### Post by volkswagner on 2012-06-06
> **nowashburn said:**
> Thanks for the tutorial. After reading it through though I don't see where I have anything setup wrongly. The virtual hosts only seem to work if I add the ip address of the server to ports.conf ex: NameVirtualHost xx.xx.xx.xxx . Again, I'm not sure if this is the correct way of doing things though.


The following is not proper syntax:
```
<VirtualHost virtualhost1.com>
```

My best guess this works for you after changing ports.conf because you likely have dns entry or /etc/hosts which match your virtualhost1.com to an actual ip address.

It is best to stick with Apache2's recommended routine of using:
```
<VirtualHost *>
<VirtualHost *:80>
<VirtualHost xxx.xxx.xxx.xxx>
<VirtualHost xxx.xxx.xxx.xxx:80>
```

You will then use ServerName directive to use domain name scheme.
```
ServerName virtualhost1.com
```

---

### Post by nowashburn on 2012-06-06
> **volkswagner said:**
> The following is not proper syntax:
```
<VirtualHost virtualhost1.com>
```

My best guess this works for you after changing ports.conf because you likely have dns entry or /etc/hosts which match your virtualhost1.com to an actual ip address.

It is best to stick with Apache2's recommended routine of using:
```
<VirtualHost *>
<VirtualHost *:80>
<VirtualHost xxx.xxx.xxx.xxx>
<VirtualHost xxx.xxx.xxx.xxx:80>
```

You will then use ServerName directive to use domain name scheme.
```
ServerName virtualhost1.com
```

I'm really unsure what I could be doing wrong at this point then. If I dont use the syntax
```
<VirtualHost virtualhost1.com>
```

The virtual hosts do not work at all and yes, there is an entry in etc/hosts for the servers ip address. Thanks for your help as I am still pretty new at setting all this up.

---

### Post by rubylaser on 2012-06-06
What he meant is your vhost entry needs to start with a routing line, then the server name.  Here's a barebones example of a vhost file.

```
<VirtualHost *:80>
  ServerName virtualhost1.com
  DocumentRoot /var/www/virtualhost1.com
</VirtualHost>
```

This would redirect all requests to the virtualhost1.com URL on port 80 (http) to the /var/www/virtualhost1.com folder.  I hope that makes it a little clearer.

---

### Post by nowashburn on 2012-06-06
Thanks everyone for your help! The following two suggestions fixed my issues:

> **volkswagner said:**
> 
My best guess this works for you after changing ports.conf because you likely have dns entry or /etc/hosts which match your virtualhost1.com to an actual ip address.


I removed the dns entry for the ip server's main ip address. If it's not supposed to be there in the first place, I honestly don't know how it got there at all.

> **CharlesA said:**
> 
It looks like you didn't set up your virtual hosts correctly.
See here:
[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)


After reading a little more closely, I added NameVirtualHost * and ServerName incorrect.com to the /etc/apache2/sites-available/default file.

Thanks again! :)

---

### Post by CharlesA on 2012-06-06
> **rubylaser said:**
> What he meant is your vhost entry needs to start with a routing line, then the server name.  Here's a barebones example of a vhost file.

```
<VirtualHost *:80>
  ServerName virtualhost1.com
  DocumentRoot /var/www/virtualhost1.com
</VirtualHost>
```

This would redirect all requests to the virtualhost1.com URL on port 80 (http) to the /var/www/virtualhost1.com folder.  I hope that makes it a little clearer.

+1

> **nowashburn said:**
> Thanks everyone for your help! The following two suggestions fixed my issues:



I removed the dns entry for the ip server's main ip address. If it's not supposed to be there in the first place, I honestly don't know how it got there at all.



After reading a little more closely, I added NameVirtualHost * and ServerName incorrect.com to the /etc/apache2/sites-available/default file.

Thanks again! :)

That really isn't the "proper" way to do it, even if it works.

See here: [http://ubuntuforums.org/showthread.php?t=1977192](http://ubuntuforums.org/showthread.php?t=1977192)

---

### Post by nowashburn on 2012-06-06
> **CharlesA said:**
> +1



That really isn't the "proper" way to do it, even if it works.

See here: [http://ubuntuforums.org/showthread.php?t=1977192](http://ubuntuforums.org/showthread.php?t=1977192)

What specifically about it isn't "proper" ?

---

### Post by CharlesA on 2012-06-06
> **nowashburn said:**
> What specifically about it isn't "proper" ?
If you are running multiple virtual hosts, it is easier to manage by using a separate site for each.

If you are only running one - using the default site would work, but it can get messy/unorganized if you add more sites.

---

### Post by nowashburn on 2012-06-06
> **CharlesA said:**
> If you are running multiple virtual hosts, it is easier to manage by using a separate site for each.

If you are only running one - using the default site would work, but it can get messy/unorganized if you add more sites.

I believe that is what I am actually doing now? Sorry if I wasn't full clear on how it is setup now:


apache2/ports.conf:

NameVirtualHost *:80
Listen 80

(no more ip address listed)

__________________________

sites-available/default:

NameVirtualHost *
<VirtualHost *>

__________________________

sites-available/virtualhost1.com:

<VirtualHost *:80>
ServerName virtualhost1.com

__________________________

sites-available/virtualhost2.com:

<VirtualHost *:80>
ServerName virtualhost2.com

---

### Post by CharlesA on 2012-06-06
That looks right.

---

