---
title: "Complex Web Configuration"
date: 2012-02-01
forum: Server Platforms
---

### Post by Pyr3x on 2012-02-01
I run a web server on Ubuntu Server 11.10 (Apache 2) and KVM on the Same Box. The OS within the VM is Server 2008 running exchange & IIS. Is it possible to allow web access to the mail boxes via IIS and the website access through Apache but have the Linux box forwarding based on the domain name used to access the site such as "mail.sitenamehere.com"?

This would be very cool as Apache has a lot more to offer me then IIS but exchange has more to offer me in the mail department.

I would very much appreciate any help that can be offered on this complicated configuration!

---

### Post by SeijiSensei on 2012-02-01
I'm not entirely sure what you're trying to do here, but it sounds like you'd like requests for "mail.example.com" to be routed to IIS on the VM and requests for "www.example.com" to be answered by Apache on the VM host.

If so, you can do this with Apache by creating a VirtualHost definition for mail.example.com that invokes Apache's [proxy]("http://httpd.apache.org/docs/2.1/mod/mod_proxy.html").  Point the proxy at the VM's IP address.

---

### Post by TheFu on 2012-02-01
I'd treat the  Exchange VM as a completely different server, setup bridged networking on the hostOS, not NAT, and forward whatever traffic you want from the router to the alternate internal IP address and ports.
Router     Forward-To
25          Exchange-25
80          Apache-80
443        Exchange-443

Simple?  I assuming you are running NAT to the VM from the hostOS. Is that correct?  Make the Exchange-VM have a static IP on the same subnet that your hostOS does.  There are guides for setting up bridges to VMs in Ubuntu out there. Perhaps 11.10 makes this easier?  I'm still running 10.04 LTS - stability matters most to me.

Apache is very powerful, but it is pretty heavy if all you want is a reverse proxy.  Nginx, pound and even squid are alternatives. I'm certain there are more options.  Name-based forwarding is possible in apache and pound and nginx. Further, you can install an SSL cert in the load balancer to keep life easier, but convincing some back-end systems to make all their URLs be HTTPS when they don't manage the cert may not be possible (or may just be really difficult).

From a system design standpoint, it is best to not run any public services, like Apache or Samba on the hostOS. Instead put them inside a VM (or two). There are lots of good reasons besides improved system stability and security to do this.  It does add a level of complexity, but at least then all your public services are in a VM.  OTOH, I'm certain that lots of home users run services on their VM hosts just like you.

I virtualize pretty much everything - even my main desktop OS runs inside a VM along with about 15 "services" each running inside a VM.

Lastly, if you are interested in an MS-Exchange replacement, check out Zimbra. It has impressive capabilities beyond what Exchange provides. Been running it here inside a VM for almost 4 years. LOVE IT and it doesn't eat a MS-Windows license.  I understand needing to understand MS-Exchange and running it yourself to gain skills. We all got bills to pay.

Anyway, I hope this helps in some way, even if I misunderstood your question.

---

### Post by Pyr3x on 2012-02-02
Thank you both for the replies!.

I used the Apache proxy method and it's working great if I open say:

mail.example.com

It forwards to the IIS Server as expected.

Now the issue I am being faced with is what if it's using SSL?

It's being directed to the Apache server. How would I fix this?


This is what I added to the Apache 2 (000-default)

```

<VirtualHost *:80>
  ServerName mail.example.com
  ServerAlias www.mail.example.com
  ServerAdmin someadmin@gmail.com
  ProxyRequests Off
  ProxyPass / http://internalip:80/
  ProxyPassReverse / http://internalip:80/
</VirtualHost>

```

---

### Post by volkswagner on 2012-02-02
I believe for you to get ssl working you need to do the same thing for your port 443.

```
<VirtualHost *:443>
  ServerName mail.example.com
  ServerAlias www.mail.example.com
  ServerAdmin someadmin@gmail.com
  ProxyRequests Off
  ProxyPass / https://internalip:443/
  ProxyPassReverse / https://internalip:443/
</VirtualHost>
```

Notice the https also.


Pyr3x, May I ask the steps you took for getting this to work.  After seeing your thread, I attempted the same thing.

I have inside mods-enabled "proxy_http.load, proxy.load and proxy.conf".  Do you have any added mods?

Did you have to do anything on your iis server?

My requests don't get past my Apache2 server.

---

### Post by SeijiSensei on 2012-02-02
Proxies and HTTPS don't mix.  The proxy will appear to be a "man-in-middle-attack."

If you have only one HTTPS server, I'd just forward the traffic from the host's port 443 to the guest's 443.  You can use iptables for this or an application-level TCP proxy like [this one]("http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/proxies/TcpProxy") (requires compilation).

---

