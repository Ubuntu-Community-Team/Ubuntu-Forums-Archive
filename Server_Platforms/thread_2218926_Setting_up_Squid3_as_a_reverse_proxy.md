---
title: "Setting up Squid3 as a reverse proxy"
date: 2014-04-22
forum: Server Platforms
---

### Post by HelenM on 2014-04-22
Hi Guys,

I have tried my best to study a solution to my continued issues without posting stupid newbie questions on this board.
This is how far I have got, but it wont work at the moment.

What I want to do is to get my proxy to accept a specific url 'example.com' and rewrite that url to a static ip address from my vps.
This is as far as I have got.

My squid.conf file is: 
```

http_port 202.55.1.2:80 accel 
defaultsite=www.example.com 192.168.1.5 parent 80 0 no-query originserver

```
I was trying [COLOR=#333333] to run squid in reverse proxy mode, on port 80 using the static ip 202.55.1.2  and configure it talk to internal the apache server
And my httpd.conf file is:
[/COLOR]```
Port 80
BindAddress 192.168.1.5

```
Has anyone any ideas why this isn't working or if there is a better way to do it.

Hope some can help me.

Take Care

Helen x

---

### Post by koenn on 2014-04-25
the squid conf should probably be something like 
```

http_port 202.55.1.2:80 accel defaultsite=www.example.com 

cache_peer 192.168.1.5 parent 80 0 no-query originserver

```
see [http://wiki.squid-cache.org/SquidFaq/ReverseProxy](http://wiki.squid-cache.org/SquidFaq/ReverseProxy)
your squid.conf should probably contain more that that, you're supposed to add to or modify the defauls, not replace the whole file with just those 2 lines. 


You do understand that the server at 192.168.1.5 should be reachable from your VPS, right ?  That is going to be a problem. How do you intend to make that happen ? 


 a different approach would be to set up apache as a reverse proxy (searcg for apache mod proxy and mod proxy-html. I'ts slightly more complicated but offers more features in terms of mapping URL's to different back-end- servers, URL rewriting, headers and content mangling, etc.
 For what you're doing, you don't need those, and squid is probably more suitable.

---

### Post by SeijiSensei on 2014-04-25
I wouldn't use Squid for this if you trying to proxy web traffic.  Use [Apache with mod_proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") instead.

---

### Post by HelenM on 2014-04-25
Thanks for your replies guys, I have also come to the conclusion that squid is probably no use for  this procedure. From my studying it appears haproxy would probably be my best option and I have been working on a script to achieve my aims, as of yet though it is not working but it is a long way from the couple of lines I opened this thread with.
What attracted me to haproxy is that I am hoping to achieve this without the need to use apache.
Take Care
Helen x

---

### Post by SeijiSensei on 2014-04-25
Your choice, of course, but using Apache is pretty simple.  You just define a virtual host for "example.com" and add the proxy directives to the <VirtualHost> stanza.

---

### Post by koenn on 2014-04-26
> **SeijiSensei said:**
> I wouldn't use Squid for this if you trying to proxy web traffic.  

Why is that ?

---

### Post by SeijiSensei on 2014-04-26
Because it's a lot easier to do it with Apache, particularly if you have virtual hosts.  As I said above, you can define a virtual host that proxies connections for a URL to whatever server you want. I see Squid as designed more as an outbound proxy at which it excels.  Can Squid proxy connections for [www.example1.com](www.example1.com) to one host and those for [www.example2.com](www.example2.com) to another?  If so, I suspect it would take some serious fiddling with squid.conf.  In Apache you just set up two <VirtualHost> containers with the proxy settings for each ServerName.

---

### Post by koenn on 2014-04-26
> **SeijiSensei said:**
> Can Squid proxy connections for [www.example1.com](www.example1.com) to one host and those for [www.example2.com](www.example2.com) to another?  If so, I suspect it would take some serious fiddling with squid.conf.  

Oh, I think you're right about that one.
It's just that in this particular case (re the OP) having squid sit in front of a single website would (apparentmy - I've never uses squid a a reverse proxt myself) require 2 lines in squid.conf - that's what made me wonder about your comment. But I see your point.

In the general case, I also suspect squid would be better at caching (and thus taking load of the back-end server) than, say, apache mod_cache - seeing that caching is  what squid was build for and its elaborate features for tweaking cache behaviour. Loadbalancing between webservers also looks rather straightforward in squid.

---

### Post by koenn on 2014-04-26
oh, and @OP

no matter what software you use for the proxy, you still have to deal with that other problem that the proxy/your VPN needs a network connection to your web server, and 192.168.1.5 is ** not a routable address**

---

### Post by HelenM on 2014-04-26
I wonder if you guys could help me with my haproxy script it wont work, I cant get putty to connect to my proxy at all, it should connect on port 80, but when I telnet the proxy on port 80 it refuses, I have opened port 80 on my vps.
Take Care
Helen x
```

global
  daemon
  maxconn 20000
  user haproxy
  group haproxy
  stats socket /var/run/haproxy.sock mode 0600 level admin
  log /dev/log local0 debug
  pidfile /var/run/haproxy.pid
  spread-checks 5


defaults
  maxconn 19500


  log global
  mode http
  option httplog
  option abortonclose
  option http-server-close
  option persist
  option accept-invalid-http-response


  timeout connect 20s
  timeout server 120s
  timeout client 120s
  timeout check 10s
  retries 3


listen stats # Website with useful statistics about our HAProxy frontends and backends
  bind *:6969
  mode http
  stats enable
  stats realm HAProxy
  stats uri /
  stats auth admin:0us5zW3KDq8pZVZe




frontend f_proxy
  mode http
  bind *:80
  log global
  option httplog
  option accept-invalid-http-request


  capture request header Host len 50
  capture request header User-Agent len 150


  # Botlist
  acl bots hdr_reg(User-Agent) -i Googlebot
  use_backend b_deadend if bots


  #
  # NOT IMPLENTED (example DPI reqrite)
   use_backend b_prime_rewrite if { hdr(host) -i 221.33.1.45 }
  #


  
  


  default_backend b_deadend


backend b_proxy


  log global
  mode http
  option httplog
  option http-server-close


 


  


 
#INSERT_BACKEND


frontend f_proxy_ssl
  bind *:443
  mode tcp
  log global
  option tcplog
  no option http-server-close


  tcp-request inspect-delay 5s
  tcp-request content accept if { req_ssl_hello_type 1 }




  default_backend b_deadend_ssl


backend b_proxy_ssl
  log global
  option tcplog
  mode tcp
  no option http-server-close
  no option accept-invalid-http-response




backend b_deadend
  mode http
  log global
  option httplog


backend b_deadend_ssl
  mode tcp
  log global
  option tcplog
  no option accept-invalid-http-response
  no option http-server-close


backend b_prime_rewrite


  log global
  mode http
  option httplog
  option http-server-close


  # rewrite the Host header 
  reqirep ^Host:\ 221.33.1.45   Host:\ www.example.com


  #--- prime
  use-server prime if { hdr(host) -i 221.33.1.45}
  server primewire www.example.com check inter 10s fastinter 2s downinter 2s fall 1800

```

---

### Post by SeijiSensei on 2014-04-26
> **koenn said:**
> It's just that in this particular case (re the OP) having squid sit in front of a single website would (apparentmy - I've never uses squid a a reverse proxt myself) require 2 lines in squid.conf - that's what made me wonder about your comment. But I see your point.

I was reacting to this part of Helen's request:
> What I want to do is to get my proxy to accept a specific url 'example.com' and rewrite that url to a static ip address from my vps.

That suggested she wanted to proxy requests for example.com (a "specific URL") but not requests for example1.com.  Apache's mod_proxy handles that task with the minimum fuss.

I'm afraid I cannot help with haproxy; I've never used it.  Are you tunneling only requests for example.com, or any connection arriving on port 80?  If the latter, there are many simple options for passing a TCP request through a host.  I've used iptables, [application-level proxies]("http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/proxies/TcpProxy"), and just today set up [xinetd]("http://computerblog2.wordpress.com/2007/05/19/forwarding-ports-using-a-xinetd-redirect/") to proxy requests for POP/IMAP services so I could protect against dictionary attacks.  (There are reasons why I cannot use fail2ban for this purpose.)  What specifically are you trying to do?

If you just want to pass requests for your.outside.ip.addr on port 80 back to some.other.ip.addr also on port 80, you can add this command to /etc/rc.local that uses iptables for the task:
```
/sbin/iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j DNAT --to-destination some.other.ip.addr:80
```
Of course the destination port need not be 80, but any port you choose.  You'll need to enable net.ipv4.ip_forward=1 in /etc/sysctl.conf as well.  Read the instructions in that file.  If you disable FORWARDing by default in iptables, you'd also need a rule that permits forwards coming in on external port 80.

---

