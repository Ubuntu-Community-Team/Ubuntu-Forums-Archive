---
title: "how to make a script run at startup"
date: 2009-09-10
forum: Server Platforms
---

### Post by joeinbend on 2009-09-10
Ubuntu Server 9.04

Hi all, I have a script that I run to communicate with a piece of USB hardware, and it works correctly when I run it from the command line (sudo ./phidgetwebservice21) however what I really need is to have it just run that script in the background at startup, so I dont have to see it running or do any manual intervention. I'm sure this is very straightforward but I just have no experience in that field. Can someone give me a play-by-play on how to make this work?

thanks!!

---

### Post by pilp4 on 2009-09-10
System > Prefrences > Startup Applications. Hope that helps.

---

### Post by MrWES on 2009-09-10
> **pilp4 said:**
> System > Prefrences > Startup Applications. Hope that helps.

Uh? I'll give ya $1,000 if you can show me where that is on a server install...duh!

@pilp4; you can add your script name to the /etc/rc.local or put it in a crontab as:

@reboot bashscript.sh

```
@reboot /usr/bin/screen -dmS rtorrent /usr/local/bin/rtorrent

```

Bill

---

### Post by lensman3 on 2009-09-11
If you have a  script called "/etc/rc.d/rc.local", then add the script to this file.  This script is run as one of the last things on boot.

I have added to my gateway firewall:

/sbin/ifconfig eth1 txqueuelen 100
/sbin/ifconfig eth0 txqueuelen 100

these lines.  They set the queue length for my Ethernet stacks to 100 packets, so that response is faster.  All this machine does is do firewall "stuff".  It ususally doesn't even break a sweat at 5 percent utilization. 

The only problem about adding stuff to this file is you have to remember to do it again when you upgrade.

Hope this helps.

---

### Post by joeinbend on 2009-09-11
Thanks for all the helpful tips, I'm getting close! I added the following line to my /etc/rc.local:

/usr/lib/phidgetwebservice21

..and left the "exit 0" line below it (the only un-commented line in the file before I added the line mentioned above.

I restarted the server, and sure enough the service works! after about an hour or so, it stopped working again. I check the running processes via my "htop", and it's still there, and when I try to re-run the command manually from the console it tells me it's still running. Did I boff something?

---

### Post by joeinbend on 2009-10-03
Hi all, the above addition to my /etc/rc.local got what I needed, but I find that sometimes the service crashes, and I dont know how to invoke a restart. I'm used to command-line things where for this example I would have the "sudo /etc/init.d/phidgetwebservice21 status|start|stop|restart" commands available to me. Can I get an outline of how I might set my module up to do behave this way?

---

### Post by joeinbend on 2009-12-04
::bump::

---

### Post by munky99999 on 2009-12-04
The occasional problem I've found with doing it in rc.local is basically the script runs ever so slightly too soon. For example scripts to add network shares; they tend to end up running before you can get your network connection up.

So you simply put in there

sleep "n seconds" then the command.

replace quotations with a #

---

