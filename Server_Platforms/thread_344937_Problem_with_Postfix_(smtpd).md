---
title: "Problem with Postfix (smtpd)"
date: 2007-01-23
forum: Server Platforms
---

### Post by nmarmol on 2007-01-23
Hello,
I've installed ubuntu server.  I opened some service like sshd.  But  with postfix i got some problems. 

when I execute a nmap command in my internal network I received the following response

root@ubuntu-test:/etc/postfix# nmap localhost

Starting Nmap 4.10 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-01-24 00:29 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 1677 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
25/tcp open  smtp

Nmap finished: 1 IP address (1 host up) scanned in 0.157 seconds

But when i executed the same command from an external network the repose if the following:

Starting Nmap 4.00 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-01-23 18:17 VET
Interesting ports on adsl-200-88.tricom.net (200.42.200.88):
(The 1663 ports scanned but not shown below are in state: closed)
PORT     STATE    SERVICE
22/tcp   open     ssh
**25/tcp   filtered smtp**
135/tcp  filtered msrpc
136/tcp  filtered profile
137/tcp  filtered netbios-ns
138/tcp  filtered netbios-dgm
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
1080/tcp filtered socks

Nmap finished: 1 IP address (1 host up) scanned in 15.486 seconds


As you see the smtp service is filtered.  Outside my lan I cannot connect.

I want to open this service(smtp).  What Can I do?  Anyone Can help?

Best regards
nelson

---

### Post by jtc on 2007-01-23
I'd say your ISP is blocking port 25.

Those ports listed as filtered are typicall ports to be blocked.

---

### Post by nmarmol on 2007-01-23
I've called my ISP provider.  They told me the port 25 is open.

I trace the server with the port and I verified that port is opened.

grproxy:~ # **traceroute -p 25 200.42.200.88**
traceroute to 200.42.200.88 (200.42.200.88), 30 hops max, 40 byte packets
 1  10.0.0.1 (10.0.0.1)  0.653 ms   1.169 ms   0.859 ms
 2  209.58.3.172 (209.58.3.172)  19.943 ms   22.534 ms   23.153 ms
 3  192.168.103.1 (192.168.103.1)  11.015 ms   11.406 ms   11.515 ms
 4  172.22.220.1 (172.22.220.1)  11.493 ms   11.432 ms   11.380 ms
 5  172.22.0.154 (172.22.0.154)  14.598 ms   12.428 ms   13.062 ms
 6  172.22.0.97 (172.22.0.97)  13.048 ms   12.888 ms   15.508 ms
 7  172.22.0.98 (172.22.0.98)  16.352 ms   14.042 ms   11.798 ms
 8  pri-028-b3.codetel.net.do (196.3.74.28)  11.920 ms   12.425 ms   18.506 ms
 9  Leased-Lines-208-117.tricom.net (200.42.208.117)  100.559 ms   102.371 ms   100.649 ms
10  200.42.213.133 (200.42.213.133)  95.902 ms   53.302 ms   88.900 ms
11  adsl-200-88.tricom.net (200.42.200.88)  92.648 ms   90.520 ms   90.018 ms


Any Suggestions?

Best regards
Nelson

---

### Post by jtc on 2007-01-23
Well, that filterd status still gives me association of something blocking instead of postfix choosing not to respond. You'r refering to your internal network. Does that meen you have more then one computer (the one running postfix) and that they are sharing their connection through a router? If so, have your tried nmap from another local computer instead of just running nmap on localhost? If there is a router, is it told to forward port25 to the right internal ip-nummer?

Unless the above is the case, we can also take a look at postfix. What value does the line *inet_interfaces* have in the file /etc/postfix/main.cf ?

---

### Post by nmarmol on 2007-01-23
When I spoke about may internal lan I want to say that the machine is a server with a public ip.  Inside my lan the service works.  But if I accessed from internet it give me time out.

I want access that service from internet.

This is my configuration:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = multicentrolasirena.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = ubuntu-test, multicentrolasirena.com, localhost.multicentrolasirena.com, localhost
relayhost =
mynetworks = host 127.0.0.0/8 10.0.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
**inet_interfaces = all**
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination


best regards
nelson

---

### Post by jtc on 2007-01-23
I have really no idea what is blocking its port 25, but I'm pretty sure it isn't postfix doing. The line "inet_interfaces = all" tells postfix to listen to all network interfaces. Neither can I find anything else in your main.cf which would restrict its listening.

Well, I do find one small error. There is a space inside your "reject _unauth_destination" which shouldn't be there. Still, I don't think that is the issue here.

---

### Post by jtc on 2007-01-23
> **nmarmol said:**
> 
grproxy:~ # **traceroute -p 25 200.42.200.88**


...and by the way, that tell traceroute to use the UDP-port 25. Smtp uses TCP.

---

### Post by chrisfay on 2007-01-23
Try:

telnet 68.32.218.210 25

If you get a response you can be relatively sure your ISP does not filter your port 25. Most will block it both out and inbound so an outbound connection should prove it's open.

You could always add something like:

```
9923      inet  n       -       n       -       -       smtpd
```

... somewhere in your /etc/postfix/master.cf file and try connecting on port 9923 instead. (make sure and restart postfix) If you are successful on a non-standard port, then you know you have some port 25 issue. 

> If there is a router, is it told to forward port25 to the right internal ip-nummer?

I second this... Have you given your server a static LAN IP and correctly forwarded the port?

---

