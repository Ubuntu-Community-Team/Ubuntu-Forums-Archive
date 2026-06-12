---
title: "how to make a server in ubuntu?"
date: 2007-06-03
forum: Server Platforms
---

### Post by InfectedJ11 on 2007-06-03
hi everyone I just install a fresh copy of Ubuntu 7.04 and I would like to run a web server or a server anyways can someone explain to me how to install a server + some security tips on how to install firewalls and iptables things like that I also would like to install a server that would run apache+sql+php+perl+html.

I would like to know how to make a nice level of security for a web server. thank you !!

---

### Post by etcpool on 2007-06-03
in the easy way 

u should take a look at aritcles & howtos at [http://www.howtoforge.com](http://www.howtoforge.com)


there're serveral howtos for linux server including ubuntu there.

---

### Post by statictonic on 2007-06-03
> **InfectedJ11 said:**
> hi everyone I just install a fresh copy of Ubuntu 7.04 and I would like to run a web server or a server anyways can someone explain to me how to install a server + some security tips on how to install firewalls and iptables things like that I also would like to install a server that would run apache+sql+php+perl+html.

I would like to know how to make a nice level of security for a web server. thank you !!

Did you install Ubuntu Desktop or Ubuntu Server?  If you did a clean install of Desktop I would recommend that you just redo the install using server, since that will have apache, mysql and php all set to go for you.

/var/www is the default directory for websites on there, by default php should work fine and mysql will be up and running.  What specifically did you want setup with iptables?  What is this server bering used for?  Do you need DNS or DHCP on the server?

---

