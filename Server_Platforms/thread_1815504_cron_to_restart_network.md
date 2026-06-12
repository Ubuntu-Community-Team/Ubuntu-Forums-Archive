---
title: "cron to restart network"
date: 2011-07-31
forum: Server Platforms
---

### Post by lindevox on 2011-07-31
**_CRON TO RESTART NETWORK SERVICE_**

I'm setting up Ubuntu 11.04 SERVER on my SERVER:

Processor    : Intel core i3
Motherboard  : Gigabyte GA-H67N-USB3-B3
Memory       : 4 GB DDR3-1333 (Dual Channel)
Hard disk    : 1x 160 GB SATA (for the OS)
             : 3x 500 GB SATA ( RAID 10 )
USB WIFI     : TP-LINK TL-WN821N

The USB WIFI TP-LINK TL-WN821N disconnected after a few minutes.
dunno why this happened, it might be caused by the new feature or the motherboard that turn off the USB port for power saving reason and cause my USB WIFI to disconnect.

I have to restart the network every time it was disconnected by invoking :

```
invoke-rc.d/networking restart
``` 

My problem is how to automatically get the network restart  as a background process every xx minutes?

I've tried configuring Scheduled Cron Jobs from WEBMIN-1.550:

   Execute cron job as : root
   active?             : yes
   command             : invoke-rc.d networking restart  
   Input to command    : [LEAVE IT BLANK}
   Description         : restart network every 5 minutes

   checked the : Time and date selected below
   On minutes Column checked 2 minutes

In syslog I get this error:

CRON[1419]: (root) CMD (invoke-rc.d networking restart #restart network every 2 minutes)
CRON[1418]: (CRON) error (grandchild #1419 failed with exit status 127)
CRON[1418]: (CRON) info (no MTA installed, discarding output)

Pls Help!
TQ

---

### Post by Vishal Agarwal on 2011-08-02
Put the cron entry into the crontab in etc/crontab. To schedule it for any no of time duration ( Like for every five minutes call; */5 in minutes section) and closely observer the log files. you wil get the required result.

*/5 * * * * * root '/etc/init.d/networking restart'



I hope it will work. 

In any case Pl confirm the out come of my post.

---

### Post by kabeza on 2011-12-13
> **Vishal Agarwal said:**
> Put the cron entry into the crontab in etc/crontab. To schedule it for any no of time duration ( Like for every five minutes call; */5 in minutes section) and closely observer the log files. you wil get the required result.

*/5 * * * * * root '/etc/init.d/networking restart'



I hope it will work. 

In any case Pl confirm the out come of my post.


Sorry for bumping, but... by invoking this command through cron, won't it ask for password?

---

### Post by rubylaser on 2011-12-13
You'd just want to add it to your root crontab.
```
sudo -i
```
```
crontab -e
```

Then, add the line like this
```
*/5 * * * * * '/etc/init.d/networking restart'
```
No need for root, because root is executing it via cron.

---

### Post by kabeza on 2011-12-13
thanks. PS: how can I check if the cron job was executed successfuly? Does cron have any log I could see?
I've set it to run everyday at 0:00am

---

### Post by Lars Noodén on 2011-12-13
You can find the logs from [font=Courier New]cron[/font] in [font=Courier New]/var/log/syslog[/font]

```

grep CRON /var/log/syslog

```

---

### Post by lindevox on 2011-12-13
I've tried Vishal's suggestion. It did restart my usb wifi and the server was able to connect to wifi router (thank's Vishal), but after sometimes  ubuntu 10.10 server will fail to detect usb wifi. So I guess the problem is on the energy saver feature on mini-itx motherboard I use. It keeps turn off idle usb ports.

Last week, my Ubuntu 10.10 network down and I only can ping eth0 and wlan0, but they wasn't connected to any of my routers (I got 1 internal wifi router and 1 external wifi router connected to internet).

Finally I reinstall and upgrade to Ubuntu 11.10. everything was back to normal and seems that the "starting/restarting" wlan0 interface was fixed.
But, I need to run my system for a couple of weeks for the testing before I mark this thread as "SOLVED". 

TQ Guys.

---

### Post by kabeza on 2011-12-14
Hi
I checked the logs and saw the command wasn't run, but I guess it was because it was enclosed by single quote

> 0 0 * * * '/etc/init.d/networking restart'

Now, removed the quotes and seemed to work, but I get this message

**Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces**

---

### Post by Lars Noodén on 2011-12-14
> **kabeza said:**
> **Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces**

What is the new way of doing it?

---

