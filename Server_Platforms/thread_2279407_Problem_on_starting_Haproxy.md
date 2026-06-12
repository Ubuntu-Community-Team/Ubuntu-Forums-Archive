---
title: "Problem on starting Haproxy"
date: 2015-05-23
forum: Server Platforms
---

### Post by satimis on 2015-05-23
Hi all,

Guest VM - Ubuntu 14.04 Haproxy
Host - Ubuntu 14.04
VirtualBox
On router - port 80 forwarded to VM

This is a new installation.

$ sudo service haproxy restart
 * Restarting haproxy haproxy```

[ALERT] 142/180117 (1118) : Starting frontend http-frontend: cannot bind socket [static_IP:80]
   ...fail!

```

$ netstat -nat | grep 80 | grep LISTEN```

tcp6       0      0 :::80                   :::*                    LISTEN   

```

cat /etc/haproxy/haproxy.cfg```

global
        log /dev/log    local0
        log /dev/log    local1 notice
        chroot /var/lib/haproxy
        stats socket /run/haproxy/admin.sock mode 660 level admin
        stats timeout 30s
        user haproxy
        group haproxy
        daemon

        # Default SSL material locations
        ca-base /etc/ssl/certs
        crt-base /etc/ssl/private

        # Default ciphers to use on SSL-enabled listening sockets.
        # For more information, see ciphers(1SSL). This list is from:
        #  https://hynek.me/articles/hardening-your-web-servers-ssl-ciphers/
        ssl-default-bind-ciphers ECDH+AESGCM:DH+AESGCM:ECDH+AES256:DH+AES256:ECDH+AES128:DH+AES:ECDH+3DES:DH+3DES:RSA+AESGCM:RSA+AES:RSA+3DES:!aNULL:!MD5:!DSS
        ssl-default-bind-options no-sslv3

defaults
        log     global
        mode    http
        option forwardfor
        option http-server-close
        option  httplog
        option  dontlognull
        timeout connect 5000
        timeout client  50000
        timeout server  50000
        errorfile 400 /etc/haproxy/errors/400.http
        errorfile 403 /etc/haproxy/errors/403.http
        errorfile 408 /etc/haproxy/errors/408.http
        errorfile 500 /etc/haproxy/errors/500.http
        errorfile 502 /etc/haproxy/errors/502.http
        errorfile 503 /etc/haproxy/errors/503.http
        errorfile 504 /etc/haproxy/errors/504.http

        frontend http-frontend
        bind static_IP:80
        reqadd X-Forwarded-Proto:\ http

        backend wwwbackend
        server 1-www 192.168.0.xxx:80 check
        server 2-www 192.168.0.xxx:80 check
        server 2-www 192.168.0.xxx:80 check

```

Please help.  Thanks

Regards
satimis

---

### Post by TheFu on 2015-05-23
What other process could snatch port 80 before haproxy starts?  Could there be a web server on the same box already? I see the netstat ... perhaps **lsof** would show more?  If you don't start haproxy and telnet to port 80 then GET? What happens?

Did haproxy actually stop?

Is the VM bridge or NAT? Any iptables forwarding happening too?

BTW, you've already done so good stuff there. It is just that something is grabbing port 80, so we need to find it.

---

### Post by satimis on 2015-05-23
> **TheFu said:**
> What other process could snatch port 80 before haproxy starts?  Could there be a web server on the same box already? I see the netstat ... perhaps **lsof** would show more?  If you don't start haproxy and telnet to port 80 then GET? What happens?

Did haproxy actually stop?

Is the VM bridge or NAT? Any iptables forwarding happening too?

BTW, you've already done so good stuff there. It is just that something is grabbing port 80, so we need to find it.
Hi,

LAMP is installed on the VM.  But no website is running
Network - Bridge
iptables not configured

&#10219; lsof | tail```

tail      4217         satimis    1u      CHR             136,23      0t0      26 /dev/pts/23
tail      4217         satimis    2u      CHR             136,23      0t0      26 /dev/pts/23
lsof      4218         satimis  cwd       DIR                8,1     4096  931720 /home/satimis
lsof      4218         satimis  rtd       DIR                8,1     4096       2 /
lsof      4218         satimis  txt       REG                8,1   163224     695 /usr/bin/lsof
lsof      4218         satimis  mem       REG                8,1  7216688    8230 /usr/lib/locale/locale-archive
lsof      4218         satimis  mem       REG                8,1  1840928  148401 /lib/x86_64-linux-gnu/libc-2.19.so
lsof      4218         satimis  mem       REG                8,1   149120  148398 /lib/x86_64-linux-gnu/ld-2.19.so
lsof      4218         satimis    4r     FIFO                0,8      0t0   29725 pipe
lsof      4218         satimis    7w     FIFO                0,8      0t0   29726 pipe

```

# lsof -Pni | grep ":80"
No output

~&#10219; sudo service apache2 stop```

[sudo] password for satimis: 
 * Stopping web server apache2
 * 

```

~&#10219; netstat -nat | grep 80 | grep LISTEN
No output

&#10219; sudo service haproxy stop```

 * Stopping haproxy haproxy
   ...done.

```

&#10219; sudo service haproxy start```

 * Starting haproxy haproxy
[ALERT] 142/210955 (17774) : Starting frontend http-frontend: cannot bind socket [61.92.142.14:80]
   ...fail!

```

satimis

---

### Post by TheFu on 2015-05-23
61.92.142.14:80 ????  How does the VM get this IP?  Is your box on a NAT network behind a router?  Most home users would have a router connected to their single public IP, forward port 80 to the HAproxy running on a 192.168.x.x static internal LAN address. HAproxy would be on that private subnet, not the public internet. Does this appear close?
```
61.92.142.14
|____WAN-router-LAN
|    |____LAN-PC-bridge (192.168.x.x)
|    |    |____bridge-VBox-HA_proxy
|    |    |    |____192.168.x.x
```

Does ifconfig show that IP for the VM? Does it ping on the internet from that IP?

Of course, if you've got a different network setup, please describe. I'd rather not assume this stuff while we work to get this going.

BTW - I normally use **sudo lsof |grep 80** to find which process is listening on a specific port (assuming netstat failed).  However, it seems unlikely for the public IP running on a machine inside a vbox VM to really be connected.  I know exactly how I'd do this on KVM with Linux bridges, but don't know how to do it with vbox.  Hope you don't mind - I just did an nmap scan of that IP. From here, port 80 is closed, which doesn't say much.

---

### Post by satimis on 2015-05-23
> **TheFu said:**
> 61.92.142.14:80 ????  How does the VM get this IP?  Is your box on a NAT network behind a router?  Most home users would have a router connected to their single public IP, forward port 80 to the HAproxy running on a 192.168.x.x static internal LAN address. HAproxy would be on that private subnet, not the public internet. Does this appear close?
```
61.92.142.14
|____WAN-router-LAN
|    |____LAN-PC-bridge (192.168.x.x)
|    |    |____bridge-VBox-HA_proxy
|    |    |    |____192.168.x.x
```

Yes, it is correct.

> 
Does ifconfig show that IP for the VM? 

Yes

> 
Does it ping on the internet from that IP?

&#10219; ping yahoo.com```

PING yahoo.com (206.190.36.45) 56(84) bytes of data.
64 bytes from ir1.fp.vip.gq1.yahoo.com (206.190.36.45): icmp_seq=1 ttl=51 time=205 ms
64 bytes from ir1.fp.vip.gq1.yahoo.com (206.190.36.45): icmp_seq=2 ttl=51 time=204 ms
...

```

> 
BTW - I normally use **sudo lsof |grep 80** to find which process is listening on a specific port (assuming netstat failed). 

It output a big file.

Edit
===
&#10219; sudo haproxy -d -f /etc/haproxy/haproxy.cfg
```

Available polling systems :
      epoll : pref=300,  test result OK
       poll : pref=200,  test result OK
     select : pref=150,  test result FAILED
Total: 3 (2 usable), will use epoll.
Using epoll() as the polling mechanism.
[ALERT] 142/215626 (23675) : Starting frontend http-frontend: cannot bind socket [61.92.142.14:80]

```

Regards
satimis

---

### Post by TheFu on 2015-05-23
If my diag is correct, then HAproxy needs to be setup for 192.168.x.x, NOT the public IP.

---

### Post by satimis on 2015-05-23
> **TheFu said:**
> If my diag is correct, then HAproxy needs to be setup for 192.168.x.x, NOT the public IP.
Your advice works.

satimis@haproxy:~&#10219; sudo /etc/init.d/haproxy start```

 * Starting haproxy haproxy
   ...done.

```

&#10219; sudo haproxy -d -f /etc/haproxy/haproxy.cfg  ```
                
Available polling systems :
      epoll : pref=300,  test result OK
       poll : pref=200,  test result OK
     select : pref=150,  test result FAILED
Total: 3 (2 usable), will use epoll.
Using epoll() as the polling mechanism.
[WARNING] 143/000612 (11002) : Server wwwbackend/1-www is DOWN, reason: Layer4 timeout, check duration: 2001ms. 2 active and 0 backup servers left. 0 sessions active, 0 requeued, 0 remaining in queue.
[WARNING] 143/000613 (11002) : Server wwwbackend/2-www is DOWN, reason: Layer4 timeout, check duration: 2001ms. 1 active and 0 backup servers left. 0 sessions active, 0 requeued, 0 remaining in queue.
[WARNING] 143/000614 (11002) : Server wwwbackend/3-www is DOWN, reason: Layer4 timeout, check duration: 2002ms. 0 active and 0 backup servers left. 0 sessions active, 0 requeued, 0 remaining in queue.
[ALERT] 143/000614 (11002) : backend 'wwwbackend' has no server available!

```

I'll set up the web servers later and check again.

Thanks

Regards
satimis

---

### Post by TheFu on 2015-05-23
Nice.  Glad it worked.

Sometimes this stuff gets confusing and a diagram is needed.  You can't just pick any IP you like (well .... that isn't really true, but there are repercussions when you do this, especially if you don't really, completely, understand, IP networking and your router is just a home version). 

BTW - I've never used HAproxy. For a reverse proxy like this, I've used pound and nginx. Stayed with nginx for the extra features (speed, caching, performance, security, compression) it provides, while not being bloated like other options.  HAproxy certainly is some fine software, so I'm not suggesting you should switch.

Have a great day in HK-NT! I always enjoy visiting there.

---

### Post by satimis on 2015-05-23
Hi,

Problem still remains, not completely solved although Haproxy is running.

Started the 3 VMs with websites running.

$ sudo /etc/init.d/haproxy status```

haproxy is running.

```

$ sudo haproxy -d -f /etc/haproxy/haproxy.cfg```

Available polling systems :
      epoll : pref=300,  test result OK
       poll : pref=200,  test result OK
     select : pref=150,  test result FAILED
Total: 3 (2 usable), will use epoll.
Using epoll() as the polling mechanism.
00000000:http-frontend.accept(0005)=0007 from [61.92.142.14:55424]
00000000:http-frontend.clireq[0007:ffffffff]: GET / HTTP/1.1
00000000:http-frontend.clihdr[0007:ffffffff]: Host: piano1.satimis.com
00000000:http-frontend.clihdr[0007:ffffffff]: User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0
00000000:http-frontend.clihdr[0007:ffffffff]: Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
00000000:http-frontend.clihdr[0007:ffffffff]: Accept-Language: en-US,en;q=0.5
00000000:http-frontend.clihdr[0007:ffffffff]: Accept-Encoding: gzip, deflate
00000000:http-frontend.clihdr[0007:ffffffff]: Cookie: wp-settings-1=hidetb%3D1%26libraryContent%3Dbrowse%26editor%3Dtinymce%26imgsize%3Dmedium; wp-settings-time-1=1432306505
00000000:http-frontend.clihdr[0007:ffffffff]: Connection: keep-alive
00000000:http-frontend.clihdr[0007:ffffffff]: Cache-Control: max-age=0
00000000:http-frontend.clicls[0007:ffffffff]
00000000:http-frontend.closed[0007:ffffffff]
00000001:http-frontend.accept(0005)=0007 from [61.92.142.14:55427]
00000001:http-frontend.clireq[0007:ffffffff]: GET / HTTP/1.1
00000001:http-frontend.clihdr[0007:ffffffff]: Host: piano1.satimis.com
00000001:http-frontend.clihdr[0007:ffffffff]: User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:38.0) Gecko/20100101 Firefox/38.0
00000001:http-frontend.clihdr[0007:ffffffff]: Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
00000001:http-frontend.clihdr[0007:ffffffff]: Accept-Language: en-US,en;q=0.5
00000001:http-frontend.clihdr[0007:ffffffff]: Accept-Encoding: gzip, deflate
......
.....

```

The websites on the VMs can't be accessed on Internet.

Warning:```

503 Service Unavailable
No server is available to handle this request.

```

On Haproxy VM terminal, ping the websites without problem, showing public IP as well.

> 
- snip -
Stayed with nginx for the extra features (speed, caching, performance, security, compression) it provides, while not being bloated like other options.  HAproxy certainly is some fine software, so I'm not suggesting you should switch.
.
I'll test nginx later.  I'll clone a VM with Ubuntu 14.04 as OS for its test.  Also I'll ensure LAMP is not running avoiding confusion.

I found following links for testing nginx;
nginx
[http://nginx.org/](http://nginx.org/)

nginx community
[http://wiki.nginx.org/Install](http://wiki.nginx.org/Install)

How To Install Linux, nginx, MySQL, PHP (LEMP) stack on Ubuntu 14.04
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04)

Nginx Basics &#8211; Install Nginx on Red Hat Enterprise Linux and Debian based OSs
[http://www.rackspace.com/knowledge_center/article/nginx-basics-install-nginx-on-red-hat-enterprise-linux-and-debian-based-oss](http://www.rackspace.com/knowledge_center/article/nginx-basics-install-nginx-on-red-hat-enterprise-linux-and-debian-based-oss)

Any suggestion?  Thanks

Regards
satimis

---

### Post by satimis on 2015-05-25
Hi all,

I discovered the trick.

On /etc/haproxy/haproxy.cfg```

.....
.....
        backend wwwbackend
        server 1-www 192.168.0.xxx:80 check
        server 2-www 192.168.0.xxx:80 check
        server 2-www 192.168.0.xxx:80 check

```

"server 1" should be replaced with the hostname of that VM
same as "server 2" and "server 3".

However problem still remains.  The webpages can't be displayed correctly.  Neither I can login.

Warning:```

The requested URL /wp-login.php was not found on this server.

```

I'll give up Haproxy and start installing Ngnix on another VM.  If still fail, I'll give up load-balancing and install all websites on ONE VM, or on the hdd without vitrualization

Regards
satimis

---

### Post by TheFu on 2015-05-25
Get the website working from outside first, THEN insert the reverse proxy.  For a home user, a single server should be able to flood your uplink bandwidth.   HA-proxy isn't the issue. Switching to some other answer probably won't help.  How are you keeping each client tied to the specific back-end?  Cookies inserted by the proxy or something else?

I didn't search, but suspect there are example haproxy configs for exactly this issue on the internet.  Did a search - [https://www.digitalocean.com/community/tutorials/how-to-use-haproxy-as-a-layer-7-load-balancer-for-wordpress-and-nginx-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-use-haproxy-as-a-layer-7-load-balancer-for-wordpress-and-nginx-on-ubuntu-14-04)

"1-www" is a real hostname?  Can the haproxy box ping it with that name?  **ping 1-www**

I don't know anything about WP (or php), sorry.

---

### Post by satimis on 2015-05-25
> **TheFu said:**
> Get the website working from outside first, THEN insert the reverse proxy.  For a home user, a single server should be able to flood your uplink bandwidth.   HA-proxy isn't the issue. Switching to some other answer probably won't help.  How are you keeping each client tied to the specific back-end?  Cookies inserted by the proxy or something else?

I didn't search, but suspect there are example haproxy configs for exactly this issue on the internet.  Did a search - [https://www.digitalocean.com/community/tutorials/how-to-use-haproxy-as-a-layer-7-load-balancer-for-wordpress-and-nginx-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-use-haproxy-as-a-layer-7-load-balancer-for-wordpress-and-nginx-on-ubuntu-14-04)

"1-www" is a real hostname?  Can the haproxy box ping it with that name?  **ping 1-www**

I don't know anything about WP (or php), sorry.

Hi,

Thanks for your link.

All websites running on VMs can be accessed on Internet without problem if Port 80 is forwarded to their VMs.

Following /etc/haproxy/haproxy.cfg seems working but still having some problem.
```

global
        log /dev/log    local0
        log 127.0.0.1   local1 notice
        maxconn 4096
        user satimis
        group haproxy
        daemon

defaults
        log     global
        mode    http
        option  httplog
        option  dontlognull
        retries 3
        option redispatch
        maxconn 2000
        contimeout     5000
        clitimeout     50000
        srvtimeout     50000

listen webfarm 0.0.0.0:80
    mode http
    stats enable
    stats uri /haproxy?stats
    balance roundrobin
    option httpclose
    option forwardfor
    server lesousvidepc1a 192.168.0.xx2:80 check
    server music_pc1a 192.168.0.xx3:80 check
    server localsites 192.168.0.xx4:80 check

```

satimis is the user of haproxy (group)

VM1 - Load Balancer
Hostname: haproxy
OS: Ubuntu 14.04
Private IP: 192.168.0.xx1

VM2 - Web Server 1
Hostname: lesousvidepc1a
OS: Ubuntu 14,04 with LAMP and Wordpress
Private IP: 192.168.0.xx2
Website - lesousvide.com

VM3 - Web Server 2
Hostname: music_pc1a
OS: Ubuntu 14,04 with LAMP and Wordpress
Private IP: 192.168.0.xx3
Websites - ballet.satimis.com  piano1.satimis.com

VM4 - Web Server 3
Hostname: localsites
OS: Ubuntu 14,04 with LAMP and Wordpress
Private IP: 192.168.0.xx4
Websites - lesousvide.com  satimis.com  ballet.satimis.com

All websites can be ping on Terminal.  Ping hostname doesn't work

Following websites can be accessed on Internet without problem;
lesousvide.com
satimis.com

Following websites can't be displayed properly;
ballet.satimis.com
piano1.satimis.com

Regards
satimis

---

### Post by TheFu on 2015-05-25
Are you trying to have the same website on multiple servers or just trying to use name-based reverse proxy?  If the later, how does haproxy "know" which name to send to which back-end?  I haven't seen anything to provide that posted here.

---

### Post by satimis on 2015-05-25
> **TheFu said:**
> Are you trying to have the same website on multiple servers or just trying to use name-based reverse proxy?  If the later, how does haproxy "know" which name to send to which back-end?  I haven't seen anything to provide that posted here.
This is only a test.  The server is NOT running 24 hrs.

There is a config file, /etc/apache2/sites-enabled/001-local-cfg on each web server VM```

<VirtualHost *:80>
DocumentRoot /var/www/html/ballet
ServerName ballet.satimis.com
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /var/www/html/satimis
ServerName satimis.com
</VirtualHost>

etc.

```


Edit
===
I found the possible cause of the problem.  I couldn't run all web servers (VMs) at the same time.  If I only run ONE web server there is no problem on browsing the websites running on it.  I tried all of them, one by one.  In another word Port 80 couldn't be forward to all web servers simultaneously.

---

### Post by TheFu on 2015-05-26
I run many, many, many different websites off the same port using a reverse proxy which connects to a few different back ends - based on the requested domain by the client.  For my sanity, only the reverse proxy listens on port 80 - all the back end systems listen on different ports - 81, 8080, 8181, 9090, 9191, .... for simple static content, most comes from 1 nginx server on 8080 with different name-based service.

Perhaps if you diagram how each client request routes through you gateway, router, proxy, host, vm, web-server, app-server .... for every domain, you'll see the conflict? Be certain to have ports and IP addr for the front/back of every connection. If there are any collisions, that's bad.

---

### Post by satimis on 2015-05-26
> **TheFu said:**
> I run many, many, many different websites off the same port using a reverse proxy which connects to a few different back ends - based on the requested domain by the client.  For my sanity, only the reverse proxy listens on port 80 - all the back end systems listen on different ports - 81, 8080, 8181, 9090, 9191, .... for simple static content, most comes from 1 nginx server on 8080 with different name-based service.
- snip - 
I have tried 8080 and 8181.  None of them can work.  Websites can't be accessed on Internet.

This is only a test.  The live websites are running on Godaddy server.  I'm prepared testing following feature:-
- The live sites are running on Godaddy server.  I'll clone their local sites.
- When the local sites is UP, visitors will browse the local sites instead of the live sites on Godaddy server
- When the local sites is DOWN, visitors will browse the live sites on Godady server.  It is automatically switched.

---

