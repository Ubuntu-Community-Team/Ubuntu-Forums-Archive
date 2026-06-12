---
title: "squid cache server"
date: 2012-08-24
forum: Server Platforms
---

### Post by mohammad alsharqi on 2012-08-24
hello everybody 
i'd installed squid server on ubuntu to caching & fastest the browse 

but my squid configuration may be incorrect so there is no request from cache but the site had cached, i'd check the access.log but every site was tcp-miss


what is the best conf.. of squid.conf to cache sites

thanks

---

### Post by drdos2006 on 2012-08-24
Have a look here and hopefully it will help you as much as it helped me.
> 
[http://en.kioskea.net/faq/804-ubuntu-installing-an-http-proxy-server-squid#2-configuring-the-proxy](http://en.kioskea.net/faq/804-ubuntu-installing-an-http-proxy-server-squid#2-configuring-the-proxy)

On the Server.......

1.Installing the proxy
To install Squid type the following command in a terminal:

sudo aptitude install squid


2.Configuring the proxy
Configuration of Squid is done by editing the following file: /etc/squid/squid.conf
To edit this file, type Alt+F2 and enter the following command:

gksu gedit /etc/squid/squid.conf


2.1.Naming the proxy
Its important that Squid knows the name of the machine. To do this, locate the line "visible_hostname".
For example, if the machine is called "ubuntu" insert:

visible_hostname ubuntu


2.2 Choosing the Port
By default, the proxy server will use port 3128. To choose another port, locate the line:

http_port 3128



and change the port number, for example:

http_port 3177


2.3.Choosing the interface
By default the proxy server will listen on all interfaces. For security reasons, its better to put it on your local network only. For example, if the network card connected to your LAN has IP 10.0.0.1, change the line:

http_port 10.0.0.1:3177


2.4. Setting access rights and priorities
By default, nobody else is allowed to connect to the proxy server. A list of permissions must be created.

For example, we will define a group encompassing the local network.

Find the line beginning with acl localhost...
At the end of the section, add:

acl localnet src 10.0.0.0/255.255.255.0


2.5. Authorizing access to group
Now that the group is defined, we will authorise it to use the proxy.
*** NOTE WELL ***
Locate the line :
http_access allow ... and add above "http_access deny all"

http_access allow localnet


2.6. Allow the use non-standard ports
By default, Squid allows HTTP traffic only on specific ports (e.g. 80). This can cause problems on websites using other ports.

    For example, [http://toto.com:81/images/titi.png](http://toto.com:81/images/titi.png) will be blocked by Squid 

To avoid this deadlock, find the line: http_access deny! Safe_ports and the edit it to: # http_access deny! Safe_ports 
7.
# Uncomment and adjust the following to add a disk cache directory.
cache_dir  ufs  /var/spool/squid3  100 16  256


regards

---

### Post by SeijiSensei on 2012-08-25
At best squid typically caches only 20-30% of the remote content, mostly graphics.  If you see entries in /var/log/squid/access.log, then the cache is probably running as expected.

Try repeatedly visiting the same site and see whether anything is cached.  If you use this site for testing, you should see objects like the smilies and other icons be cached.  None of the message content is likely to be cached since the site is dynamic.

Also some sites will use HTTP headers to prevent caching their content.  Streaming video sites are a common example of this.

---

### Post by mohammad alsharqi on 2012-08-25
thanks alot  drdos2006 for ur help

SeijiSensei this is access.log when i browse yahoo.com

1345929775.248   2596 192.168.10.3 TCP_MISS/200 66952 GET [http://www.yahoo.com/](http://www.yahoo.com/) - DIRECT/87.248.112.181 text/html
1345929776.123   1427 192.168.10.3 TCP_MISS/200 6004 GET [http://l1.yimg.com/nn/fp/rsz/images/082412/pushup_sm_1345844497.jpg](http://l1.yimg.com/nn/fp/rsz/images/082412/pushup_sm_1345844497.jpg) - DIRECT/183.177.93.19 image/jpeg
1345929776.156   1459 192.168.10.3 TCP_MISS/200 6119 GET [http://l1.yimg.com/nn/fp/rsz/images/082512/1air-ipad_sm_1345911256.jpg](http://l1.yimg.com/nn/fp/rsz/images/082512/1air-ipad_sm_1345911256.jpg) - DIRECT/183.177.93.19 image/jpeg
1345929776.368   1468 192.168.10.3 TCP_MISS/200 3749 GET [http://l.yimg.com/dh/ap/default/120824/rapper1_vmsm.jpg](http://l.yimg.com/dh/ap/default/120824/rapper1_vmsm.jpg) - DIRECT/183.177.93.19 image/jpeg
1345929776.438   1547 192.168.10.3 TCP_MISS/200 8896 GET [http://l.yimg.com/nn/fp/rsz/images/082412/squid1_ac_1345844611.jpg](http://l.yimg.com/nn/fp/rsz/images/082412/squid1_ac_1345844611.jpg) - DIRECT/183.177.93.19 image/jpeg
1345929776.517   1617 192.168.10.3 TCP_MISS/200 14899 GET [http://l.yimg.com/dh/ap/default/120824/hamster1.jpg](http://l.yimg.com/dh/ap/default/120824/hamster1.jpg) - DIRECT/183.177.93.19 image/jpeg
1345929777.346   2035 192.168.10.3 TCP_MISS/200 417 GET [http://b.scorecardresearch.com/p?](http://b.scorecardresearch.com/p?) - DIRECT/77.109.171.72 image/gif
1345929777.411   2018 192.168.10.3 TCP_MISS/200 492 GET [http://us.bc.yahoo.com/b?](http://us.bc.yahoo.com/b?) - DIRECT/217.146.179.205 image/gif
1345929788.981   2540 192.168.10.3 TCP_MISS/200 80031 GET [http://l1.yimg.com/nn/fp/rsz/images/082412/pushup_uni_1345844497.jpg](http://l1.yimg.com/nn/fp/rsz/images/082412/pushup_uni_1345844497.jpg) - DIRECT/183.177.93.19 image/jpeg
1345929798.374   1934 192.168.10.3 TCP_MISS/200 18363 GET [http://l1.yimg.com/dh/ap/default/120824/bride_uni.jpg](http://l1.yimg.com/dh/ap/default/120824/bride_uni.jpg) - DIRECT/183.177.93.19 image/jpeg



and this for facebook

1345929828.414    320 192.168.10.3 TCP_MISS/000 0 GET [http://www.facebook.com/](http://www.facebook.com/) - DIRECT/66.220.153.70 -
1345929829.980   1320 192.168.10.3 TCP_MISS/301 400 GET [http://facebook.com/](http://facebook.com/) - DIRECT/69.171.237.16 text/html
1345929832.295   2308 192.168.10.3 TCP_MISS/200 12404 GET [http://www.facebook.com/](http://www.facebook.com/) - DIRECT/66.220.153.70 text/html
1345929834.106   1726 192.168.10.3 TCP_MISS/302 649 GET [http://secure-us.imrworldwide.com/cgi-bin/m?](http://secure-us.imrworldwide.com/cgi-bin/m?) - DIRECT/138.108.7.20 text/html
1345929837.504   3389 192.168.10.3 TCP_MISS/200 519 GET [http://www.facebook.com/brandlift.php?](http://www.facebook.com/brandlift.php?) - DIRECT/66.220.153.70 image/gif

---

