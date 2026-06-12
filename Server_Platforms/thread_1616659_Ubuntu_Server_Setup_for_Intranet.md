---
title: "Ubuntu Server Setup for Intranet"
date: 2010-11-08
forum: Server Platforms
---

### Post by bbl on 2010-11-08
I work in a place where entire network is in windows domain. I am thinking to install one Ubuntu server for testing purpose basically a LAMP server with SSH. So, far I manged to install a server and access its pages by IP address. However I am trying to access its page by name like [http://intranet](http://intranet) not [http://100.xx.xx.xx](http://100.xx.xx.xx). Now the problem is network administrator often changes  the IP of every computer. So, is there any way to achieve this via DHCP or anything else. So, that whenever I go to [http://intranet](http://intranet) it will route the traffic to this server.

---

### Post by SeijiSensei on 2010-11-08
Best solution: Get the network administrator to agree to let you assign a static IP address to the server and have her create an A and a PTR record in the Windows DNS server for your server's hostname and IP pairing.

If that's not possible, is it the case that your server will get a well-defined hostname from Windows DHCP?  Open a Terminal on the Linux box, and first enter "ifconfig" to see what IP address you have been assigned.  (It's probably going to be the one assigned to eth0.)  Next, enter the command "host -t ptr enter.your.ip.here" and see what hostname it returns.  If that hostname remains static even though the IP changes, you can use that name in URLs.

If your hostname changes each time the IP changes, there's little you can do other than my first suggestion.

---

### Post by bbl on 2010-11-09
> **SeijiSensei said:**
> Best solution: Get the network administrator to agree to let you assign a static IP address to the server and have her create an A and a PTR record in the Windows DNS server for your server's hostname and IP pairing.

If that's not possible, is it the case that your server will get a well-defined hostname from Windows DHCP?  Open a Terminal on the Linux box, and first enter &quot;ifconfig&quot; to see what IP address you have been assigned.  (It's probably going to be the one assigned to eth0.)  Next, enter the command &quot;host -t ptr enter.your.ip.here&quot; and see what hostname it returns.  If that hostname remains static even though the IP changes, you can use that name in URLs.

If your hostname changes each time the IP changes, there's little you can do other than my first suggestion.

 thanks for reply   ok now i have a static ip , how can i access its page by name ([http://intranet](http://intranet) ) from another computer

---

### Post by s1nch4n on 2010-11-10
> **bbl said:**
> thanks for reply   ok now i have a static ip , how can i access its page by name ([http://intranet](http://intranet) ) from another computeryou should read more read carefully ...

> **SeijiSensei said:**
> Best solution: **Get the network administrator to agree to let you assign a static IP address to the server and have her create an A and a PTR record in the Windows DNS server for your server's hostname and IP pairing.**

If that's not possible, is it the case that your server will get a well-defined hostname from Windows DHCP?  Open a Terminal on the Linux box, and first enter "ifconfig" to see what IP address you have been assigned.  (It's probably going to be the one assigned to eth0.)  Next, enter the command "host -t ptr enter.your.ip.here" and see what hostname it returns.  If that hostname remains static even though the IP changes, you can use that name in URLs.

If your hostname changes each time the IP changes, there's little you can do other than my first suggestion.

---

### Post by broadview on 2010-11-10
hi hw r u ? have a nice day.

---

### Post by bbl on 2010-11-10
> **s1nch4n said:**
> you should read more read carefully ...

sorry bro , thanks for help

---

