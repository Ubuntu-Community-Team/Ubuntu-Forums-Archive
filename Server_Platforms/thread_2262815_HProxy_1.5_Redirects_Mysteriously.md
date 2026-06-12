---
title: "HProxy 1.5 Redirects Mysteriously"
date: 2015-01-27
forum: Server Platforms
---

### Post by bggaudreault on 2015-01-27
Hello, my HAProxy 1.5 haproxy.cfg file is redirecting webqa.domain2.com:80 to web.domain.com, but I can't figure out why since I've tried commenting out all lines that I think are causing the problem.  I was able to comment out webqa.domain2.com:443 successfully.

Background: I'm new to HAProxy and a co-worker setup 2 redundant HAProxy 1.5 servers, but he's also new to HAProxy.  My coworker copied configs from a few different HAProxy 1.4 servers in hopes to combine resources into a redundant structure.

Can someone help?  At the very least, can someone make recommendations on cleaning up the code if it's not well-written for HAProxy 1.5 and the need to process domain.com, domain2.com, and DomainKeep.com traffic?

Here's the washed config file:

########################## GLOBAL SECTION ######################
global


        log     /dev/log        local0
        log     /dev/log        local1 notice
        chroot  /var/lib/haproxy
        stats   socket /run/haproxy/admin.sock mode 660 level admin
        stats   timeout 30s
        user    haproxy
        group   haproxy
        daemon
        maxconn 50000


#      Default SSL material locations
        ca-base         /etc/ssl/certs
        crt-base        /etc/ssl/private


#      Default ciphers to use on SSL-enabled listening sockets.
#      For more information, see ciphers(1SSL).
        ssl-default-bind-ciphers kEECDH+aRSA+AES:kRSA+AES:+AES256:RC4-SHA:!kEDH:!LOW:!EXP:!MD5:!aNULL:!eNULL


########################## DEFAULTS SECTION ######################
defaults


        log        global
        mode     http
        option    httplog
        option    forwardfor
        option    http-server-close
        option    log-health-checks
        option    log-separate-errors
        option    redispatch
        timeout  connect 5000
        timeout  client  50000
        timeout  server  50000
        timeout  http-request 10000
        errorfile 400 /etc/haproxy/errors/400.http
        errorfile 403 /etc/haproxy/errors/403.http
        errorfile 408 /etc/haproxy/errors/408.http
        errorfile 500 /etc/haproxy/errors/500.http
        errorfile 502 /etc/haproxy/errors/502.http
        errorfile 503 /etc/haproxy/errors/503.http
        errorfile 504 /etc/haproxy/errors/504.http


########################## STATISTICS PAGE SECTION ######################
listen stats


        bind    :8080
        stats   enable
        stats   uri /haproxy?stats
        stats   realm Strictly\ Private
        stats   auth account:password


########################## FRONT ENDs SECTION ######################
frontend http_in


        bind :80
        timeout client 600000
        capture request header Host      len 100
        capture request header Referer  len 100
        tcp-request content reject if { src -f /etc/haproxy/blacklist.lst }


        acl services80 hdr_dom(host) -i services.domain2.com
        acl appspro80 hdr_dom(host) -i appspro.domain2.com
        acl check80 hdr_dom(host) -i    check.domain2.com
#      acl valid hdr_dir(referer) -i       domain.com


        acl    DomainKeep.com.acl hdr_dom(host) -i DomainKeep.com
#      acl webqa hdr_dom(host) -i                        webqa.domain2.com
        acl webdev hdr_dom(host) -i                       webdev.domain2.com
        acl webstage hdr_dom(host) -i                    webstage.domain2.com
#      acl vecapp url_sub                                    /stuff/stuff.html


        acl ssl_only.acl url_sub /stuff/login.aspx url_sub /order/stuff/login.aspx url_sub /login url_sub /stuff url_sub buynow url_sub /order/stuff/junk
#      acl ssl_var.acl url_sub .ashx url_sub .css url_sub .js url_sub .jpg url_sub .png url_sub .gif url_sub .axd


#      redirect code 301 prefix [https://web.domain.com](https://web.domain.com) if ssl_only.acl
        use_backend DomainKeep.com:80 if DomainKeep.com.acl
        use_backend gis if                         services80
        use_backend gis if                         appspro80
        use_backend check if                     check80
#      use_backend webqa if                    webqa
        use_backend webdev if                  webdev
        use_backend webstage if                webstage


        default_backend DomainKeep.com:80
#      default_backend web.domain.com:80


#############################
frontend https_in


        bind :443 ssl crt /etc/ssl/WILDCARD.domain.com.2014.chain.pem crt /etc/ssl/DomainKeep.com.2014.chain.pem crt /etc/ssl/WILDCARD.domain2.com.2014.chain.pem
        timeout client 600000
        capture request header Host     len 100
        capture request header Referer  len 100
        tcp-request content reject if { src -f /etc/haproxy/blacklist.lst }


#      For non-SNI matching.
#       acl DomainKeep.com:443 hdr_dom(host) -i DomainKeep.com
#       acl webqa hdr_dom(host) -i                      webqa
#       acl webdev hdr_dom(host) -i                    webdev
#       acl webstage hdr_dom(host) -i                  webstage


#      For SNI matching, use the "{ ssl_fc_sni..." lines, otherwise use the other lines.
#      use_backend DomainKeep.com:80 if DomainKeep.com:443
        use_backend DomainKeep.com:80 if { ssl_fc_sni DomainKeep.com }
#      use_backend webqa if                    webqa
#      use_backend webqa if                    { ssl_fc_sni webqa.domain2.com }
#      use_backend webdev if                  webdev
        use_backend webdev if                  { ssl_fc_sni webdev.domain2.com }
#      use_backend webstage if                webstage
        use_backend webstage if                { ssl_fc_sni webstage.domain2.com }


#      default_backend web.domain.com:80
#############################
frontend http_4443


        bind :4443
        timeout client 600000
        reqadd X-Forwarded-Proto:https
        reqadd X-Forwarded-Port:443
        capture request header Host     len 100
        capture request header Referer  len 100
        capture request header If-Modified-Since        len 100


        acl ssl_only url_sub /stuff/login.aspx url_sub /order/stuff/login.aspx url_sub /login url_sub /stuff url_sub buynow url_sub .ashx url_sub .css url_sub .js url_sub .jpg url_sub .png url_sub .gif url_sub /order/stuff/junk url_sub .axd


        acl heck443 hdr_dom(host) -i        check
        acl wsvcstest443 hdr_dom(host) -i wsvcstest
        acl wsvcs443 hdr_dom(host) -i      wsvcs
        acl contain2 url_sub                     /stuff/login.aspx


        redirect code 301 prefix [http://web.domain.com](http://web.domain.com) if                      !ssl_only
        redirect location [https://web.domain.com/order/stuff/login.aspx](https://web.domain.com/order/stuff/login.aspx) if contain2


        use_backend check if  check443
        use_backend wsvcs if wsvcs443
        use_backend wsvcs if wsvcstest443


#      default_backend web.domain.com:80


#############################
frontend http_8080


        bind :8080
        timeout client 600000
        capture request header Host     len 100
        capture request header Referer  len 100


        acl services8080 hdr_dom(host) -i services
        acl appspro8080 hdr_dom(host) -i appspro


        use_backend mapserver if services8080 or appspro8080


#############################
frontend http_6080


        bind :6080
        timeout client 600000
        capture request header Host     len 100
        capture request header Referer  len 100


        default_backend arc


#############################
frontend http_7080


        bind :7080
        timeout client 600000
        capture request header Host     len 100
        capture request header Referer  len 100


        default_backend a7080


########################## BACK ENDs SECTION ######################
backend web.domain.com:80


        timeout server 600000
        balance roundrobin
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server webproawvc1 172.16.0.188:80 check
        server webproawvd1 172.16.0.102:80 check
        server webproawvd2 172.16.0.79:80 check
        server webproawvd3 172.16.0.144:80 check


backend web2


        timeout server 600000
        balance roundrobin
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server webproawvc2 172.16.0.228:80 check
        server webproawvc3 172.16.0.23:80 check


# backend webqa
#
#       timeout server 600000
#       balance roundrobin
#       stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
#       server webqaawvc1 172.16.0.97:80 check


backend webdev


        timeout server 600000
        balance roundrobin
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server webdevawvd1 172.16.0.135:80 check


backend webstage


        timeout server 600000
        balance roundrobin
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server webstgawvc1 172.16.0.121:80 check


backend g80


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server appsproawvc1 172.16.0.238:80 check
        server appsproawvd1 172.16.0.171:80 check


backend g8080


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server appsproawvc1 172.16.0.238:8080 check
        server appsproawvd1 172.16.0.171:8080 check


backend go


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server appsproawvc2 172.16.0.78:80 check
        server appsproawvc3 172.16.0.245:80 check
        server appsproawvd2 172.16.0.153:80 check


backend mapserver


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server appsproawvc2 172.16.0.78:8080 check
        server appsproawvc3 172.16.0.245:8080 check
        server appsproawvd2 172.16.0.153:8080 check


backend arc


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server appsproawvc1 172.16.0.238:6080 check
        server appsproawvd1 172.16.0.171:6080 check


backend g7080


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server appsproawvc1 172.16.0.238:7080 check
        server appsproawvd1 172.16.0.171:7080 check


backend wsvcs


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server appsproawvc1 172.16.0.206:80 check
        server appsproawvd1 172.16.0.42:80 check


backend check


        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
#      server maps01vm 172.16.0.153:80 check
#      server mapsproawvc1 172.16.0.239:80 check


backend DomainKeep.com:80
        timeout server 600000
        balance source
        stick-table     type ip size 200k expire 30s store conn_cur peers haproxypeers
        server NETProAWVC1 172.16.0.170:80 check


########################## PEERs SECTION ######################
peers haproxypeers
        peer LB1 172.16.0.117:1024
        peer LB2 172.16.0.210:1024
###############################################################

---

