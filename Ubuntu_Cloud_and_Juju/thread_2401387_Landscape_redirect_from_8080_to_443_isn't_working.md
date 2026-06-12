---
title: "Landscape redirect from 8080 to 443 isn't working"
date: 2018-09-17
forum: Ubuntu Cloud and Juju
---

### Post by erisgriffon on 2018-09-17
After some struggling I managed to get the Landscape quickstart installed and apache running. When I go to the SSL page (https://<servername>) I get an error:

>                [h=1]Oops![/h]       [h=5]Sorry for the inconvenience. Please contact your system administrator for more information.[/h]    
         [h=3]Landscape is unavailable[/h]   Service will resume shortly.

 
  
         


In /var/log/apache2/landscape_error.log is the following: 

```
[Mon Sep 17 19:56:35.956201 2018] [proxy:error] [pid 20500:tid 140470738978560] (111)Connection refused: AH00957: HTTP: attempt to connect to 127.0.0.1:8080 (*) failed
[Mon Sep 17 19:56:35.956259 2018] [proxy_http:error] [pid 20500:tid 140470738978560] [client 192.168.123.93:52119] AH01114: HTTP: failed to make connection to backend: localhost
```

I haven't screwed with the default apache landscape config, but I've attached it (and sanitized my servername out as <servername>)

This has been a frustrating journey so far, and I'm trying to get this set up because I think it might be useful for my company. Thanks a bunch!

---

### Post by elsberrymatt on 2019-05-22
I am having the same issue.  Ubuntu 18.04 Server / Landscape 19.01
I followed the manual install to the letter, here:  [https://docs.ubuntu.com/landscape/en/landscape-install-manual](https://docs.ubuntu.com/landscape/en/landscape-install-manual)
We are using separate App and DB servers (as it suggests).

All I can ever get is the "Oops!" screen.

The Apache2 logfile is as follows:
[Wed May 22 19:56:48.833642 2019] [proxy:error] [pid 13819:tid 140597633447680] (111)Connection refused: AH00957: HTTP: attempt to connect to 127.0.0.1:8080 (*) failed
[Wed May 22 19:56:48.833701 2019] [proxy_http:error] [pid 13819:tid 140597633447680] [client 172.30.58.149:2726] AH01114: HTTP: failed to make connection to backend: localhost

---

