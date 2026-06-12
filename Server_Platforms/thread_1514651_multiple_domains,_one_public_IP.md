---
title: "multiple domains, one public IP"
date: 2010-06-21
forum: Server Platforms
---

### Post by kentsusai on 2010-06-21
Hiiiiiiiiiii! ):P

I'm stuck folks! help! :P

I would like to set up an ubuntu server to forward outside requests directed to different domains to different computers on my local network. The bind is I only have ONE public IP.

Here's an example of what I want to do.
- if a request is sent to [www.first-domain.com](www.first-domain.com), I want to forward it to a local server (say 192.168.0.10)
- if a request is sent to [www.second-domain.com](www.second-domain.com), I want to forward it to a local server (say 192.168.0.20)
and so on...

I will need to forward these requests not only for web sites but for other services such as SSH, mail, RDP, VNC, etc etc

PS Once it hits those local servers, I know how to use iptables to forward them as desired. Don't need help with that ;)

Cheers!! :KS

---

### Post by Ryan Dwyer on 2010-06-21
You're aware you can host multiple websites/domains on one machine, right?

I assume you don't want to do that for some reason and actually want one server per domain. In that case I'm pretty sure you need to purchase more IP addresses from your internet provider, then configure your router to forward to the internal addresses depending on the external address. Most consumer routers can't do this, so you need a Linux box and some fancy IP tables to control your routing.

The best way is to make one web server, one mail server etc then just forward the ports. Multiple IP's not needed.

---

### Post by cdenley on 2010-06-21
If you have one public IP, then you can't have multiple servers sharing the same port. With HTTP requests, apache can tell which host they are accessing because the browser supplies that in the HTTP headers. It can then serve a separate site (virtual host) or redirect to another server based on which hostname was used. However, for most other types of traffic, there is no way for a server or router to tell which domain was used to access your public IP. The user resolves your domain using their own DNS server, then all traffic with your public IP is by IP address, and the domain is not supplied unless their client (such as a web browser) supplies it.

You either have to provide a unique port for each server, use a single SSH server and tunnel to another server as needed, or use a VPN server and access each server by its own private IP.

---

### Post by kentsusai on 2010-06-22
Hi all,

Thanks for your prompt help, but a work around won’t cut it in this instance.

I only have **ONE **public IP. I cannot get more than **ONE **public IP address.

To explain what I want to do, I'll further elaborate by way of example:-
- if a request is sent to [www.first-domain.com:80](www.first-domain.com:80), I want to forward it to a local server (say 192.168.0.10:80)
- if a request is sent to [www.first-domain.com:22](www.first-domain.com:22), I want to forward it to a local server (say 192.168.0.20:22)
- if a request is sent to [www.second-domain.com:80](www.second-domain.com:80), I want to forward it to a local server (say 192.168.0.30:80)
- if a request is sent to [www.second-domain.com:22](www.second-domain.com:22), I want to forward it to a local server (say 192.168.0.40:22)
- if a request is sent to [www.third-domain.com:80](www.third-domain.com:80), I want to forward it to a local server (say 192.168.0.50:100)
and so on...

I should be able to make requests to different domains on the **same **ports or different ports. If all of my requests have to be on different ports, it just won’t cut it.

Can it be done using Linux?

---

### Post by Ryan Dwyer on 2010-06-22
It can't be done using anything, at least for SSH. When someone connects using SSH the client never sends a domain name. An SSH connection is just a connection on an IP address.

For web traffic, it can be done if you inspect the HTTP packet for the HTTP host header, but I've never seen that method used.

---

### Post by kentsusai on 2010-06-22
Guess what...

Microsoft server **can** do it!

I'd be flabbergasted if Linux can't!!!!! There must be a Linux based solution to my problem!

*EDIT*
CORRECTION! The Microsoft Server can only handle http requests! From what I can see, it **cannot **do exactly what I want.

Seems that unless I get multiple public IPs, I cannot do what I want ](*,)

---

### Post by cryptotheslow on 2010-06-22
I've never actually done it, but for the http traffic you might be able to make it work using the Apache mod_proxy module as a reverse proxy. Take a look at the ProxyPass and ProxyPassReverse directives. [http://httpd.apache.org/docs/1.3/mod/mod_proxy.html](http://httpd.apache.org/docs/1.3/mod/mod_proxy.html)

You could also take a look at Pound proxy for the http stuff.

As for the other traffic, I don't think it's possible as the domain name is not passed from client to server in the connection setup - it is just an IP connection.

Any links to some info on the MS server that can achieve this?

---

### Post by kentsusai on 2010-06-22
See my correction above. The Microsoft Server cannot do exactly what I want.

---

### Post by amanisdude on 2012-05-14
I know this thread is pretty old, but for anyone getting here from a web search, what you might be looking for is a *reverse proxy server* (at least with regard to websites).

You can [Wikipedia]("http://en.wikipedia.org/wiki/Reverse_proxy") what that means, but it's basically a dedicated machine that serves as the entry point to all incoming traffic of a particular type (such as web traffic). This machine takes a particular request (such as an HTTP request) and redirects it to a machine on the internal network via a proxy system.

It then takes the response of that machine on the internal network and redirects it to the Internet user. This is frequently done for security reasons, but it is very useful for splitting up a resource (such as a website with many sub-domains) across multiple machines. Everyday Internet users who connect to a network with this configuration will probably never even know that they're actually connected to a reverse proxy server.

Anyway, an Apache module called [*mod_proxy*]("http://en.wikipedia.org/wiki/Mod_proxy") can be used for this purpose if you're using Apache. (See [the Apache Module pages]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html") for documentation.) You'll, of course, have to know how to configure Apache, and you'll obviously need two or more machines.

Alternatively, if you're trying to [load balance]("http://en.wikipedia.org/wiki/Load_balancing_(computing)") a cluster of servers—that is, if you want to distribute the *SAME* website over multiple machines—you may be able to use [*nginx*]("http://en.wikipedia.org/wiki/Nginx") with Apache (or as the HTTP server itself).

At any rate, what [kentsusai]("http://ubuntuforums.org/member.php?u=346536") wanted to do in this thread in terms of his website is definitely possible with Ubuntu and Apache. Doing this with SSH is probably also possible with a lot more work (and maybe a little hacking), but that's currently beyond my understanding. ^_^"

—***AmanIsDude***

*Additional Resources*:
&#8210; [Reverse proxy - Wikipedia]("http://en.wikipedia.org/wiki/Reverse_proxy")
&#8210; [mod_proxy - he HTTP Server]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html")

*See also*:
&#8210; [Nginx/ReverseProxy - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Nginx/ReverseProxy")
&#8210; [nginx - Wikipedia]("http://en.wikipedia.org/wiki/Nginx")
_________________

---

