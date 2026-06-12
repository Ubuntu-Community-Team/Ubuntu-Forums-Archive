---
title: "Ubuntu Server 13.10. Squid 3.3.8.  WARNING: external ACL 'memberof' queue overload"
date: 2013-11-11
forum: Server Platforms
---

### Post by Roswebnet on 2013-11-11
Hi everyone
  
  During configuration of LDAP basic and group authentication methods by Squid, a came across this error (/var/log/squid3/cache.log):
  
  ```
WARNING: external ACL 'memberof' queue overload. Request rejected 'administrator InternetAccess'.
```
  
  For basic authentication I use following piece of code:
  
  ```

  auth_param basic program /usr/lib/squid3/basic_ldap_auth -P -R -u cn -b "cn=Users,dc=dot,dc=lan" ubuntu.dot.lan
  auth_param basic realm ubuntu.dot.lan
```
  
  The test shows:
  
  Administrator Pa77w0rd
  
  OK.
  
  For LDAP groups I use this:
  
  ```

  external_acl_type memberof %LOGIN /usr/lib/squid3/ext_ldap_group_acl -P -R -K -b "dc=dot,dc=lan" -f "(&(cn=%v)(memberOf=cn=%a,cn=Users,dc=dot,dc=lan))" -D [EMAIL="nslcd-service@dot.lan"]nslcd-service@dot.lan[/EMAIL] -w "Pa77w0rd" -h ubuntu.dot.lan
  
```
  
  
  The test shows:
  
  Administrator InternetAccess
  
  OK
  
  
  My ACL list has following rules:
  ```

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
  acl LDAP_Auth proxy_auth REQUIRED
  acl ClientNet src 192.168.1.135
  acl Block_site url_regex -i fb vk youtube
  acl InetAccess external memberof InternetAccess
  
```
  
  And my Access/deny rules are:
  ```

  http_access allow localhost manager
  http_access deny manager
  http_access deny !Safe_ports
  http_access deny CONNECT !SSL_ports
  http_access allow localhost
  http_access deny Block_site
  http_access allow InetAccess
  http_access deny !LDAP_Auth
  http_access allow ClientNet
  http_access deny all
  
```
  
  Where is the problem? How to solve it?
  
  Thank you.

---

### Post by Roswebnet on 2013-11-13
I found a solution!
    
   Problem was with IPv6.
   When squid tries to run the helper he asks IPv6, which I have disabled.  Therefore, in logs appears following line of code:
   WARNING: Cannot run '/usr/lib/squid3/ext_ldap_group_acl' process.
    
   As far as I have good understanding of the process, squid do not stop to  restart the helper. Therefore in logs appears:
   WARNING: external ACL 'memberof' queue overload. Request rejected  'administrator InternetAccess'
    
   The solution is to put the ipv4 flag in front of %LOGIN just like  this:
    
   ```
external_acl_type memberof ipv4 %LOGIN /usr/lib/squid3/ext_ldap_group_acl  -P -R -K -b "dc=dot,dc=lan" -f  "(&(cn=%v)(memberOf=cn=%g,cn=Users,dc=dot,dc=lan))" -D [EMAIL="nslcd-service@dot.lan"]nslcd-service@dot.lan[/EMAIL]  -w "Pa77w0rd" -h ubuntu.dot.lan
```
    
   references:
   [http://squid-web-proxy-cache.1019090.n4.nabble.com/external-acl-td4662446.html~](http://squid-web-proxy-cache.1019090.n4.nabble.com/external-acl-td4662446.html~)
   [http://squid-web-proxy-cache.1019090.n4.nabble.com/Starting-helpers-with-ipv6-disabled-td4660978.html](http://squid-web-proxy-cache.1019090.n4.nabble.com/Starting-helpers-with-ipv6-disabled-td4660978.html)

---

### Post by Damian_Caceres on 2014-10-14
Hi

You can spend the entire squid.conf? Because I can not get it to authenticate with my ad and watching it could see that I'm doing wrong 


greetings

---

