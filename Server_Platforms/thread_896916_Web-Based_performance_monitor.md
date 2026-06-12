---
title: "Web-Based performance monitor"
date: 2008-08-21
forum: Server Platforms
---

### Post by heterosapien on 2008-08-21
Hi,

I was wondering if anyone could suggest a good application that I can use on Ubuntu Server 8.04 to monitor the performance of it through a web browser.  I only have the cli installed.

Thanks

---

### Post by wirelessmonkey on 2008-08-21
cacti may be good for you... it's in the repositories, or [www.cacti.net](www.cacti.net)

---

### Post by heterosapien on 2008-08-21
From what I can see, this only monitors the network traffic.  I am looking for something that monitors the cpu, hard drive, etc usage.

---

### Post by gishaust on 2008-08-21
what about  awstats

---

### Post by heterosapien on 2008-08-21
I installed one through apt-get called phpSysInfo but I do not know how to configure it.  If anyone else knows what the path would be to open it in a browser from another computer or how to configure it, please let me know.

---

### Post by erwall on 2008-08-21
> **heterosapien said:**
> I installed one through apt-get called phpSysInfo but I do not know how to configure it.  If anyone else knows what the path would be to open it in a browser from another computer or how to configure it, please let me know.
Mini howto:
```

sudo aptitude remove phpsysinfo
wget http://internap.dl.sourceforge.net/sourceforge/phpsysinfo/phpsysinfo-2.5.4.tar.gz
tar zxf phpsysinfo-2.5.4.tar.gz
mv phpsysinfo /var/www/
cd /var/www/phpsysinfo
mv config.php.new config.php
chown -R www-data. /var/www/phpsysinfo
```

Then pull up your browser and go to [http://yourserver/phpsysinfo](http://yourserver/phpsysinfo)

Also, I think you should give munin a shot, is just as easy to setup and gives you much more historical data.

```
sudo aptitude install munin munin-node
```

Then pull up your browser and go to [http://yourserver/munin](http://yourserver/munin)

Takes a while for stuff to start showing up in the graphs.

---

### Post by jure1873 on 2008-08-22
munin + monit
it's in the repositories

---

### Post by windependence on 2008-08-22
[http://www.nagios.org/](http://www.nagios.org/)

The defacto standard. I'm sure it's in the repositories as well.

-Tim

---

### Post by Viruk on 2008-08-22
I use cacti to monitor several Ubuntu servers and Windows servers and it works great, however I run cacti on its own machine. 

I have notes on how I set it up if you are in need of any help. 

I want to look into Nagios but I am under the impression that it is a bit more complicated to set up (but also more powerful) - I'm sure someone can correct me if I have that wrong. 

In terms of what you can monitor with cacti, I track the following types of information on Ubuntu boxes:
[LIST]
[*]Hard disk space (it shows used and available and can monitor different partitions on seperate graphs)
[*]Memory buffers
[*]RAM (Real Memory)
[*]Swap space (virtual memory)
[*]Logged in users
[*]Number of processes
[*]Network traffic (network card - you can monitor more than one if you have more)
[*]local traffic (loopback)
[*]CPU useage
[*]Load Average
[*]ping latency
[/LIST]

---

### Post by windependence on 2008-08-22
You are quite right, Nagios can be much harder to set up, but is feature rich (not that Cacti isn't). Fortunately there are many great tools and tutorials out there to help you.

-Tim

---

### Post by TurboRush on 2008-08-22
> **jure1873 said:**
> munin + monit
it's in the repositories

+1 for Munin.

---

### Post by heterosapien on 2008-08-22
Thanks erwall, helped a lot.  I am going to give cacti a shot now.

---

### Post by heterosapien on 2008-08-25
> **Viruk said:**
> I use cacti to monitor several Ubuntu servers and Windows servers and it works great, however I run cacti on its own machine. 

I have notes on how I set it up if you are in need of any help. 

I want to look into Nagios but I am under the impression that it is a bit more complicated to set up (but also more powerful) - I'm sure someone can correct me if I have that wrong. 

In terms of what you can monitor with cacti, I track the following types of information on Ubuntu boxes:
[LIST]
[*]Hard disk space (it shows used and available and can monitor different partitions on seperate graphs)
[*]Memory buffers
[*]RAM (Real Memory)
[*]Swap space (virtual memory)
[*]Logged in users
[*]Number of processes
[*]Network traffic (network card - you can monitor more than one if you have more)
[*]local traffic (loopback)
[*]CPU useage
[*]Load Average
[*]ping latency
[/LIST]

It would be great if you could give me some notes on how you configured cacti to work.

---

### Post by Viruk on 2008-08-27
> **heterosapien said:**
> It would be great if you could give me some notes on how you configured cacti to work.

I sent you a PM

---

