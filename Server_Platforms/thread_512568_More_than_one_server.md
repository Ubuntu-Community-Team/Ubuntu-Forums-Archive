---
title: "More than one server"
date: 2007-07-29
forum: Server Platforms
---

### Post by jonk on 2007-07-29
Hi!

I have an ubuntuserver running apache that all traffic to port 80 (amongst others) goes to. Now I'm getting a second  server and I need my server to send visitors for certain domains to go the second server. How do you do that?

---

### Post by koenn on 2007-07-29
hej, 

the obvious way to do this would be that each server has its own (public) IP address and there wouldn't be a problem because DNS would resolve 1 domain to server_1 and another domain to server_2. Simple. 

So either that's what you need but you didn't know it, or you're running 1 and soon 2 servers from behind a NAT router. Your sig sussests the latter. 

You probably can pull this of with a http proxy server (eg squid). 
You'd direct all incomming hhtp to the squid, i.e. forward port 80 on the router to port 3128 at squid.ip.address). 
the proxy server then should get the requested page from 1 of the 2 web servers and serve it back to the client. It's kind of the "reverse" of what a proxy is usually used for, and you'll need to read the documentation on how exactly this has to be set up (reverse proxy, accelerating proxy ...)


You'll probably also need a dns server (eg dnsmasq; bind might be overkill) so that  squid can find out from it that a request for smurf.pirateboy should go to server_1.ip.address but requests for jong.pira.... should go to server_2.ip.address

Note that 'servers' here means software, daemons, services. You don't need a separate machine for each, eg the squid could be running together with webserver_1 and the dnsmasq with webserver_2 or so.

---

### Post by jonk on 2007-07-29
I'm using a singe IP and the two servers are two separate machines.. Isn't there a simple way?

---

### Post by dantrevino on 2007-07-29
If you use one machine its really easy to do virtual hosting.  If you use more than one you'll need to do the squid proxy that koenn suggests.

---

### Post by koenn on 2007-07-29
Yes, there is a simple way.
> **koenn said:**
> the obvious way to do this would be that each server has its own (public) IP address and there wouldn't be a problem because DNS would resolve 1 domain to server_1 and another domain to server_2. Simple.

By having only 1 ipadres and have your router translate the real addresses of the server into its own public address (NAT), you've giving up on the ability to route packages based on their destination address. They all have dst=router.ip.adress : port 80. 
The only way to make distincions, as far as I can see, is the requested URL. You can't solve that on a network level, so you need an appplication, such as a proxy server, to handle that. 
The reverse proxy approach is the most obvious workaround that I can see. Maybe there are others - I'd be interested to see them.

---

### Post by koenn on 2007-07-29
OK, here's an Ugly Workaround (TM) : 

you run only 1 webserver, on server_1. You put the files for some of your websites in a directory on server_2. You export (NFS) or share (samba) that directory / those directories, and mount it/them to the filesystem of server_1. 
Then, you configure the sites/document root of your webserver so that they point eac c to the correct directory. 
All http requests go to and are handled by server_1 - but some files actually live on server 2 but look "local" to the web server. 

Might work, I've never tried it.

---

### Post by lionelp on 2007-08-01
Squid is for me a bit too much. I would use the apache mod_proxy for that. I would serve as you do local domains on the machine which is accessed by Internet. For domains I want to serve on the other machine, I will set-up a virtualhost on the machine accessible for internet containing :

<VirtualHost *:80>
    ServerName myvirtualhost
    ServerAdmin [email]me@mydomain.com[/email]

    ProxyPass           /       [http://myotherserver/](http://myotherserver/)
    ProxyPassReverse    /       [http://myotherserver/](http://myotherserver/)

</VirtualHost>

Your other server must have a virtualhost with name "myotherserver" in that case.

I don't know if my point is clear, but that's quite easy to do with apache mod_proxy.

---

