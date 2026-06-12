---
title: "Monitoring server and networked devices?"
date: 2010-10-14
forum: Server Platforms
---

### Post by SlugSlug on 2010-10-14
Hi All,

I am looking for some software that will sit on a central server that will monitor other servers (agents) and their devices over the internet.

The setup that needs monitoring is 100+ ubuntu servers scattered over the internet each server will need to monitor via ping (or something else)  the status or 4 networked devices and be in constant contact with a central server.

So I am aware of any devices that are down / power down / coms down/  etc..

Capability to monitor FTP (or lack of) would be a bonus

So I am after some advice from users with experience of such software please..

Thanks,

---

### Post by mbaas on 2010-10-14
Nagios sound right

---

### Post by piratebill on 2010-10-14
Check out "auto scan network".  it does everything you just described (it is a gui app....might be an issue)


[http://autoscan-network.com/](http://autoscan-network.com/)

---

### Post by arrrghhh on 2010-10-14
Oy, there's tons.  For deeper monitoring, Zenoss, Zabbix, Nagios to some extent.

There's a couple of suites (drawing a blank) that just do ping monitoring if that's your fancy.  NMIS is what we use currently, but I wouldn't recommend it TBH.

---

### Post by SlugSlug on 2010-10-15
Thanks all,

I will try Nagios next 

so far tried 
[OpenNMS]("http://www.osalt.com/opennms") ~ OK but will only monitor the one device doesn't  accross the net (can't find a way to tell it there are 5 devices on different ports)

AutoScan Network ~ pretty cool app but only really for internal networks

---

### Post by SlugSlug on 2010-10-15
Nagios seems great!

Do you guys know how to disable ping checks? I also have an issue with HTTP auth..

             ```
   check_command                   check_http!-a!user:pass 
```Does not seem to work..  how should it look?

---

### Post by SlugSlug on 2010-10-15
and it seems 

```
check_http!-p 81
```

is not working .. it still checks port 80

---

### Post by SlugSlug on 2010-10-15
never mind found out you do it through the /etc/nagios-plugins/config/  bit

---

### Post by SlugSlug on 2010-10-15
just wanted to add.

Nagios is Awesome!


:guitar::popcorn::guitar:

---

