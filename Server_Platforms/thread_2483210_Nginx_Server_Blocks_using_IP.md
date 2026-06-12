---
title: "Nginx Server Blocks using IP"
date: 2023-01-23
forum: Server Platforms
---

### Post by Bob_Mendon on 2023-01-23
I set up an ubuntu Nginx server. I have three virtual hosts. How can I set up accounts like commercial web hosts? Each host would have it's own IP and root directory etc.

---

### Post by MAFoElffen on 2023-01-23
Something like this:
```

server {
  listen          12.34.56.78:80;
  server_name     domain1.com

  index           index.html;
  root            /var/www/domain1.com
}

server {
  listen          98.76.54.32:80;
  server_name     domain2.com;

  index           index.html;
  root            /var/www/domain2.com


```

---

### Post by TheFu on 2023-01-23
Typically, people use virtualhosts with SNI to share the same IP across any number of websites. [https://nginx.org/en/docs/http/server_names.html](https://nginx.org/en/docs/http/server_names.html)

If you want to force separate IPs to be used, then in the nginx per-site config file, you'll need to specify the IP:port, not just the port.  Read up on the "listen" directive in the nginx documentation.

If you like, you can use nginx as a load balancer or a reverse proxy.  This is a little more complex than I'm willing to explain here.  I use it this way too and have traffic sent to different back-end servers on the local network.  This uses the "upstream" and "server" config options (this is server in a different way than the normal "server stanza" used 
```
upstream blogproxy {
       server 172.22.22.41:9000;
       server 172.22.22.41:9001;
       server 172.22.22.42:9000;
       server 172.22.22.42:9001;
}
```

Add in the location stanza that references the named upstream in the proxypass and you have a load balanced, highly scalable setup. I'm leaving out lots of other things necessary, but the sort version is:
```
        location @your-server-alias {
#   ..... 15 other lines here to handle compression, micro--caching, headers and proxy stuff.
                 proxy_pass http://blogproxy ;
        }
```
       Note how the "blogproxy"  is used in the location and in the upstream.

Of course, there's lots of any hacking stuff in the config file and I use "include" where I've standardized different things, like logs, blocked IP ranges, SSL cert stuff, user-agents I don't want to allow access, and certain URLs that should never be allowed in any request. Lots of security things in my nginx files to block all sorts of exploits or even just people trying to steal bandwidth by directly accessing some media content, but without using the websites.  Lots of things added over the decades, based on real-world experience.

---

