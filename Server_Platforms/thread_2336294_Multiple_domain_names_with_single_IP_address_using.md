---
title: "Multiple domain names with single IP address using LXC containers"
date: 2016-09-06
forum: Server Platforms
---

### Post by courtney2 on 2016-09-06
Right now I'm trying to set up a server that does both a website and Nextcloud. I have the website and Nextcloud running perfectly in separate containers. Currently nextcloud occupies ports 80 and 443, and I was contemplating putting the website container on the DMZ. How can I make it so that typing in either one of these domain names points to the right container?

---

### Post by ian-weisser on 2016-09-07
Both containers must use different ports that you specify.
Then use iptables on the host to forward port requests to the correct container.

---

### Post by volkswagner on 2016-09-07
Provided your containers have unique ip addresses, you can use reverse proxy.

I wrote a [basic how to]("https://ubuntuforums.org/showthread.php?t=1920715") on this.

Please note the comment on SSL/port 443.

---

### Post by courtney2 on 2016-09-08
ian-weisser, would that mean I would be using the host server IP address for port forwarding? If I'm understanding this right, the host would receive the request to domain1.com or domain2.com, then use iptables to forward to the container. Would I then need to do any apache configuration on the host to accomplish all of that or is it just strictly iptables handling all of this? 

volkswagner, I have just a couple questions before I jump on that. I want to put one container on the DMZ because all it is doing is working as a wordpress website. Would this reverse proxy thing still work if I set one machine in the DMZ? So for example, I run the reverse proxy on my wordpress server and then have it send the port 80 requests to my other server. I shouldn't have to about port 443 with the reverse proxy because the site forces a redirect to an HTTPS connection if it receives an HTTP request. Would that mess with the reverse proxy?

---

### Post by ian-weisser on 2016-09-08
> **courtney2 said:**
> ian-weisser, would that mean I would be using the host server IP address for port forwarding? If I'm understanding this right, the host would receive the request to domain1.com or domain2.com, then use iptables to forward to the container. Would I then need to do any apache configuration on the host to accomplish all of that or is it just strictly iptables handling all of this? 

Let's clarify using a terrible example.
Your host is 1.1.1.1. Your containers are 10.10.10.10 and 10.10.10.11
Request for domain1.com:10 gets converted by dns to 1.1.1.1:10. iptables forwards the packet to 10.10.10.10
Request for domain2.com:11 gets converted by dns to 1.1.1.1:11. iptables forwards the packet to 10.10.10.11 
Strictly iptables on the host. The packets will not reach Apache on the host.

But you can do even better and get rid of those pesky port numbers.
If you set up your host and container networking cleverly, each container will get a static IP addr or DCHP IP addr from the LAN router (instead of the host)
So your host is 1.1.1.1, and your machines become 1.1.1.2 and 1.1.1.3.
Request for domain1.com gets converted by dns to 1.1.1.2, and the packets magically find your container.
Request for domain2.com gets converted by dns to 1.1.1.3, and the packets magically find your container.

When you set up your containers, learn BOTH ways of setting up the networking. It's much easier to diagnose problems later if you have been exposed to both.
Consider security - Apache should be running in a container, not on the host.

---

### Post by courtney2 on 2016-09-08
I agree with that not running Apache on the host, which is why I thought I would ask :) I like your method ian, I think I am going to do that, sounds pretty simple. I sadly don't know iptables all too well so I am going to have to look up how to do this with iptables. I've spent 2 years in school learning a lot of this stuff, but I'm glad I have a simple job that is helping me apply what I learned and learn what I don't know!

---

### Post by courtney2 on 2016-09-12
I ended up opting for HAProxy to do the job, however I am unable to configure it properly. I got it to work with http, but my current issue is getting it to direct my https traffic as well. Here are my current configurations

```

global
        log /dev/log    local0
        log /dev/log    local1 notice
        chroot /var/lib/haproxy
        stats socket /run/haproxy/admin.sock mode 660 level admin
        stats timeout 30s
        maxconn 4096
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
        mode    tcp
        option  tcplog
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



frontend http-in
        bind 10.0.0.105:80

        acl is_nextcloud hdr(host) -i domain1.com   #10.0.0.160
        acl is_wordpress hdr(host) -i domain2.com      #10.0.0.165

        use_backend nextcloud_cluster if is_nextcloud
        use_backend wordpress_cluster if is_wordpress

        redirect scheme https code 301 if { hdr_end(host) -i domain1.com } !{ ssl_fc }
        redirect scheme https code 301 if { hdr_end(host) -i domain2.com } !{ ssl_fc }


frontend https-in
        mode tcp
        bind 10.0.0.105:443

        option socket-stats
        tcp-request inspect-delay 5s
        tcp-request content accept if { req_ssl_hello_type 1 }



        use_backend wordpress_cluster if { req_ssl_sni -i domain1.com }
        use_backend nextcloud_cluster if { req_ssl_sni -i domain1.com }

backend wordpress_cluster
        balance leastconn
        #option httpclose
        #option forwardfor
        #server node1 10.0.0.165:80
        mode tcp

        # maximum SSL session ID length is 32 bytes.
        stick-table type binary len 32 size 30k expire 30m

        acl clienthello req_ssl_hello_type 1
        acl serverhello rep_ssl_hello_type 2

        # use tcp content accepts to detects ssl client and server hello.
        tcp-request inspect-delay 5s
        tcp-request content accept if clienthello

        # no timeout on response inspect delay by default.
        tcp-response content accept if serverhello

        stick on payload_lv(43,1) if clienthello

        # Learn on response if server hello.
        stick store-response payload_lv(43,1) if serverhello

        option ssl-hello-chk

        server stn_container 10.0.0.165:443 



        #server is_wordpress 10.0.0.165:443




backend nextcloud_cluster
        balance leastconn
        #option httpclose
        #option forwardfor
        #server node1 10.0.0.160:80
        mode tcp

        # maximum SSL session ID length is 32 bytes.
        stick-table type binary len 32 size 30k expire 30m

        acl clienthello req_ssl_hello_type 1
        acl serverhello rep_ssl_hello_type 2

        # use tcp content accepts to detects ssl client and server hello.
        tcp-request inspect-delay 5s
        tcp-request content accept if clienthello

        # no timeout on response inspect delay by default.
        tcp-response content accept if serverhello

        stick on payload_lv(43,1) if clienthello

        # Learn on response if server hello.
        stick store-response payload_lv(43,1) if serverhello

        option ssl-hello-chk

        server stn_container 10.0.0.160:443 



```

Currently if I type in domain2.com, I get domain1.com's SSL certificate and an established connection with domain1.com. But of course it's an untrusted connection because I typed in domain2.com

---

