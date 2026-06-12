---
title: "NAT several web services to port 80/443"
date: 2023-04-04
forum: Server Platforms
---

### Post by finway on 2023-04-04
Hello,
I have an Ubuntu server with several local web services.
I'd like to access those services from Internet
And NAT-like all of them to port 80/443 so I haven't to open other ports on my firewall.

I thought Nginx was able to do that, but it seems it can only redirect... (My browser redirects to hard-specified address without any proxy or NAT resolution)

Am I missing something ?
Is it possible ?
What would be best option ?
Thanks mates !

http://example.com/service1/:80 <--> 127.0.0.1:3001
http://example.com/service2/:80 <--> 127.0.0.1:3002
... etc

---

### Post by TheFu on 2023-04-04
There are many tools that can perform a reverse-proxy, including nginx.   DNS names can be used for this or you can use a proxy config for a specific sub-path to point to a different service.  I prefer using different DNS names myself, since name-based proxies are easy.

[http://srv1.example.com:80/](http://srv1.example.com:80/) <--> {ip}:{port}
[http://srv2.example.com:80/](http://srv2.example.com:80/) <--> {ip}:{port}
[https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/)
I also setup an IP only webserver, with no name to return a tiny static webpage. No need to help random IP scanners to find web servers, right?

nginx can also be the TLS termination handler for HTTPS stuff.  You'll likely need to ensure the returned URLs from the real services generate "HTTPS:" for URLs, even if they are only capable of HTTP.

Beware that placing any web service onto the public internet without requiring key-based authentication just for the connect to be possible first, is asking to be cracked.  Best practice is to setup a VPN server at the location and only allow internal access once the VPN connection is up.  ssh-tunnels can be used too, but those are more hassle for non-Linux clients.  Also, never mix your public webserver on the same LAN as any desktops, unless having your entire LAN pwn'd is the goal. Servers providing internet services need to be firewalled off from all other stuff. The easy way to accomplish that is by having different LANs.

I use nginx as a load balancer for multiple back-end servers. It works well.  I suppose the new kids use HAProxy for that. There are lots of choices and different programming languages have their preferred method.  I'm a perl guy and use starman for my high-availability needs with PSGI services. [https://metacpan.org/pod/Starman](https://metacpan.org/pod/Starman).  Ruby has a number of these. I used "thin" when I did ruby stuff.  I'd assume python and php have their own too.  But even when I'm using PLACK/Starman for HA, I'll use nginx for the TLS termination. My customers don't really care what is used, if it works.  nginx was a little scary there before they moved their HQ out of their home country where the federal police raided their offices on bogus charges. The company behind it is in Seattle now.

Guess it just depends on what you use and learn.  Long ago, before we all moved to TLS connections, I used a different tool - the same one that slashdot used. Can't remember the name now.

25 yrs ago, we could get away with really bad security and not worry too much. That's completely different these days.

Anyway, if you want specific advice, you'll need to post specific setups including config files.

---

### Post by ameinild on 2023-04-07
I use a tool called [Nginx Proxy Manager]("https://nginxproxymanager.com/"). It's a dockerized instance of Nginx that works as a reverse proxy, with a nice GUI to set things up.

There's also HAProxy, which has the benefit of being available as a module for pfSense Firewalls.

---

### Post by finway on 2023-04-08
Thank you both for your answers !

I found a solution with nginx by digging a bit
Yet it's still not pretty clear to me.

I have let's encrytp w/ certbot.

I made a single 'mywebservices.conf' configuration file in /conf.d/
If I do several, I receive an error of port 443 duplication.
I guess it's normal to avoid error, but don't understand why is there site-enable directory etc, if can do only 1 file.

It's still not clear for me who's certificate is used for https.
I guess the one specified in nginx conf file ?!
One of my webservice is http and I connect to it this way in nginx conf, but it redirects automatically to https internally (= w/o nginx).
One of my webservice is https so no other way to connect to it than this way.
Is it okay & safe to do so ? I don't see other way for it to work both in local and on www.

Finally,
My problem was that one of my webservice redirects automatically to a sub-folder
[http://127.0.0.1:3001](http://127.0.0.1:3001) redirects to [http://127.0.0.1:3001/sub/](http://127.0.0.1:3001/sub/)
Thus I needed to add a nginx configuration for /sub/ in addition to /myservice/
as [http://mywebserver/myservice](http://mywebserver/myservice) redirects to [https://myweberserver/sub/](https://myweberserver/sub/)
Is there a way to manage that with nginx without defining /sub/ section ; it doesn't seem proper way to do for me !

<3

---

### Post by TheFu on 2023-04-08
Less description. More actual config files.

---

