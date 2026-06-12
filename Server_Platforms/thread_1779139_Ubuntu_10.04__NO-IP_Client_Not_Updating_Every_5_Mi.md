---
title: "Ubuntu 10.04 :: NO-IP Client Not Updating Every 5 Minutes (NOIP2)"
date: 2011-06-10
forum: Server Platforms
---

### Post by own3mall on 2011-06-10
I have a NO-IP account which I use for DynamicDNS.  I downloaded and installed the noip2 package from the Ubuntu repository, and I configured it properly.

However, it does not update every 5 minutes as it should.  Instead, it only updates if I restart the no-ip service.  

I did change the permission of the file noip2.conf in /var/lib/noip2 and set the owner to nobody as stated in the read me.  The ip address in /var/lib/noip2/noip2.conf updates but only when I restart the service.

Any idea why?

Here's an output of noip2 -S:

```


Process 32291, started as noip2, (version 2.1.9)
Using configuration from /var/lib/noip2/noip2.conf
Last IP Address set xxx.xxx.xxx.xxx
Account xxxx
configured for:
    host  -.mydomain.com
    host  ftp.mydomain.com
    host  mail.mydomain.com
    host  ns1.mydomain.com
    host  ns2.mydomain.com
    host  ns3.mydomain.com
    host  ns4.mydomain.com
    host  ns5.mydomain.com
    host  ns6.mydomain.com
    host  ns7.mydomain.com
    host  www.mydomain.com
Executing /home/eric/Scripts/ip_notify.sh upon successful update.
Updating every 5 minutes via /dev/eth0 with NAT enabled.
eric@eric-desktop:~$ 


```

After recreating the config files, I got the following in my system log:

```


Jun  9 23:52:48 eric-desktop noip2[12609]: v2.1.9 daemon ended.
Jun  9 23:52:52 eric-desktop noip2[12653]: v2.1.9 daemon started with NAT enabled
Jun  9 23:52:52 eric-desktop noip2[12653]: Unknown error 5 trying to set group[] at dynupdate.no-ip.com.
Jun  9 23:52:52 eric-desktop noip2[12653]: Error info saved in /tmp/NO-IPlvHOn4
Jun  9 23:52:52 eric-desktop noip2[12653]: Error! sent 11 requests, dynupdate.no-ip.com responded with 1 replies.
Jun  9 23:52:52 eric-desktop noip2[12653]: Error info saved in /tmp/NO-IPaNY8Tw


```

/tmp/NO-IPaNY8Tw Contains

```


HTTP/1.1 200 OK
Date: Fri, 10 Jun 2011 05:53:01 GMT
Server: Apache/2
Content-Length: 2
Connection: close
Content-Type: text/plain; charset=UTF-8

:5

```

/tmp/NO-IPlvHOn4 contains:

```

HTTP/1.1 200 OK
Date: Fri, 10 Jun 2011 05:53:01 GMT
Server: Apache/2
Content-Length: 2
Connection: close
Content-Type: text/plain; charset=UTF-8

:5

```


Anyone know what I should do?  Does anyone have the NOIP2 service running properly on Ubuntu 10.04?

---

### Post by own3mall on 2011-06-10
Can anyone help?  :shock:

---

