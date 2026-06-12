---
title: "website usage monitor"
date: 2012-03-13
forum: Server Platforms
---

### Post by jmr423 on 2012-03-13
Hey i am looking for some kind of program to monitor the usage of my web server. I want to be able to see the users connected to my website, usage history, page vists and bandwidth usage and so on. I would also like this information to be graphed and accessible and password protected on the website. I **_do not_** want to be able to change any of the configurations for the website with this program. I was looking around google but could not find anything. 

I am running a ubuntu 10.04 server with shore wall firewall, lamp server and ssh connects. Can anyone recommend anything?

---

### Post by Habitual on 2012-03-13
I'd like to suggest Zabbix for all your recent remote host data/detail requests...

---

### Post by jmr423 on 2012-03-13
> **Habitual said:**
> I'd like to suggest Zabbix for all your recent remote host data/detail requests...

Thanks, i'll download it right now.

---

### Post by AntiBodies on 2012-03-14
AWStats also very good for a basic solution.. easy to setup

[http://awstats.sourceforge.net/](http://awstats.sourceforge.net/)

---

### Post by Habitual on 2012-03-14
> **AntiBodies said:**
> AWStats also very good for a basic solution.. easy to setup

[http://awstats.sourceforge.net/](http://awstats.sourceforge.net/)

+1 b/c Zabbix is NOT an OOTB-"ready"...

---

### Post by jmr423 on 2012-03-14
v> **Habitual said:**
> +1 b/c Zabbix is NOT an OOTB-"ready"...

Zabbix does not want to work with my php timezone feature so i gave up on it and started using AWStats.

---

