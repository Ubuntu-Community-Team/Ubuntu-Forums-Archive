---
title: "Script for monitoring system performance"
date: 2009-06-09
forum: Server Platforms
---

### Post by Poma on 2009-06-09
I want to make web interface to monitor my system resources. I've already made some long-term graphs using Collectd&Rrdtool but I also want to make some light-weight page with my current resources. What I want to do is to make shell(or perl) script that will collect system information and update web page every 10 seconds. Now I need some template script that collects all common performance data, such as CPU/memory/disk/network usage.

---

### Post by LepeKaname on 2009-06-09
Why not using munin? it does everything you need, and it is very easy to setup.

---

### Post by Poma on 2009-06-11
I need only current information but munin designed to write statistics to rrd logs. Do you know how to make munin or collectd to output current statistics to stdout?
Also one guy told me that sysstat package is a good thing. How about this one? Will it do the trick?

---

### Post by v3xtra on 2009-06-11
[http://ubuntuforums.org/showthread.php?t=1075599&highlight=home+server&page=2](http://ubuntuforums.org/showthread.php?t=1075599&highlight=home+server&page=2)

Check post #13.  I think this may be what you are looking for, as it is a PHP script that gets information about memory and CPU usage, and puts it in a web page for easy access.  You could easily add a meta-refresh to update the page every 10 seconds like you are wanting.  Hope that helps!

---

### Post by LepeKaname on 2009-06-12
Also you can use gkrellm (as server) to monitor in realtime a server activity from a X11 client. Very easy to setup.

---

### Post by Poma on 2009-06-12
> **v3xtra said:**
> [http://ubuntuforums.org/showthread.php?t=1075599&highlight=home+server&page=2](http://ubuntuforums.org/showthread.php?t=1075599&highlight=home+server&page=2)

Check post #13.  I think this may be what you are looking for, as it is a PHP script that gets information about memory and CPU usage, and puts it in a web page for easy access.  You could easily add a meta-refresh to update the page every 10 seconds like you are wanting.  Hope that helps!


That was good one! :)

---

### Post by Poma on 2009-06-12
> **LepeKaname said:**
> Also you can use gkrellm (as server) to monitor in realtime a server activity from a X11 client. Very easy to setup.

I don't have X Server

---

### Post by LepeKaname on 2009-06-13
At your server you don't need X server. Gkrellm can run as daemon (without interface). If you use any other computer with X, then you can see in realtime the server information (CPU, Memory, HDD, Network, etc.) in your client.

---

