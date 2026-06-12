---
title: "Help: Simple setup squid to authenticate web browsers/users"
date: 2011-03-09
forum: Server Platforms
---

### Post by Demented ZA on 2011-03-09
Can anyone show me in the direction or tutorial for an easy guide or introduction to squid access controls?

I just need users to type in username and password in order to browse web, thats it.

I searched with Google, but nothing for my needs.

---

### Post by SeijiSensei on 2011-03-10
Have you read the information about how to configure authentication in squid.conf?  Particularly the section that begins with

#  TAG: auth_param
#       This is used to define parameters for the various authentication
#       schemes supported by Squid.

How about [http://wiki.squid-cache.org/Features/Authentication?highlight=%28faqlisted.yes%29](http://wiki.squid-cache.org/Features/Authentication?highlight=%28faqlisted.yes%29) from the Squid web site?

---

### Post by Demented ZA on 2011-03-10
Thank you.

I have and I was hoping for something simpler, because for some or other reason my brain doesn't want to wrap around all that.

I think its cause my mind goes to a different place halfway through the first paragraph. I suppose I'm just tired.

I read it again just now, and I think I understand it a little better. I suppose I'm going to have have to print it out and go over it when my mind isn't so taxed, or just go over and over until I understand it.

I was also looking for some examples, but I think I'll try first, and then post back here, probably tomorrow or Saturday.

---

### Post by Demented ZA on 2011-03-12
Ok, well I've been playing around and I got my proxy server working as a normal proxy server without authentication not transparent/interception mode. As I understand, interception mode cannot be used in conjunction with authentication.

I am using a basic ACL to allow a range of IP's and that answers my first question: How do I allow managers access without having them enter username and password.

Now, on to User authentication. From the Squid Wiki, I understand that I need to choose an authentication scheme. Among the options are:


[LIST]
[*]LDAP: Uses the Lightweight Directory Access Protocol 
[*]NCSA: Uses an NCSA-style username and password file. 
[*]MSNT: Uses a Windows NT authentication domain. 
[*]PAM: Uses the Unix Pluggable Authentication Modules scheme. 
[*]SMB: Uses a SMB server like Windows NT or Samba. 
[*]getpwam: Uses the old-fashioned Unix password file. 
[*]SASL: Uses SALS libraries. 
[*]mswin_sspi: Windows native authenticator 
[*]YP: Uses the NIS database
[/LIST]
I honestly don't know how to decide on an authentication scheme? Clients will be running a mix of Windows XP and Windows 7.

I suppose using the unix password backend would be easy to set up and manage, although, it might be more secure to seperate e-mail authentication from internet/proxy authentication. What are your thoughts?

---

### Post by Demented ZA on 2011-03-12
Right. I decided to go with NCSA Authentication.

My proxy authentication is working for users : A user opens his browser, types in [www.domain.com]("http://www.domain.com"), the browser asks for password, after user typed in his credentials, the page is displayed.

What I cannot seem to get working is to allow the computer with ip of 10.10.10.105 to connect without having to type in a username and password.

This is my squid configuration file so far:
```
########################################### Squid Settings #############################################################

# error_directory /usr/share/squid/errors/en

coredump_dir /var/spool/squid

hosts_file /etc/hosts

http_port 8080


########################################### Squid Authentication settings #########################################

auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/passwd
auth_param basic children 5
auth_param basic realm Company Server Proxy
auth_param basic credentialsttl 2 hour
auth_param basic casesensitive off


############################################ Logfile Options ###########################################################

logformat squid %ts.%03tu %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt
#logformat squidmime %ts.%03tu %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt [%>h] [%<h]
#logformat common %>a %ui %un [%tl] "%rm %ru HTTP/%rv" %Hs %<st %Ss:%Sh
#logformat combined %>a %ui %un [%tl] "%rm %ru HTTP/%rv" %Hs %<st "%{Referer}>h" "%{User-Agent}>h" %Ss:%Sh

access_log /var/log/squid/access.log squid

logfile_daemon /usr/lib/squid/logfile-daemon

cache_log /var/log/squid/cache.log

cache_store_log /var/log/squid/store.log

emulate_httpd_log off


######################################### Access Control Lists #########################################################


acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32

#acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
#acl apache rep_header Server ^Apache


acl CONNECT method CONNECT
#acl purge method PURGE

###### Authentication ########

acl ncsa_users proxy_auth REQUIRED

###### Network ###############

acl localnet src 10.10.10.1-10.10.10.254/24


###### SSL Ports #############

acl SSL_ports port 443 # https
acl SSL_ports port 563 # snews
acl SSL_ports port 873 # rsync

##### Safe Ports #############

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
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl Joe src 10.10.10.105/24


###################################### Access Control Rules ##########################################################

# icp_access allow localnet
# icp_access deny all

#http_access allow localnet
http_access allow Joe !all
#http_access allow manager localhost
#http_access deny manager
#http_access allow purge localhost
http_access allow ncsa_users
#http_access deny purge
http_access allow SSL_ports
#http_access allow localhost
#http_access allow localnet
http_access allow Safe_ports
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all
# broken_vary_encoding allow apache






```

---

### Post by SeijiSensei on 2011-03-12
> acl Joe src 10.10.10.105/24

Take the /24 off the end.  You want to refer to a single IP address, not an IP subnet.

> http_access allow Joe !all

Shouldn't that be just "all" and not "!all"?

---

### Post by Demented ZA on 2011-03-13
> **SeijiSensei said:**
> Take the /24 off the end.  You want to refer to a single IP address, not an IP subnet.

Hmmm.... I didn't think of that. :-k


Shouldn't that be just "all" and not "!all"?

I changed it to
```
http access allow Joe all
```

It seems to be working now. PC with ip ending in 105 uses cache without username/password. The other PC requires a password. Perfect.

I still don't quite get the logic between the

http_access allow/deny <acl_name1> **<acl_name2>/!<acl_name3> **

I understand that ! means inverse/not. I just don't understand the expression?

I.e: 

http_access allow Joe (with ip 10.10.10.105)   **<and /or?>**   all (Match all ACL's)

How does the logic of that statement work?

I still need to get the SSL connect statement to work. I understand that SSL can't be cached as it is encrypted, so then the proxy should allow a CONNECT function?

I can parse ssl through the firewall, but then I have no ACL control over it, and I can't monitor usage stats for ssl connections.

Thank you so much for your help!

---

### Post by HermanAB on 2011-03-13
Howdy,

Here is another guide, scroll down to 'Squid Authentication':
[http://www.aeronetworks.ca/howtos/squidguard-howto.html](http://www.aeronetworks.ca/howtos/squidguard-howto.html)

---

### Post by Demented ZA on 2011-03-13
Thank you for your input. That basically yeilds the exact same result I have here. A least for the authentication part.

I'm just trying to make sense of the expressions used in squid. Some of it I get, but I didn't understand why I had to include the acl: ALL and not !ALL, etc.

I got my SSL working. Basically the configuration is fine. I was using Firefox on this particular machine and Firefox gives you the oppertunity to set HTTP and SSL proxies seperately. Internet Explorer worked all along, but I never noticed because I don't like it much.

So Basically squid is doing exactly what its supposed to be doing. i would just like to understand it better :D

> **HermanAB said:**
> Howdy,

Here is another guide, scroll down to 'Squid Authentication':
[http://www.aeronetworks.ca/howtos/squidguard-howto.html](http://www.aeronetworks.ca/howtos/squidguard-howto.html)

---

### Post by SeijiSensei on 2011-03-13
```
http access allow Joe all
```

is an example of an access rule that uses an AND connector.  The rule is true when both Joe and all are true.  That permits Joe to go everywhere.  "Joe !all" is probably the equivalent of "http_access deny Joe".

---

### Post by Demented ZA on 2011-03-17
That helps a lot. My confusion came in due to the fact that I was looking for an "or" type of logic (authentication or IP), but I suppose "or" would be vertically across the rules, and the rules are checked in sequence, and matched to the first rule it finds that is true?

Thanks for your insight.

---

### Post by SeijiSensei on 2011-03-17
Yes, OR's depend on the order of http_access rules.

---

