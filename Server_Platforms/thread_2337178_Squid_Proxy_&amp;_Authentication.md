---
title: "Squid Proxy &amp; Authentication"
date: 2016-09-15
forum: Server Platforms
---

### Post by slkamath on 2016-09-15
Hi,

I installed Ubuntu Server 14.04 LTS today and I am trying to configure Squid Proxy.

Squid Proxy also installed and asking user name & password. but I dont know where i have to create user name & password for this.

Also One more thing I have to configure is default internet should not work. it has to work for only those who have proxy authentication (user name & password).

Please help me.

Thanks in advance.

Lokesh Kamath

---

### Post by SeijiSensei on 2016-09-15
For authentication, read this: [http://stackoverflow.com/questions/3297196/how-to-set-up-a-squid-proxy-with-basic-username-and-password-authentication](http://stackoverflow.com/questions/3297196/how-to-set-up-a-squid-proxy-with-basic-username-and-password-authentication)

As for requiring people to use the proxy, it depends on how your network is configured.  I usually put the Squid box behind the egress router and make it the clients' default gateway. I use two network cards, one connected to the local network, and one connected to the router.  If you leave packet forwarding disabled as is the default (see /etc/sysctl.conf for details), then no traffic will leave the network except that passing through Squid.

---

### Post by slkamath on 2016-09-15
Thanks for your reply.

I tried that post earlier and i also tried creating user using the command 
sudo htpasswd -c /etc/squid3/passwords username_you_like

I created 2 user name & passwords when using the internet it asks proxy user name & password, If i give created user name & password it's not taking the created user name & password.

output of /etc/sysctl.conf is

net.ipv4.ip_forward=1

Default gateway is having proxy server. 

Eth0 is Wan IP
eth1 is Lan IP

Lokesh Kamath

---

### Post by SeijiSensei on 2016-09-15
Well, first, if you want to block outgoing traffic other than via the proxy, you need to set net.ipv4.ip_forward back to zero.

What do you see in /var/log/squid/access.log when you try to authenticate?

---

### Post by slkamath on 2016-09-15
I changed that settings to 0.

in /var/log/squid3/access.log

1473917616.896      0 163.172.135.224 TCP_DENIED/403 3631 GET http://vps306999.$ 1473919415.996      0 192.192.0.10 TCP_DENIED/403 4039 GET http://www.google.co$ 1473919416.051      0 192.192.0.10 TCP_DENIED/403 3789 GET http://www.squid-cac$ 1473919416.146      0 192.192.0.10 TCP_DENIED/403 3924 GET http://www.google.co$ 1473919416.174      0 192.192.0.10 TCP_DENIED/403 3998 GET http://www.google.co$ 1473919420.514      0 192.192.0.10 TCP_DENIED/403 4003 GET http://www.google.co$ 1473919420.545      0 192.192.0.10 TCP_DENIED/403 3789 GET http://www.squid-cac$ 1473920291.224      0 163.172.135.224 TCP_DENIED/403 3644 GET http://vps306999.$

Lokesh Kamath

---

### Post by SeijiSensei on 2016-09-15
There are lots of ways to get 403 DENIED errors that have nothing to do with authentication.  We need to see the contents of squid.conf.  However, before posting it here, please run the following command:
```
grep -v '^#' < squid.conf | grep -v '^$' > squid.conf.cleaned
```
and post the contents of squid.conf.cleaned inside [noparse]```

```[/noparse] tags.  That will remove all the extensive comments and blank lines in squid.conf.

---

### Post by slkamath on 2016-09-15
Output of 
**grep -v '^#' /etc/squid3/squid.conf | grep -v '^$' /etc/squid3/squid.conf.cleaned**
auth_param basic program /usr/lib/squid3/basic_ncsa_auth
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hour
auth_param basic casesensitive off
acl ncsa_users proxy_auth REQUIRED
http_access allow ncsa_users
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /usr/etc/passwd
auth_param basic realm Squid proxy-caching web server
acl password proxy_auth REQUIRED
acl network src 192.192.0.0/24
acl hours time S M T W T F S 9:00-19:00
acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
http_access allow network hours
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
acl user_auth proxy_auth REQUIRED
http_access allow user_auth
http_access deny all
http_port 8080 
http_port 8888 
http_port 3128
cache_dir ufs /var/spool/squid3 5120 16 256
refresh_pattern -i \.(gif|jpeg|jpg|png|)$ 3600	90%	43200
cache_dir ufs /var/spool/squid3 100 16 256
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .		0	20%	4320
cache_effective_user proxy
visible_hostname leinternetProxy
cache_effective_group proxy

---

### Post by SeijiSensei on 2016-09-15
```
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /usr/etc/passwd
```
Shouldn't this directive point to the file where the passwords are stored?  In your case that seems to be /etc/squid3/passwords based on this:
```
sudo htpasswd -c /etc/squid3/passwords username_you_like
```  

I doubt you even have a file called /usr/etc/passwd nor even a /usr/etc directory.

Have you tested everything else without authentication enabled?  If not, comment out anything having to do with authentication and see if Squid works correctly without it.  If so, then you know the problem lies in the authentication directives.

---

### Post by slkamath on 2016-09-16
Hi,

If I change this line net.ipv4.ip_forward=1 to net.ipv4.ip_forward=0 then internet is not working in any system. 

Also I changed 
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /usr/etc/passwd to

auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/passwords & created user name & password. 



Without squid in all the system internet is working. If I put proxy authentication then it's asking user name & password.

If I give created user name & password it's not taking.

I did few changes to squid.conf file

now if i give proxy authentication directly internet is working. it's not asking user name & password of proxy.

Current Output of squid.conf is

```
grep -v '^#' /etc/squid3/squid.conf | grep -v '^$' /etc/squid3/squid.conf.cleaned
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/squid_password
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hour
auth_param basic casesensitive off
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/passwords
auth_param basic realm Squid proxy-caching web server
acl ncsa_users proxy_auth REQUIRED
acl hours time M T W H F 9:00-17:00
acl network src 192.192.0.0/24
acl hours time S M T W T F S 9:00-19:00
acl RestrictedHost src 192.192.0.1
acl GoodSites dstdomain "/usr/local/etc/allowed-sites.squid"
acl BadSites  dstdomain "/usr/local/etc/restricted-sites.squid"
acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
http_access deny RestrictedHost
http_access allow network hours
http_access deny BadSites
http_access allow network hours GoodSites
http_access allow network
http_access allow ncsa_users
http_access allow ncsa_users hours
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all
http_port 8080 
http_port 8888 
http_port 3128
cache_dir ufs /var/spool/squid3 5120 16 256
refresh_pattern -i \.(gif|jpeg|jpg|png|)$ 3600	90%	43200
cache_dir ufs /var/spool/squid3 100 16 256
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .		0	20%	4320
cache_effective_user proxy
visible_hostname leinternetProxy
cache_effective_group proxy
```

Le me know where i went wrong. :(

---

### Post by SeijiSensei on 2016-09-16
> **slkamath said:**
> If I change this line net.ipv4.ip_forward=1 to net.ipv4.ip_forward=0 then internet is not working in any system.
Isn't that what you want?  Allowing only browsing via Squid and no other Internet connections?  You should still be able to connect to the Internet from the Squid box itself.

Squid doesn't require packet forwarding.  It accepts in the incoming URL request, makes its own request to the remote site, then sends the results back to the client workstation.

I'm going to be away for a few days, so someone else will have to pick up the baton here.

---

### Post by slkamath on 2016-09-16
Thank you so much.

Squid Proxy authentication is keep on asking user name & password. it's not taking the created user name & password.

---

### Post by slkamath on 2016-09-19
Can anyone help me to solve this?

If I change this line net.ipv4.ip_forward=1 to net.ipv4.ip_forward=0 internet & mails are not working. 

Squid Proxy authentication is keep on asking user name & password. it's not taking the created user name & password.

---

### Post by slkamath on 2016-09-19
Now I did some changes in my settings.

net.ipv4.ip_forward=1 to net.ipv4.ip_forward=0

Internet is working only for proxy users. Now I want to exclude 10 IP address from squid proxy(10 IP address can access anything to everything) How can I do this settings?

Lokesh Kamath

---

### Post by slkamath on 2016-09-19
One more issue what we are facing is
after changing this net.ipv4.ip_forward=1 to net.ipv4.ip_forward=0 
our mails are not working. If i do the telnet mail.laxmielectronics.com 587
telnet: could not resolve mail.laxmielectronics.com/587: Temporary failure in name resolution
So Please guide me to come out from this issue.

Current Output of 
```
grep -v '^#' < squid.conf | grep -v '^$' > squid.conf.cleanedauth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/passwords
auth_param basic children 5
auth_param basic realm LAXMI ELECTRONICS moulds & precision engg pvt ltd - Proxy Server
auth_param basic credentialsttl 2 hour
auth_param basic casesensitive off
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/passwords
acl users src 192.192.0.50-192.192.0.200/24
acl ncsausers proxy_auth REQUIRED
acl RestrictedHost src 192.192.0.1
acl GoodSites dstdomain "/usr/local/etc/allowed-sites.squid"
acl BadSites dstdomain "/usr/local/etc/restricted-sites.squid"
acl SSL_ports port 443
acl Safe_ports port 80 # http
acl safe_ports port 587 #SMTP
acl safe_ports port 465 #SMTP
acl safe_ports port 110 #POP
acl safe_ports port 143 #IMAP
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
acl ncsa_users proxy_auth REQUIRED
acl ncsausers proxy_auth REQUIRED
http_access allow ncsa_users
http_access allow all ncsausers
http_access allow users
http_access deny all
http_access deny RestrictedHost
http_access deny BadSites
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all
http_port 3128
cache_dir ufs /var/spool/squid3 5120 16 256
refresh_pattern -i \.(gif|jpeg|jpg|png|)$ 3600    90%    43200
cache_dir ufs /var/spool/squid3 100 16 256
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320
cache_effective_user proxy
visible_hostname leinternetProxy
cache_effective_group proxy
```

---

### Post by slkamath on 2016-09-22
Please someone help me.

Thanks in advance.

---

### Post by SeijiSensei on 2016-09-22
> telnet: could not resolve mail.laxmielectronics.com/587: Temporary failure in name resolution


That's a DNS problem, not a Squid problem.  Can you connect with telnet if you use the server's IP address?

---

### Post by slkamath on 2016-09-23
I think you are back. Thanks.

Through IP Address telnet is working fine.

---

### Post by SeijiSensei on 2016-09-23
So you need to fix your DNS.  It has to be internal to your network.  I can resolve "mail.laxmielectronics.com" from outside.

---

### Post by slkamath on 2016-09-23
Ok.

So you are suggesting me to change sysctl.conf
net.ipv4.ip_forward=1 to net.ipv4.ip_forward=0

I have to do any other changes to work internet & mails? because if i change net.ipv4.ip_forward=1 to net.ipv4.ip_forward=0 mail & internet wont work.

---

### Post by SeijiSensei on 2016-09-23
You seem to have conflicting objectives, and the way they are stated leaves them pretty unclear.

First, you said you wanted to force all machines behind the proxy server to use Squid and not have any other connections to the Internet.  Setting ip_forward=0 and configuring Squid correctly will do that.  But now it appears you actually do want to let machines behind the proxy connect to remote machines.  To do that requires enabling forwarding and then writing a variety of iptables rules to limit access to just the locations to which you want to connect.  You could have rules like
```

# send mail via the submission port (587)
iptables -A INPUT -p tcp -s 192.168.1.0/24 -d 162.251.80.14 --dport 587 -j ACCEPT
# retrieve mail via IMAP
iptables -A INPUT -p tcp -s 192.168.1.0/24 -d 162.251.80.14 --dport 143 -j ACCEPT
# allow traffic on local network
iptables -A INPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT
# block everything else from local network
iptables -A INPUT -s 192.168.1.0/24 -j REJECT

```

We've moved way beyond a simple answer to a simple query because, frankly, I just don't think you have enough knowledge and experience to configure something as complex as what you're trying to do.  You really need to consider hiring a knowledgeable and experienced consultant to work with you on evaluating what exactly your needs are and what the best methods are to accomplish them.

---

### Post by slkamath on 2016-09-23
Thanks for your suggestion.

I dont have enough knowledge on this. we have given these things to out sourcing initially (approximately 7years). Now Hardware failed and they are also not ready to help, so i stared installing and all other things.

Once again many thanks.

---

### Post by slkamath on 2016-09-28
Hi

Good Evening.

My problem has solved and the requirement what i have posted is working fine.

I will thank one & all who is part of my problem solving process.

:):):)

Lokesh Kamath

---

