---
title: "Squid None Aborted problem"
date: 2015-11-06
forum: Server Platforms
---

### Post by secoonder on 2015-11-06
I am using squid 3.5.8 and ubuntu 14.04.3 LTS...
 always getting NONE_ABORTED/000 or TCP_MISS_ABORTED/000. My internal network gets slow after it. 

When i see cache.log...
root@seco:/home/seckin# tailf /var/log/squid/cache.log 
[B]2015/11/08 17:54:02 kid1| ERROR: No forward-proxy ports configured.
2015/11/08 17:54:02 kid1| ERROR: No forward-proxy ports configured.
2015/11/08 17:54:37 kid1| ERROR: No forward-proxy ports configured.
2015/11/08 17:54:37 kid1| ERROR: No forward-proxy ports configured.[/B]

What is the problem.can you help me ?
thank you very much

---

### Post by secoonder on 2015-11-07
Hi,

any suggestion on the above post?

Thanks
Seckin

---

### Post by SeijiSensei on 2015-11-07
Did you Google for that error string "TCP_MISS_ABORTED/000" and happen to read this: [http://superuser.com/questions/909593/basic-proxy-server-config-fails-for-some-websites-tcp-miss-and-tcp-miss-aborted](http://superuser.com/questions/909593/basic-proxy-server-config-fails-for-some-websites-tcp-miss-and-tcp-miss-aborted)

Are you using IPv6?  Does your provider?  If so, you might try the recommendation in the last reply in that thread, to add

```
dns_v4_first on
```

to squid.conf and restart the proxy.  Even if you're not sure about IPv6, it won't hurt to try that suggestion.

---

### Post by secoonder on 2015-11-08
Thank you for your answer.
we are not using ipv6.
i added 
"dns_v4_first on" in the squid.conf and restart the proxy.Unfortunately,the problem is not solved...
root@seco:/home/seckin# tailf /var/log/squid/access.log
1446998020.074   1747 192.168.4.52 **TAG_NONE_ABORTED/000 0** POST [http://gn.symcd.com/](http://gn.symcd.com/) **- HIER_NONE/- -**
1446998020.829   2203 192.168.4.52** TAG_NONE_ABORTED/000 0** POST [http://vassg142.ocsp.omniroot.com/](http://vassg142.ocsp.omniroot.com/) - **HIER_NONE/- -**
1446998020.829   2203 192.168.4.52 **TAG_NONE_ABORTED/000 0** POST [http://vassg142.ocsp.omniroot.com/](http://vassg142.ocsp.omniroot.com/) - [B]HIER_NONE/- -
[/B]
When i saw cache.log...
root@seco:/home/seckin# tailf /var/log/squid/cache.log 
[B]2015/11/08 17:54:02 kid1| ERROR: No forward-proxy ports configured.
2015/11/08 17:54:02 kid1| ERROR: No forward-proxy ports configured.
2015/11/08 17:54:37 kid1| ERROR: No forward-proxy ports configured.
2015/11/08 17:54:37 kid1| ERROR: No forward-proxy ports configured.



[/B]i read a lot of documents.
"""you should changed these lines:""""

  *http_port 3128 ***transparent **
  *to *
  *http_port 3128** intercept ***
  [I]http_port **3129 **


[/I]i changed them in squid.conf
# General
*http_port 3128** intercept ***
  [I]http_port **3129 **
[/I]visible_hostname Proxy
forwarded_for delete
via on
dns_v4_first on
acl seckin src 192.168.4.0/24
http_access allow seckin

i  **did not** take an "[I]**No forward-proxy ports configured." **error.
"cache.log" is clear.

But i took an same error in access.log
root@seco:/home/seckin# tailf /var/log/squid/access.log
1446998020.074   7 192.168.4.52 **TAG_NONE_ABORTED/000 0** POST [http://spor.mynet.com]("http://gn.symcd.com/")**- HIER_NONE/- -**
1446998020.829 7 192.168.4.52** TAG_NONE_ABORTED/000 0** POST [http://spor.mynet.com/]("http://vassg142.ocsp.omniroot.com/") - [B]HIER_NONE/- -.

[/B][/I]And My internal network is very slow because of this problem.

My ubuntu Version is 14.04.3 LTS
Squid Version is 3.5.8

could  the bug of ubuntu 14.04 ? May be ?


  

Any ideas?

Thank you very much

---

### Post by SeijiSensei on 2015-11-08
From what I read while skimming the discussions that Google search brought up, the bug might be in Squid itself.  I have a client where we run Squid, but we're using 3.1.23 on CentOS 6.6.  We don't have any of those "ABORTED" errors in access.log.  We're running in transparent mode with 
```
http_port 3128 transparent
```
in squid.conf and this iptables rule:
```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 10.1.2.0/24 --destination-port 80
```
where 10.1.2.0/24 is the address of the LAN network.  We handle HTTPS traffic outside of squid.  At some point we might implement ssl_bump, but we would need to install certificates in all the client browsers to make that work transparently.

---

### Post by secoonder on 2015-11-11
Ok Thank you SeijiSensei.

&#304; am installed 12.04 and squid 3.1
The problem is solved

---

### Post by secoonder on 2016-02-28
Hello again.
As a result of long study i solved the problem.i installed ubuntu 14.04 and squid 3.5.
i added tcp_outgoing_address 1.2.3.4(My outbound interface ip).The problem is solved.
and i added
http_port 3128 transparent ssl-bump generate-host-certificates=on dynamic_cert_mem_cache_size=4MB key=/etc/mydlp/ssl/private.pem cert=/etc/mydlp/ssl/public.pem
http_port 3129 transparent ssl-bump generate-host-certificates=on dynamic_cert_mem_cache_size=4MB key=/etc/mydlp/ssl/private.pem cert=/etc/mydlp/ssl/public.pem
and i installed the certifica to clients.
https redirected succesfully on my proxy server.But i took en error when the client requested https.(http is no problem)
in access.log 
[B][I]2016/02/28 16:02:15| clientNegotiateSSL: Error negotiating SSL connection on FD 16   
2016/02/28 16:02:15| clientNegotiateSSL: Error negotiating SSL connection on FD 16  
2016/02/28 16:02:15| clientNegotiateSSL: Error negotiating SSL connection on FD 16[/I][/B]

Can you help me? Thank you

---

