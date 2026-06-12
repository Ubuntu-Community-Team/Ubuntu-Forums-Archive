---
title: "Installing the server for 8.04.03"
date: 2009-09-07
forum: Server Platforms
---

### Post by bigoxygen on 2009-09-07
Hi

I am following the guide from **[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)**

I don't understand a part of it (I have bolded some part of it):

Now you need to restart your network services using the following command

sudo /etc/init.d/networking restart

You need to **setup manually** DNS servers in resolv.conf file when you are not using DHCP.

sudo vi /etc/resolv.conf

You need to add look something like this
[B]
search domain.com

nameserver xxx.xxx.xxx.xxx[/B]


Thanks:popcorn:

---

### Post by Cardale on 2009-09-07
Are you using this for a production server?

---

