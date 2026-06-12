---
title: "Apache2 &amp; Ddclient"
date: 2008-06-16
forum: Server Platforms
---

### Post by Nitewalker on 2008-06-16
I can't see my site from the WAN unless they enter the IP address. If you enter smj2.homeip.net it doesn't load, but if you put in the current listed IP address it does. I am using Ubuntu 8.04, Apache2 Web Server, and ddclient configured per suggested conf file from dyndns for my site. I have a Dlink 624 wireless router for my wirless laptop and the Web Server is hook to it thru the DSL modem? 2nd part of question is do I have to install SSL to get the dns service to work.I have read about all I can and still cant' get it to work, any assistance would sure be helpful:confused:

---

### Post by firecat53 on 2008-06-16
You will need to forward port 80 (and 443 if you use ssl) from your router to your server. There should be a page on your router configuration for port forwarding. Public port would be 80 -- private port also 80 and private ip would be the local ip of your server on your network.

Good luck!
Scott

---

### Post by Nitewalker on 2008-06-16
I do have port 80 open on my router along with 22 and 5900, and have checked them and they are all open.  Haven't open 443 yet as I am still trying to find out if I have to run SSL with dyndns & Ddclient.

---

### Post by heebus on 2008-06-16
Does that hostname resolve to your IP address?  If you don't have auto-updating turned on inside your router and the IP has changed, the DDNS may need updating.

---

### Post by Nitewalker on 2008-06-16
if I enter the url it just runs and doesn't connect.  I am using a Dlink-624 wireless router and have enabled the DDNS feature.

Is there some other modules I need to install besides Apache2 & Ddclinet?  

When I  run "sudo ddclient -dameon -verbose" it says at the end something about an fatal error:

nitewalker@smj2:~$ sudo ddclient -daemon=0 -verbose
CONNECT:  checkip.dyndns.com
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: checkip.dyndns.com
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Content-Type: text/html
RECEIVE:  Server: DynDNS-CheckIP/1.0
RECEIVE:  Connection: close
RECEIVE:  Cache-Control: no-cache
RECEIVE:  Pragma: no-cache
RECEIVE:  Content-Length: 105
RECEIVE:  
RECEIVE:  <html><head><title>Current IP Check</title></head><body>Current IP Address: 72.160.31.250</body></html>
INFO:     forcing updating smj2.homeip. because no cached entry exists.
INFO:     setting IP address to 72.160.31.250 for smj2.homeip.
UPDATE:   updating smj2.homeip.
FATAL:    Error loading the Perl module IO::Socket::SSL needed for SSL connect.
FATAL:     On Debian, the package libio-socket-ssl-perl must be installed.
Can't exec "sendmail": No such file or directory at /usr/sbin/ddclient line 1346.
ddclient: cannot execute command | sendmail -oi root.
nitewalker@smj2:~$

---

### Post by firecat53 on 2008-06-17
Have you installed yet the two packages it mentioned in the error report:  
libio-socket-ssl-perl and sendmail?

I checked, and both are in the repositories.

Scott

---

### Post by Nitewalker on 2008-06-18
No I have installed them, thanks for bringing it to my attention, I will do so and retry and get back with the results, thanks again.

---

### Post by Nitewalker on 2008-06-18
I added the 2 missing files as suggested and still can't connect to site using URL from the WAN, but works if I enter the IP address.  Everything works from within my LAN.  The address that is shown in report from daemon=0 -verbose is current address.  Not sure of what they mean by "Not fully qualifed Domain".

nitewalker@smj2:/etc/ddclient$ sudo ddclient -daemon=0 -verbose
CONNECT:  checkip.dyndns.com
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: checkip.dyndns.com
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Content-Type: text/html
RECEIVE:  Server: DynDNS-CheckIP/1.0
RECEIVE:  Connection: close
RECEIVE:  Cache-Control: no-cache
RECEIVE:  Pragma: no-cache
RECEIVE:  Content-Length: 104
RECEIVE:  
RECEIVE:  <html><head><title>Current IP Check</title></head><body>Current IP Address: 72.160.26.10</body></html>
INFO:     forcing updating smj2.homeip. because no cached entry exists.
INFO:     setting IP address to 72.160.26.10 for smj2.homeip.
UPDATE:   updating smj2.homeip.
CONNECT:  members.dyndns.org
CONNECTED:  using SSL
SENDING:  GET /nic/update?system=dyndns&hostname=smj2.homeip.&myip=72.160.26.10 HTTP/1.0
SENDING:   Host: members.dyndns.org
SENDING:   Authorization: Basic bml0ZXdhbGtlcjpuaWNvbGUwMg==
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Date: Wed, 18 Jun 2008 15:31:15 GMT
RECEIVE:  Server: Apache
RECEIVE:  X-UpdateCode: X
RECEIVE:  Content-Length: 7
RECEIVE:  Connection: close
RECEIVE:  Content-Type: text/plain
RECEIVE:  
RECEIVE:  notfqdn
FAILED:   updating smj2.homeip.: notfqdn: A Fully-Qualified Domain Name was not provided
FATAL:    Cannot create file '/var/cache/ddclient/ddclient.cache'. (No such file or directory)
Argument "FAILED" isn't numeric in numeric ne (!=) at /usr/sbin/ddclient line 1375.
nitewalker@smj2:/etc/ddclient$

---

### Post by mbeach on 2008-06-18
check your /etc/ddclient.conf and make sure your server is correct, it appears to be perhaps missing the ".net"  If it is there, make sure there are no spaces.

you might want to make sure the dyndns option in your router is off/unselected as I believe that particular router may be unsupported (you'll be getting denied by the dyndns service).  I had a similar router (the non-wireless version) which I think was banned or something like that by dyndns [I could be wrong or out of date on that].  If you are running the ddclient on your server you don't need it on the router as well.

good howto:
[http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html](http://mexpolk.blogspot.com/2008/01/ubuntu-gutsy-dyndns-client-setup.html)
which I suspect is valid for Hardy.

---

### Post by jjgomera on 2008-06-18
> **Nitewalker said:**
> 
FAILED:   updating smj2.homeip.: notfqdn: A Fully-Qualified Domain Name was not provided

i think you have bad configuration in /etc/ddclient:

do you have smj2.homeip.net or smj2.homeip?, first is  correct

sendmail isn't necesary, i haven't installed and ddclient works ok for me

---

### Post by Nitewalker on 2008-06-18
Thank you all, IT WORKS:)
I did have a bad entry in name, had forgot to put the ".net", also I disabled DDNS in my router, and also found I had to add a dir to /var/cache, as it didn't have the "ddclient/ddclient.cache" in it, once I made the changes and added the dir it all came up okay, and I checked it from the WAN using my palm and a computer at where I work.  Thanks again for everyones assistance....:popcorn:

---

