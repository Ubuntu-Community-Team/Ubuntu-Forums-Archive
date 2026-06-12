---
title: "Ubuntu as production server"
date: 2005-10-20
forum: Server Platforms
---

### Post by theQmaster on 2005-10-20
Hi,

I have ubuntu install and configured to handle http request, database is configured, apache2 running, mod_jk set - all is great.

How do I transform it in a production server ? Is there a boot option that allows to have only the needed daemons running ?

I know, I know, should have gotten the Debian but I didn't know and I don't want to waste the work I put on this machine.

My best,
theQMaster

---

### Post by LordHunter317 on 2005-10-20
[QUOTE=theQmaster]Hi,

I have ubuntu install and configured to handle http request, database is configured, apache2 running, mod_jk set - all is great.

How do I transform it in a production server ? Is there a boot option that allows to have only the needed daemons running ?

I know, I know, should have gotten the Debian but I didn't know and I don't want to waste the work I put on this machine.

My best,
theQMaster[/QUOTE]Well, tomcat has specific production configuration that needs to be setup.  Apache should be performance tuned: the default process/thread limits will be too low.  YOu'll need to gage memory allocation as well, especially ofr your DB.

As for disabling services, that's the sysadmin's job.  Use update-rc.d.

---

### Post by dbee on 2005-10-21
There's a cool little tutorial at 

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

on how to get started with an ubuntu server Qmaster. It's 5.10 which I reckon may even be a little bit more stable at this stage. It installs a headless server from base though, I'd suggest you do the same and just save any config files you've written and transfer them onto your new server. It goes through all the rc-updates and modifying your /etc/init.d

If you do want to install kde, or gnome though. I'd imagine that putting on webmin would be a good idea. You can find it with synaptic ...

Like LH said, you might want to modify your apache httpd.conf, or your mysql.conf depending on how busy you expect your server to get.  You'll have to google to find more info on that ...

---

### Post by LordHunter317 on 2005-10-21
I would hardly call such things optional, more like required.  Default values for both are too low to be sane for actual production.

---

### Post by theQmaster on 2005-10-21
[QUOTE=LordHunter317]I would hardly call such things optional, more like required.  Default values for both are too low to be sane for actual production.[/QUOTE]


So what values you'd recomend ?

---

