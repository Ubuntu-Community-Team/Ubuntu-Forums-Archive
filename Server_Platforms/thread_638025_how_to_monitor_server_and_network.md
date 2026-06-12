---
title: "how to monitor server and network?"
date: 2007-12-11
forum: Server Platforms
---

### Post by superman69 on 2007-12-11
Hi there

I am looking for software that will be able to monitor my servers, and service on the servers..mysql tcp/ip httpd etc.

I also want a mail sent if something goes down, I got a free app The Pinger but it's only pinging the servers and it doesn't work most of the time.

Please let me know if you have any ideas.

Thanks
Superman6

---

### Post by umattu on 2007-12-11
Have you tried Nagios?

[http://www.nagios.org/](http://www.nagios.org/)

I do not have personal experiance with this yet, but I have read it is pretty good.

---

### Post by rennen01 on 2007-12-11
Nagios combined ntop is an amazing combo.  Try them out!

---

### Post by stpr on 2007-12-12
I would also suggest Nagios, but it is a little confusing the installation. If you manage to install it correctly, you will be very pleased with the outcome.

---

### Post by HermanAB on 2007-12-12
I suggest using Zabbix.  Very easy to install. Just works: [http://www.zabbix.com/](http://www.zabbix.com/)

Cheers,

Herman

---

### Post by rennen01 on 2007-12-12
> **HermanAB said:**
> I suggest using Zabbix.  Very easy to install. Just works: [http://www.zabbix.com/](http://www.zabbix.com/)

Cheers,

Herman

I'm gonna try this out.  Thanks for the link.

---

### Post by superman69 on 2007-12-19
Hi there 

I got nagios running but how do I added more hosts to monitor?

Please let me know thanks

Superman69

---

### Post by techno-wiz on 2008-02-08
To add hosts you have to edit the windows.cfg file in the /usr/local/nagios/etc/objects directory.

---

### Post by gunbladeiv on 2008-02-10
snort + base anyone?
im using the piggy to monitor and give alert for any intrusion attemp or any unusual things on the network.  And the BASE will give the report through web browser.  So I can access it from anywhere and doesn't have to open port for other things.

may you should try this one out.. SNORT+BASE or maybe sguil?

---

### Post by viniciusfs on 2008-02-12
Nagios configuration files are terrible!

---

### Post by wirelessmonkey on 2008-02-12
> **viniciusfs said:**
> Nagios configuration files are terrible!

Use[ Groundworkopensource]("http://www.groundworkopensource.com") to manage them...

---

