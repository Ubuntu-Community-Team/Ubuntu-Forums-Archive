---
title: "Can't change my apache2 listening port"
date: 2009-11-19
forum: Server Platforms
---

### Post by poundcomma on 2009-11-19
Hi. I'm a brand new noob (my first Linux install, via Ubuntu Server 9.10, happened yesterday), so please bear with me. 

My ISP blocks port 80, and I'm trying to set up a development environment that can be accessed from outside of my network. From what I've read, I should just be able to add port 78 to /etc/apache2/ports.conf and restart apache (plus some DNS changes outside the scope of this topic), but so far that's not working. 

When I try to pull up my IP and new port (192.168.1.200:78) on the browser on a different machine on the network, I get a "Cannot find server" error. When I pull up just 192.168.1.200, I get an index of my /var/www folder, as expected.

What am I missing? Any ideas?

Here are the contents of my /etc/apache2/ports.conf file (you can see where I was testing with the full IP - that didn't work either):

```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80
Listen 78
#Listen 192.168.1.200:80
#Listen 192.168.1.200:78

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```

---

### Post by poundcomma on 2009-11-19
Not 5 minutes later I figured this out on my own. Should've read the comment at the top of that file. I added a new record for Virtual port 78 and we're all set.

---

### Post by spikyjt on 2009-11-19
Well done for getting stuck in and fixing it yourself. And for reporting back that you succeeded. This thread might just help someone in the future with the same problem.

Another option is to leave your server on the default port 80 and port forward another port from your router to port 80 on your server - if that works in your network setup. Also 8080 is a more common alternative port for http

---

