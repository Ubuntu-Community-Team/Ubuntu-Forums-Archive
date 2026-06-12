---
title: "Apache Optimization for home use."
date: 2013-01-16
forum: Server Platforms
---

### Post by brent1975 on 2013-01-16
Hello, I curently running ubuntu 12.04 at home and have Apache, mysql samba and a few other things running.  What I am wanting to know is being my sites are not high traffic sites is there any type of optimizations that I could do to tweek apache use less of resources. I don't want it to be slow but at the same time if I can free up resources that are not necessary for a basic home site why not. I have read alot of different threads from google and I just wanted to ask here perhaps an apache expert would have some advice.

Take in mind my server is working proper I am just wanting to tune up a little is all.

Any information would be grateful. 

Thanks in advance.

---

### Post by SeijiSensei on 2013-01-17
> **brent1975 said:**
> is there any type of optimizations that I could do to tweek apache use less of resources.

I wouldn't bother myself.  The default settings are not especially resource intensive, and Apache itself is pretty efficiently coded.  It's been around for nearly two decades now.

---

### Post by tgalati4 on 2013-01-17
What resources do you want to free up?  RAM, CPU utilization?  Electrical power?  To me the last one is most important because your power bill (running 24/7) will exceed the cost of hardware in a few years.

You can run Apache on a desktop machine and not even know it's running.  It's only when your site gets slammed with traffic that you have a problem and chances are your internet connection is the bottleneck, not CPU power to answer http requests.

If you are low on RAM, add more RAM to the system.  Any apache tweaks will simply offload the performance to something less desireable like swap.  There are "light" servers such as:

lighttpd - A fast webserver with minimal memory footprint

But they may not run all of the web services that you want.  Can lighttpd run Drupal7? I don't think so.

Most tweaking of Apache has to do with maximizing http requests per second, and that assumes maximum bandwidth to the internet--which you do not have.  Otherwise you would not be asking this question.

You can install apache plug-ins like fastcgi and other "precompiled" modules that help serve requests faster, but for a home site, you may not notice the difference, because the traffic is so low.

The biggest performance gain is to avoid crappy, desktop processors like the Celeron.  Stick with business-grade Xeon processors and you won't care about performance tweaking anymore.

---

### Post by Warren Hill on 2013-01-17
I have a small Apache server with MySQL, PHP, etc. at home.  To be honest with low traffic I can't see any difference in performance on the machine whether its running and being accessed by the other 4 computers in the house and if I stop it.

So I agree with the other posters its not worth the effort.  If this computer was being accessed continually by the rest of the world it may be a different issue though I suspect my 8 Meg broadband would probably be the bottleneck and not my computer.

I am actually considering moving this to a Raspberry Pi but only so I don't have to run a desktop 24/7: Not to improve either Web server performance or to speed up the desktop PC.

---

### Post by sandyd on 2013-01-17
You can also try other servers if you think Apache is too heavy by default:

Nginx, Lighttpd, Caucho Resin, .etc .etc

However, I do agree with the above posters - the default Apache installation does not use much resources in low traffic. It is when a large amount of traffic reaches the server that optimization is required.

---

### Post by jonobr on 2013-01-17
>  It's been around for nearly two decades now.

Man Im getting old......

---

### Post by brent1975 on 2013-01-23
> **tgalati4 said:**
> What resources do you want to free up?  RAM, CPU utilization?  Electrical power?  To me the last one is most important because your power bill (running 24/7) will exceed the cost of hardware in a few years.

You can run Apache on a desktop machine and not even know it's running.  It's only when your site gets slammed with traffic that you have a problem and chances are your internet connection is the bottleneck, not CPU power to answer http requests.

If you are low on RAM, add more RAM to the system.  Any apache tweaks will simply offload the performance to something less desireable like swap.  There are "light" servers such as:

lighttpd - A fast webserver with minimal memory footprint

But they may not run all of the web services that you want.  Can lighttpd run Drupal7? I don't think so.

Most tweaking of Apache has to do with maximizing http requests per second, and that assumes maximum bandwidth to the internet--which you do not have.  Otherwise you would not be asking this question.

You can install apache plug-ins like fastcgi and other "precompiled" modules that help serve requests faster, but for a home site, you may not notice the difference, because the traffic is so low.

The biggest performance gain is to avoid crappy, desktop processors like the Celeron.  Stick with business-grade Xeon processors and you won't care about performance tweaking anymore.

Thanks for the reply. Yes that is basically what my server is. Just an old desktop that I used to use a couple years ago has 2 gig of ram I don't even recall what processor is in there.   I don't really have alot running on the server basic lamp with samba. for my storage shares. A teamspeak server for my sons online game that he plays and minidlna for listing to music on all of our devices.  I am not sure going out getting a buisness grade xeon would be in the best interest for something so small... But I will take a look and see what the cost is.

---

### Post by hydn79 on 2013-01-23
If you have VERY low traffic as you confirmed and want to lower RAM usage greatly. Then change config to this:

```
<IfModule prefork.c>
StartServers	   1
MinSpareServers    1
MaxSpareServers    2
ServerLimit	  32
MaxClients        32
MaxRequestsPerChild  1000
</IfModule>

```

Restart. RAM usage cut in half!

---

