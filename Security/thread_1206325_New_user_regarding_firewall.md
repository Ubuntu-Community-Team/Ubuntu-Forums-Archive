---
title: "New user regarding firewall"
date: 2009-07-07
forum: Security
---

### Post by MonkeyMayhem on 2009-07-07
I have a couple of questions on the security of firewalls.  For years I've ignored my computer security.  I thought, I'm no one interesting, what kind of person would want to hack into my system.  Well it happened.  I ended up installing a firewall on a clean system.  The sad part is, it happened again even with my firewall active (windows xp obviously).  It happened years later, but now I'm trying desperately to lock out all potential hackers.

So now I'm on ubuntu trying to secure my home computer as much as possible.  My first question is how safe is my system when ufw configured to deny all incoming?  Is it secure enough?  With all these hacking techniques on ARP and DNS, is ufw enough?  

Secondly, which packet sniffers are secure to use?  Seems like each one I've looked at has some form of vulnerability.  Is it better not to use one?

---

### Post by lovinglinux on 2009-07-07
OMG, I was writing a big explanation, then Firefox froze and I have lost everything. So now I will reduce the explanation. Sorry.

If you have a router with firewalling capabilities you are already protected. Nevertheless, routers can also be exploited.

If you are not running any services, which means applications that can accept connections on a specific port (torrent client, web server, ssh server, remote desktop,  etc..), then you are pretty much protected, because incoming connections will be ignored. This is essentially the same as closing all your ports with a firewall.

If you are running a server, then you probably want to allow remote machines to connect to it. So using a firewall in this case is debatable, unless you want to limit the access to the server.

If you are running a server open to the web, then the risk is proportional to the security of your server application. It is only a threat if the application has exploitable flaws. So keep Ubuntu updated and use Apparmor if you want to be protected from zero day attacks.

That being said, I must admit I have a router, I use firewall rules to block everything and I use [moblock](http://moblock-deb.sourceforge.net/) fuill time. I just don't use Apparmor yet (need to learn). I guess is paranoia, acquired after 15 years using Windows :)

Gufw is just a firewall manager, which means it allows you to create rules for iptables (the real firewall) the easy way. Nevertheless, it is the recommended firewall manager these days and blocking incoming connections with it will do the job. But if you want full control of your firewall, then create the rules yourself.

I don't know much about packet sniffers, but it seems Wireshark is the most popular. I use  a simpler applications just to check current connections ([iptstate](apt:iptstate) [apt-get]).

I recommend that you read the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) and the [Intrusion Detection](http://ubuntuforums.org/showthread.php?t=919472) tutorials.

If you want to learn about iptables:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by MonkeyMayhem on 2009-07-07
I bought a router that doesn't have a firewall built in.  I also have default services running.  I'm not sure I should turn them off since I think I do depend on a couple.  What are my options now?

---

### Post by lovinglinux on 2009-07-07
> **MonkeyMayhem said:**
> I bought a router that doesn't have a firewall built in.  I also have default services running.  I'm not sure I should turn them off since I think I do depend on a couple.  What are my options now?

Don't turn them off and use the firewall for limiting access according to your needs. For example, you can only allow access to the services from IP addresses on your local network.

---

### Post by fela on 2009-07-07
I've been using Linux (Ubuntu) for the past 1.77 years without any form of software antivirus or firewall (apart from the router's firewall). I haven't got any kind of malware or anything like that (and I do click lots of...shall we say interesting stuff). But that's not to say that you definitely won't get hacked, just it's known to be unlikely due to Linux's inherent high security when compared to OSes such as NT, DOS and variants like OS/2 etc. Plus people don't tend to even write viruses for Linux, but we'll start getting more multi-OS viruses when the world becomes more and more web-based. Think javascript exploits.

So what I recommend is just Ubuntu with nothing more than the firefox noScript extension (that's my setup), you can even ommit the noscript if you don't think it's worth the hassle of clicking 'allow' for every single new java(script)/flash site.

You can always install a frontend for iptables (the best linux firewall), a good GNOME one is Firestarter and the KDE equivalent is Guarddog. Although they both limit your options and the best way of configuring iptables is through the commandline iptables interface.

If you are especially paranoid you can install a A/V such as Avast!, but I'd say this is a total waste of time.

---

### Post by MonkeyMayhem on 2009-07-07
Thanks.

---

