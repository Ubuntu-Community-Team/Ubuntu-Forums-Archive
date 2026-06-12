---
title: "DNS - Cache Snooping"
date: 2010-11-22
forum: Server Platforms
---

### Post by Lloyd_mcse on 2010-11-22
Hi guys,
I'm very new to linux and ubuntu but i have managed to set up a small server to use as a test system so I can check things out before I upgrade our companies live server.
 
I am using Ubuntu 10.4 x64 with BIND9, I have set ..
 
>  
directory "/var/cache/bind";
allow-recursion {
localhost;
};
allow-query-cache {
localhost;
}; 

 
in /etc/bind/named.conf.options but it still fails a PCI scan because of 
**"DNS Cache Snooping"** am I using the correct file to set this. 
The fail description give a link to a document from 2004, Ubuntu 8.04 LTS on our live server doesn't fail on this.
Has anyone else had and fixed this issue?
Thanks in advance for any help
Kind regards
 
Lloyd

---

