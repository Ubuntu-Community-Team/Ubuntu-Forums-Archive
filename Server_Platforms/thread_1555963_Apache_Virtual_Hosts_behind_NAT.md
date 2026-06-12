---
title: "Apache Virtual Hosts behind NAT"
date: 2010-08-18
forum: Server Platforms
---

### Post by MakOwner on 2010-08-18
I'm wondering if this is even possible before I start the learning curve with Ubuntu and apache virtual hosts.

I have a static external IP address that resolves to the various domain names I will be using.  I have a web server inside my network with a private IP address and any http request to the firewall is forwarded to the webserver on the appropriate port.  This setup works well when using the same web page/configuration for all of the domains.

Will it be possible to use named virtual hosts in this configuration, or will the NAT'ing interfere?

---

### Post by Bachstelze on 2010-08-18
Nope, the NAT doesn't matter, name-based virtual hosts will work fine.

---

### Post by MakOwner on 2010-08-18
> **Bachstelze said:**
> Nope, the NAT doesn't matter, name-based virtual hosts will work fine.

Thanks -- is there a tutorial for using virtual hosts with Ubuntu?  Or at least some Ubuntu specific documentation?  Everything about it I find on the web doesn't correspond to the configuration files I find in the Ubuntu install.


It's very confusing so far.

For example:

Following the apache2 docs at [http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)

> 
For example, suppose that you are serving the domain [www.domain.tld](www.domain.tld) and you wish to add the virtual host [www.otherdomain.tld](www.otherdomain.tld), which points at the same IP address. Then you simply add the following to httpd.conf:


But there is no httpd.conf file in Ubuntu.
Why is it better to use a non-standard configuration setup?

Would these changes go in /etc/apache2/apache2.conf or in separate files in /etc/apache2/sites-available?
Putting them in files in /etc/apache2/sites-available isn't working for me...

---

### Post by Bachstelze on 2010-08-18
After you create your file in sites-available, you need to do

```
sudo a2ensite <site_name>
```

and reload the apache config.

---

### Post by MakOwner on 2010-08-18
> **Bachstelze said:**
> After you create your file in sites-available, you need to do

```
sudo a2ensite <site_name>
```

and reload the apache config.

Does do anything more than create the link from sites-available/ to sites-enabled?

---

### Post by Bachstelze on 2010-08-19
> **MakOwner said:**
> Does do anything more than create the link from sites-available/ to sites-enabled?

According to the man page, that's all it does.  I can't tell for sure, though, it's in Perl, which I'm not very familiar with.

---

### Post by MakOwner on 2010-08-19
> **Bachstelze said:**
> According to the man page, that's all it does.  I can't tell for sure, though, it's in Perl, which I'm not very familiar with.


That's all it does near as I can tell, too.
Manually creating the links has the same results, near as I can tell.

---

### Post by MakOwner on 2010-08-19
I can't figure out how to change the status of this thread to solved, could a moderator update this please?

I (roughly) followed this process [http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting](http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting) (I'm not associated with them, just found them via google...) and set up virtual hosts in /etc/apache2/sites-available 

I then added hosts entries in my DNS server inside the NAT's LAN for the various named servers to resolve all to the same IP.

External requests for the names servers through the NAT appliance (IPCop) returns the appropriate content.

---

### Post by arrrghhh on 2010-08-19
> **MakOwner said:**
> I can't figure out how to change the status of this thread to solved

Glad it's sorted for ya.  It's under the "Thread Tools" drop-down menu at the top of the page ;)

---

### Post by MakOwner on 2010-08-19
> **arrrghhh said:**
> Glad it's sorted for ya.  It's under the "Thread Tools" drop-down menu at the top of the page ;)

Thanks!
Learn something new every day.

---

