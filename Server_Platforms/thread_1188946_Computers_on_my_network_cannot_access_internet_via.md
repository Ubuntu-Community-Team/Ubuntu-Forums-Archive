---
title: "Computers on my network cannot access internet via Squid cache"
date: 2009-06-16
forum: Server Platforms
---

### Post by marklodge on 2009-06-16
I have installed debian to run Squid cache as a caching proxy.
Ive been bashing away now for 2 days and i have managed to install squid (i first tried manually, but that did not work so i used synaptic software packager to install it (from Administration menu)
That went well, thereafter i installed webamin to work with squid in a GUI
I have managed to start squid and added my range of IP addresses to the ACL list ( as mentioned here: [http://doxfer.com/Webmin/SquidProxyServer](http://doxfer.com/Webmin/SquidProxyServer) )
I have added the proxy restriction too.
Now, i tried to test it.
I opened Iceweasel Web browser (on the same machine) and setit to use the Proxy server: localhost and port:3128
That works fine. 
But when i try to change the proxy setting to my machines ip (where squid is installed) : 
Proxy server: 10.0.0.35 and port:3128
That does not work. 
Am i missing something, please help
I then tried to set another windows PC on the network to:
Proxy server: 10.0.0.35 and port:3128
That also does not work.
I also edited the conf file to http_access allow all, but i do not know if i have doen it correctly, but maybe there is another problem?
I would really appreciate your comments and help 
Thank you in advance

---

### Post by iponeverything on 2009-06-16
cd /etc/squid and post the output of:

```
cat squid.conf|grep -v \# |grep -v "^$"
```

---

