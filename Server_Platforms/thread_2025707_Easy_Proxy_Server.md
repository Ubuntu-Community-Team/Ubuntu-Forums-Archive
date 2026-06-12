---
title: "Easy Proxy Server?"
date: 2012-07-14
forum: Server Platforms
---

### Post by markosjal on 2012-07-14
I was wondering if anyone knows of an easy to configure proxy server . I have tried Squid on Ubuntu 10.04 and 10.10 and have never been able to get authentication working no matter what "how to" or front end I have used such as webmin. 

It would seem that someone might have made an easy proxy server .ISO or virtual machine image.

I will be running this on a Virtual Machine on a server with Public IP in a data center. I want the proxy to not reveal the originating IP to web sites. Would be nice if it worked with Hulu. I would like to be able to set up accounts for family and friends. I am NOT looking for a proxy on my LAN.
Open to all suggestions

Thanks

---

### Post by elico on 2012-07-14
you need a "VPN server" with nat and routing capability.
squid i a fine product.
i suppose you have windows client.
so you can use "poptop" as pptp server and use iptables on the remote machine r
to nat your traffic.
you dont need an iso just to learn some basics and make it work.
webmin can give you a lot by allowing you to setup some components easily using web interface but if you dont understand how it works you better try to learn a bit first.
you can try "clearOS" or "zeroshell".
but i recommend you to learn a bit about IPTABLES some routing basics.

---

### Post by markosjal on 2012-07-15
You are mistaken, I do not NEED a VPN server only a proxy. My clients are NOT windows they are XBMC and a few XBMC add ons allow the use of proxy servers but not VPNs.If I use a VPN it will apply to ALL components of XBMC and thereby breaking things that will not work through a proxy.  When you assume you make an a... 

I have tried and studied squid and the issue always comes down to getting authentication to work. There is no good how to and believe me I have found many with I think 3 different authentication methods. Just use google and see the mountain of folks with the same issues with authentication on squid.

---

### Post by SeijiSensei on 2012-07-15
If the clients have fixed IP addresses, use Squid ACLs to control access if you cannot get authentication to work.

Put the IPs in a file, say /etc/squid/myfriends, then add these rules to squid.conf:

```

acl FRIENDS src "/etc/squid/myfriends"
http_access allow FRIENDS
http_access deny all

```

---

### Post by elico on 2012-07-15
i maintains couple squid instances for more then 2 years  and authentication seems to work great for me.
if you are having troubles with auth i will be more then happy to assist you in it here or better on squid-users list.(havnt seen your post if you did).
the main reason you do need vpn is that it's almost the only way to completely identify yourself under other IP.
there is a nice option of using GRE tunnel which is like VPN.
if you have XBMC and all the components are http proxy ready you should check any proxy authentication options are supported in XBMC.
if you want to use squid youl also need to strip off the X-forward headers and better not  to use any disk cache on a VPS.

dont try to use squid + webmin because the module is broken for a long time.
if you want to know a thing or two about how to setup squid authentication:
first read from the definiteguide:
[http://etutorials.org/Server+Administration/Squid.+The+definitive+guide/Chapter+12.+Authentication+Helpers/12.2+HTTP+Basic+Authentication/](http://etutorials.org/Server+Administration/Squid.+The+definitive+guide/Chapter+12.+Authentication+Helpers/12.2+HTTP+Basic+Authentication/)
but since it's not updated to the current squid3+
this is an updated one:
[http://wiki.squid-cache.org/Features/Authentication](http://wiki.squid-cache.org/Features/Authentication)
it contains all you need to know how to set it up.
to set it up all together will be 2-4 minutes max.
you need to install apache-utils squid3 allow http_acces by authenticator helper create a simple http\apache httpasswd file with users and you are done.

---

### Post by markosjal on 2012-07-16
for two yers? That means that the installations were over 2 years ago. Probably not squid 3 
a lot has changed.

As for the Fixed IP auth, yea right. I suppose if its on the same LAN as the clients, or fixed public IPs . Not realistic in this case

Actually I found artica for squid . a nice ISO that seems to work and only a few bugs . Authentication built in.

---

### Post by elico on 2012-07-17
> **markosjal said:**
> for two yers? That means that the installations were over 2 years ago. Probably not squid 3 
a lot has changed.

As for the Fixed IP auth, yea right. I suppose if its on the same LAN as the clients, or fixed public IPs . Not realistic in this case

Actually I found artica for squid . a nice ISO that seems to work and only a few bugs . Authentication built in.
and what about a Fully working without bugs squid + ubuntu?
what iso did you found?

---

### Post by markosjal on 2012-07-17
Nothing with Ubuntu and authentication. Artica is Debian. It probably will install to Ubuntu but the ISO is easier.

---

