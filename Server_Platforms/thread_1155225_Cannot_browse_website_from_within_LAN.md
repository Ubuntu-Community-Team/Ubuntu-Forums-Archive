---
title: "Cannot browse website from within LAN"
date: 2009-05-10
forum: Server Platforms
---

### Post by GoodPanos on 2009-05-10
I setup LAMP from the repos and I have done this many times.  I set up WordPress sites and do work on them.  What I have never tried is to access these sites from another PC in the LAN.

So, I tried it:
```
<ip address>/sitename
```
And I get page not found. :shock:
If I just type the ip address I get the "It Works!" page.

Here is my hosts and httpd.conf files:
```
127.0.0.1 localhost
192.168.1.2 dev-pc

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

```
<VirtualHost *>
     ServerName localhost
     DocumentRoot /home/panos/www
</Virtualhost>
```

I haven't changed anything else.  Any advice is greatly appreciated.

---

### Post by GoodPanos on 2009-05-10
Figured this out.  :neutral:

Part of the issue was WordPress.  Actually it's a setting that I have always overlooked.  Here's how you fix it if you ever run into this.

By default when you install WordPress on a local PC/server it sets up the WordPress and Blog address to localhost/<site name>.  This setting can be found under Settings->General.

So, when you browse the site from another PC it redirects to the localhost address address and thus "page not found".  So, to correct this, change the Wordpress and Blog address to match the hostname or IP address of the PC/server you have the site running on.

Now, that's one piece of the puzzle.  You must also make your VirtualHost point to the address you set in WordPress.  Depending whether you want to use the hostname or IP address you would change your VirtualHost section in /etc/apache2/httpd.conf as follows:```
<VirtualHost *>
     ServerName <hostname> or <IP address>
     DocumentRoot /home/panos/www
</Virtualhost>
```

```
sudo /etc/init.d/apache2 restart
```
...and now you should be able to browse your site from within your LAN.

One catch with this whole setup is that you have to have a static IP address.  I'm still trying to figure out how to accomplish this with a dynamic address (see this [post]("http://ubuntuforums.org/showthread.php?t=1120190")).

---

