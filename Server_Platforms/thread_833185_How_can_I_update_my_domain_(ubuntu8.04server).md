---
title: "How can I update my domain ?(ubuntu8.04server)"
date: 2008-06-18
forum: Server Platforms
---

### Post by DeeBoo on 2008-06-18
Hello Guys

I am a new user in ubuntu 8.04 server and I have a small problem

I have finished setup ubuntu 8.04 server and I am left with a small problem:

I installed webmin in my server and in some sites in my server it is giving me my network IP instead of my domain , for example :

In one of my sites it is giving me this address :

[http://192.168.2.3/up](http://192.168.2.3/up) and it should be :
[http://www.mydomain.com/up](http://www.mydomain.com/up)

so how can I solve this problem ?? this is the only problem I have

---

### Post by windependence on 2008-06-18
Well I'm not quite sure when you say "it's giving me" just what it is that is giving you the IP instead of the domain, but I believe putting entries in your hosts files will take care of this. The host file would look something like this:

127.0.0.1      localhost
192.168.2.3    server.mydomain.com

-Tim

---

