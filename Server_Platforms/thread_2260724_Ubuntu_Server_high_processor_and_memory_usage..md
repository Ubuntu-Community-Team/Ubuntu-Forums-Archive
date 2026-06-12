---
title: "Ubuntu Server high processor and memory usage."
date: 2015-01-14
forum: Server Platforms
---

### Post by karlo on 2015-01-14
Hi,

A friend of mine is having issues with his Ubuntu server. He is wondering about the high processor usage. I don't know about the memory though. Plus, he's using Plesk. When I checked his Control Panel, I don't see any installations of Wordpress or any other applications. So, the entire LAMP stack might have been installed manually via SSH. I will be attaching some of the screenshots.

I have no idea how to optimize it.

[[IMG]http://i.imgur.com/0UOZ4Zlt.png[/IMG]]("http://imgur.com/0UOZ4Zl")
[[IMG]http://i.imgur.com/JObnk88t.png[/IMG]]("http://imgur.com/JObnk88")
[[IMG]http://i.imgur.com/A9EqSnct.png[/IMG]]("http://imgur.com/A9EqSnc")
[[IMG]http://i.imgur.com/K2nVNVTt.png[/IMG]]("http://imgur.com/K2nVNVT")

Another thing, I am planning to implement Cloudflare. But, I don't know if I have to manually change all of the settings of the domains or I will just install the Cloudflare application in Plesk.

Thanks.

---

### Post by TheFu on 2015-01-14
10.04 is loosing support in a few months. The time to migrate is now.
[http://blog.ircmaxell.com/2014/12/php-install-statistics.html](http://blog.ircmaxell.com/2014/12/php-install-statistics.html) - perhaps his server is hacked and is a bot controller today?  We all see the fishing emails that point back to some php server on the internet. Could that be it?

---

### Post by karlo on 2015-01-14
> **TheFu said:**
> 10.04 is loosing support in a few months. The time to migrate is now.
[http://blog.ircmaxell.com/2014/12/php-install-statistics.html](http://blog.ircmaxell.com/2014/12/php-install-statistics.html) - perhaps his server is hacked and is a bot controller today?  We all see the fishing emails that point back to some php server on the internet. Could that be it?
Please help me, how can I repair it?

---

### Post by TheFu on 2015-01-14
> **karlo said:**
> Please help me, how can I repair it?

What have you tried already?
[http://ubuntuforums.org/showthread.php?t=2235645&highlight=hacked+lamp+server](http://ubuntuforums.org/showthread.php?t=2235645&highlight=hacked+lamp+server)

---

### Post by karlo on 2015-01-14
> **TheFu said:**
> What have you tried already?
[http://ubuntuforums.org/showthread.php?t=2235645&highlight=hacked+lamp+server](http://ubuntuforums.org/showthread.php?t=2235645&highlight=hacked+lamp+server)

I was thinking of doing these first:

[http://serverfault.com/questions/321938/one-php5-cgi-process-uses-100-cpu](http://serverfault.com/questions/321938/one-php5-cgi-process-uses-100-cpu)
[http://serverfault.com/questions/590556/ubuntu-running-apache-server-prefork-php-fast-cgi-high-cpu-usage](http://serverfault.com/questions/590556/ubuntu-running-apache-server-prefork-php-fast-cgi-high-cpu-usage)

then use "apt-get update; apt-get dist-upgrade; apt-get upgrade", then probably upgrade the version of Ubuntu to the latest LTS version. Although, I don't know how to upgrade the distro itself.

---

### Post by TheFu on 2015-01-14
Either upgrade or dist-upgrade is needed - not both. Look up the differences if you care. I do dist-upgrade on every system here, every Saturday morning.

The first link doesn't seem related at all. 
Can't say anything else ... since you haven't shared any information about what is running on the box or any other facts, architecture, page loads, workload. 

Usually, I'd suggest getting monitoring going, otherwise we are just guessing.  Facts are necessary to make informed choices. I don't have many facts right now.

---

### Post by karlo on 2015-01-14
> **TheFu said:**
> Either upgrade or dist-upgrade is needed - not both. Look up the differences if you care. I do dist-upgrade on every system here, every Saturday morning.

The first link doesn't seem related at all. 
Can't say anything else ... since you haven't shared any information about what is running on the box or any other facts, architecture, page loads, workload. 

Usually, I'd suggest getting monitoring going, otherwise we are just guessing.  Facts are necessary to make informed choices. I don't have many facts right now.

Here are the technical specifications of the server: [http://www.serverloft.eu/rootservers/rootservers-compare.php?server=RootServer-L](http://www.serverloft.eu/rootservers/rootservers-compare.php?server=RootServer-L)

There are more than 15,000 visitors to the website everyday. Actually, more than that.

---

### Post by TheFu on 2015-01-15
Really need to know what is running on the system though the specs are helpful. Java stuff behaves much differently from Ruby or php or perl or python or some custom code that only the developers know.

Also, having performance data.charts from the last 6 months would be good too. Seeing the change in performance (the date) might click something in your mind for what changed on that date.

---

### Post by mastablasta on 2015-01-16
wait this is a hosted server? can you actually upgrade the OS on those servers? 
Also are you saying the server never received any updates? not even security ones?

Also if you can control the server fully then make sure to setup automated updates at least.

---

