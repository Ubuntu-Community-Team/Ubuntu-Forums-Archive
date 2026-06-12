---
title: "Ubuntu Sever 10.04 and mumble server web interface"
date: 2010-04-30
forum: Server Platforms
---

### Post by quimkaos on 2010-04-30
first of all i installed successful Ubuntu Sever 10.04 LTS with LAMP and SAMBA. with no problems at all and configured my shares on samba and one additional virtual host in Apache 2.

After that I installed mumble (former murmur)  with no problem and configured and tested it by using a Ubuntu/windows box. After I installed mumble-server-web package so I could get extra functionality by using the web interface. apparently everything works OK but now Apache seams to be not working. I can't connect to any page even locally: using lynx localhost will give me the error unavailable page...

to revert i had to do:
sudo apt-get remove mumble-server-web

but this still leaves Apache not running correctly, which can only be resolved by doing:
sudo apt-get autoremove

which will remove extra packages that mumble-server-web installed. 

this leaves me at the beginning: how to install the web interface for mumble server?

any suggestions?

Sory for any miss spelling

---

### Post by skeppstedt on 2010-05-10
Hi,

I hade the same problem after installing the mumble web interface.

Take a look at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=573699]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=573699"), that solved the problem for me.

Short story:

Open /etc/php5/conf.d/MurmurPHP.ini and replace its content with this line:

```
ice.slice=-I/usr/share/Ice/slice /usr/share/slice/Murmur.ice /usr/share/Ice/slice/Glacier2/Router.ice
```

---

