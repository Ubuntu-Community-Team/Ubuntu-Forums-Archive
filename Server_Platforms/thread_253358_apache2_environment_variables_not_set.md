---
title: "apache2 environment variables not set"
date: 2006-09-08
forum: Server Platforms
---

### Post by geoff.l on 2006-09-08
I have a LAMP server setup on a home lan with apache2.  

The primary purpose is as a development / test box for my "real" site which is hosted externally.   I needed a box to play with.

I use a "dummy" domain name of "home.lan" which is not exposed to the internet.  My hostname is set to "server1.home.lan"  and hostname and hostname -f both show this correctly.

I am not using virtual hosts, so I just have the main server and in apache2.conf I set:  ServerName server1.home.lan:80  

I am NOT using any dns for the home lan, so to access the server I point to it using the ip address.

Now pretty much everything works just fine,  but I have some problems with some specific php scripts that use apache environment variables.   Using phpinfo() to compare my hosted server with my home server I see that variables like SERVER_NAME are set to the IP address not fqdn.   

Are these set that way beacuse I requested the host by IP address ?  Or am I missing something in the setup ?  The phpinfo output shows the correct fqdn in the apache2handler section ... and so it seems apache has detected my hostname/domainname correctly.    

Also the hostname seems to be seen correctly by other application (Postfix for example).  It's just apache I'm having trouble with.

Any suggestions where to look?

---

