---
title: "Rogue Connection After Booting?"
date: 2009-08-02
forum: Security
---

### Post by dwhitney67 on 2009-08-02
I hope this is the right forum...


Everytime I reboot my system, I notice that my system is making a connection to a remote server.  Here is the output when I run netstat:
```

$ netstat -at
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 iceland.local:50439     4.23.60.126:www         ESTABLISHED
tcp6       0      0 [::]:www                [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN 

```
When I ran a 'whois' on the remote server listed above, I got these results:
```

$ whois 4.23.60.126

OrgName:    Level 3 Communications, Inc. 
OrgID:      LVLT
Address:    1025 Eldorado Blvd.
City:       Broomfield
StateProv:  CO
PostalCode: 80021
Country:    US

NetRange:   4.0.0.0 - 4.255.255.255 
CIDR:       4.0.0.0/8 
NetName:    LVLT-ORG-4-8
NetHandle:  NET-4-0-0-0-1
Parent:     
NetType:    Direct Allocation
NameServer: NS1.LEVEL3.NET
NameServer: NS2.LEVEL3.NET
Comment:    
RegDate:    1992-12-01
Updated:    2009-06-19

OrgAbuseHandle: APL8-ARIN
OrgAbuseName:   Abuse POC LVLT 
OrgAbusePhone:  +1-877-453-8353
OrgAbuseEmail:  abuse@level3.com

OrgTechHandle: ARINC4-ARIN
OrgTechName:   ARIN Contact 
OrgTechPhone:  +1-800-436-8489
OrgTechEmail:  arin-contact@genuity.net

OrgTechHandle: TPL1-ARIN
OrgTechName:   Tech POC LVLT 
OrgTechPhone:  +1-877-453-8353
OrgTechEmail:  ipaddressing@level3.com

# ARIN WHOIS database, last updated 2009-08-01 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.

```
Now, can anybody tell me why my system is connecting to an L-3 Com website?  For those that do not know, L-3 Com is a US government contractor.

After a few moments later, 'netstat' reports that the connection has been terminated (?) with a CLOSE_WAIT next to the L-3 Com entry.  Then a few moments later, the connection is re-established, and then terminated again.

Why is this happening?

P.S.  I am running Ubuntu 9.04 with the latest updates.

---

### Post by igorzwx on 2009-08-02
is it something like this:
[http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8)

---

### Post by cdenley on 2009-08-03
What is the output of this command while the connection is established?
```

sudo lsof -i :80

```
Can you capture the traffic?

---

### Post by igorzwx on 2009-08-03
better from outside, perhaps.

Boot from LiveCD on another box
[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

and scan the infected box from outside.

But nobody need our advices now, perhaps

---

### Post by cdenley on 2009-08-03
Perhaps there is something downloading weather reports?
```

echo -e "GET / HTTP/1.0\nHost: download.weather.com\n\n"|nc 4.23.60.126 80

```
[http://download.weather.com/](http://download.weather.com/)
[http://www.robtex.com/ip/4.23.60.126.html](http://www.robtex.com/ip/4.23.60.126.html)

---

### Post by cdenley on 2009-08-03
...or tinypic.com
```

echo -e "GET / HTTP/1.0\nHost: i44.tinypic.com\n\n"|nc 4.23.60.126 80

```
[http://tinypic.com/](http://tinypic.com/)

---

### Post by cdenley on 2009-08-03
Gnome's weather report applet will download radar images from image.weather.com when configured to do so. That domain may be resolved to 4.23.60.126.

---

### Post by dwhitney67 on 2009-08-03
> **cdenley said:**
> Gnome's weather report applet will download radar images from image.weather.com when configured to do so. That domain may be resolved to 4.23.60.126.
That must be it, because I do run the gnome weather applet.

I guess I was surprised to see that the IP address resolved to L-3 Com, and not some other entity, such as perhaps the Weather Channel, or NOAA.

---

### Post by bear24rw on 2009-08-03
alot of my traffic at home goes through l-3 servers

---

### Post by cdenley on 2009-08-03
[http://www.level3.com/index.cfm?pageID=443](http://www.level3.com/index.cfm?pageID=443)

---

