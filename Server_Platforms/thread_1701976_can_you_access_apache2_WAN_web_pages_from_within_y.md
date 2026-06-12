---
title: "can you access apache2 WAN web pages from within your LAN"
date: 2011-03-07
forum: Server Platforms
---

### Post by sdowney717 on 2011-03-07
[http://ubuntuforums.org/showthread.php?t=749839&page=6](http://ubuntuforums.org/showthread.php?t=749839&page=6)

this thread, some say yes, some say no.

SO, Which is it?
I do not mean accessing your pages from localhost
I mean going to your WAN IP and accessing pages at a port like 8080

as in this 
yourwanip:8080/myscript.php

this site tests your ports, mine is open on 8080
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by smuthavarapu on 2011-03-07
Tested, No you can not.

Reason, your WAN address given by the site, may not exposed to out side world.

Your LAN knows the your local ip address thats why it works.

Here come network admins / firewall blah blah blah....

---

### Post by volkswagner on 2011-03-07
I can.

If you have opened port 8080 or whatever port Apache2 is listening on, but your site is not visible from inside LAN, and visible outside it is most likely due to your routers NAT.

I can turn off NAT on my router, allowing me to use my site's domain name to access the site from inside my LAN.

Check your NAT setting on your Router.

---

### Post by BkkBonanza on 2011-03-07
From what I recall it depends on your router. Some models do and some don't route their WAN IP within the LAN. On mine it has always worked but I've seen quite a few posts by users that say theirs doesn't.

One way to get around this is to add a static DNS entry on the router that routes to the LAN IP and then use that domain name. If the router has support for manual DNS entries. Most linux based ones do, like Linksys etc.

Also be aware that you also need to port forward the correct port on the router.

---

### Post by bsntech on 2011-03-07
You certainly can access a website that you have setup within your LAN - provided these conditions.

1 - You have a static public IP address - or an IP address that doesn't change.
2 - You have a router that allows you to do "Port Forwarding"
3 - You setup a port forward for the port 8080 to go to your internal IP address

Example - I am running a web server on port 8080 that has an internal IP address of 192.168.0.1.

I have a public IP address from my Cable/DSL service of 1.1.1.1.

I have a router with Port Forwarding.

I login to the router and go to the Port Forwarding and setup the port of 8080 to be forwarded to IP address 192.168.0.1.  Settings saved.

Now, if I type in [Http://1.1.1.1:8080](Http://1.1.1.1:8080), it will then bring up the website appropriately.

Guaranteed that it works.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/services-provided/web-site-hosting.html")

---

### Post by sdowney717 on 2011-03-07
well I setup port forwarding to 192.168.1.101 which is my PC
I also put it in the DMZ, still wont go.

BUT, It also does not work for anyone trying from outside
A friend said it returns

Forbidden
You don't have permission to access /z3950search.php on this server.

[http://www.canyouseeme.org/](http://www.canyouseeme.org/) says port 8080 is open and it can see me.

should this work in the browser?
24.254.241.192:8080/z3950search.php

apache is listening on 8080
> scott@
scott@scott-desktop:~$ sudo nmap -sV 192.168.1.101

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-03-07 10:45 EST
Nmap scan report for scott-desktop (192.168.1.101)
Host is up (0.0000080s latency).
Not shown: 992 closed ports
PORT      STATE SERVICE     VERSION
25/tcp    open  smtp        Postfix smtpd
80/tcp    open  http        Apache httpd 2.2.16 ((Ubuntu))
139/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
3306/tcp  open  mysql       MySQL 5.1.49-1ubuntu8.1
5900/tcp  open  vnc         VNC (protocol 3.7)
8080/tcp  open  http        Apache httpd 2.2.16 ((Ubuntu))
10000/tcp open  http        MiniServ 0.01 (Webmin httpd)
Service Info: Host:  scott-desktop

Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 11.15 seconds


---

### Post by bsntech on 2011-03-07
If you are getting a Forbidden error, then you are correctly accessing the server without a problem.

I just copied/pasted your URL into a Firefox window and also got the Forbidden page.

Do you get a Forbidden page if you are accessing it from within your network?  I'm wondering if you have some kind of configuration setup somewhere that only allows a certain range of IP addresses to connect to it.  That would be the only thing I can think of - if it works internally but not externally.

If it doesn't work internally either - you may have your file permissions on those files incorrect.  Ensure you have all the files owned by www-data (chmod -R www-data.www-data *).  This would be the reason why a Forbidden page is also being displayed - because if the server (running as the www-data user) cannot read them, it won't work.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/services-provided/computer-repair-and-service.html")

---

### Post by BkkBonanza on 2011-03-07
That error message indicates it's getting to apache fine but that you have permission problems with the file or directory. Assuming your file has permission for apache then it's likely directory permission. It typically needs to be 755.

---

### Post by sdowney717 on 2011-03-07
> Do you get a Forbidden page if you are accessing it from within your network?

no, it works fine on localhost.
And all over my internal lan from any computer

how to set that folder for 755?
apache it is using for the php files
/home/scott/public_html

---

### Post by bsntech on 2011-03-07
Next thing to take a look at then are your error logs.  See if it gives you any kind of pointer as to why the external access is getting the Forbidden page.

Based on it working internally and not externally, this doesn't sound like a file permissions issue.  Therefore, the next thing I can think of are IP-based restrictions.

You can set IP-based restrictions so that only specific IPs are allowed access.  You may look through all of your Apache configuration files for anything like this:

Order Deny,Allow
Deny from all
Allow from 192.168.1.0/24

Something similar to that.  The above basically says to only allow anyone from the 192.168.1.0 network (192.168.1.1 - 192.168.1.254) to access the server pages - and deny anyone else.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/services-provided/domain-name-administration.html")

---

### Post by sdowney717 on 2011-03-07
from #[http://www.learncomputer.com/secure-apache/](http://www.learncomputer.com/secure-apache/)

in httpd.conf I put
and then restarted apache.
can you try it again?



AddType application/x-httpd-php .php .html

<Directory />
	Order Deny,Allow
	Deny from All
	Options None
</Directory>

<Directory /home/scott/public_html>
	Order Allow,Deny
	Allow from All 
</Directory>

<Files ~"^/.htacces">
	Order Deny,Allow
	Deny from All 
</Files>

---

### Post by bsntech on 2011-03-07
Based upon your configuration above, you are denying all access to the / directory - but you seem to be allowing everything in the /home/scott/public_html directory.

Do you have your DocumentRoot set to /home/scott/public_html - or where is that pointing to?

For the most part - I think your first configurations <Directory /> could be removed.

---

### Post by bsntech on 2011-03-07
Also - just thinking here...

To ensure there isn't a PHP issue causing it, can you create just a "test.htm" file and add something in there like "testing"?  Add it to the same directory that you have your current page.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/contact-bsntech.html")

---

### Post by sdowney717 on 2011-03-07
Ok, this is part of the log in var/log/apache2
```
127.0.0.1 - - [06/Mar/2011:21:02:41 -0500] "GET /z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.author%3D%22lahaye%22&rpos=4&marctag=on&recordcount=311 HTTP/1.1" 200 2077 "http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.author%3D%22lahaye%22&marctag=off&rpos=4&recordcount=311" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.127 Safari/534.16"
127.0.0.1 - - [06/Mar/2011:21:02:42 -0500] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.127 Safari/534.16"
127.0.0.1 - - [06/Mar/2011:21:02:43 -0500] "GET /z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.author%3D%22lahaye%22&marctag=on&rpos=5&recordcount=311 HTTP/1.1" 200 2223 "http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.author%3D%22lahaye%22&rpos=4&marctag=on&recordcount=311" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.127 Safari/534.16"
127.0.0.1 - - [06/Mar/2011:21:02:44 -0500] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.127 Safari/534.16"
127.0.0.1 - - [06/Mar/2011:21:02:44 -0500] "GET /z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.author%3D%22lahaye%22&marctag=on&rpos=6&recordcount=311 HTTP/1.1" 200 2143 "http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.author%3D%22lahaye%22&marctag=on&rpos=5&recordcount=311" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.127 Safari/534.16"
127.0.0.1 - - [06/Mar/2011:21:02:45 -0500] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.16 (KHTML, like Gecko) Chrome/10.0.648.127 Safari/534.16"
192.168.1.101 - - [06/Mar/2011:21:04:02 -0500] "GET / HTTP/1.0" 200 3539 "-" "-"
127.0.0.1 - - [07/Mar/2011:06:12:33 -0500] "GET /z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000 HTTP/1.1" 200 2233 "http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.14) Gecko/20110221 Ubuntu/10.10 (maverick) Firefox/3.6.14"
127.0.0.1 - - [07/Mar/2011:07:00:57 -0500] "GET / HTTP/1.1" 200 1486 "http://ubuntuforums.org/showthread.php?t=749839&page=3" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.14) Gecko/20110221 Ubuntu/10.10 (maverick) Firefox/3.6.14"
127.0.0.1 - - [07/Mar/2011:07:30:36 -0500] "GET /z3950search.php HTTP/1.1" 200 1824 "http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.14) Gecko/20110221 Ubuntu/10.10 (maverick) Firefox/3.6.14"
127.0.0.1 - - [07/Mar/2011:07:30:36 -0500] "POST /z3950search.php HTTP/1.1" 200 1731 "http://localhost/z3950search.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.14) Gecko/20110221 Ubuntu/10.10 (maverick) Firefox/3.6.14"
192.168.1.101 - - [07/Mar/2011:10:45:07 -0500] "GET / HTTP/1.0" 200 3539 "-" "-"
```

---

### Post by sdowney717 on 2011-03-07
Ok, this is what is in that file httpd.conf now and I restarted apache2.
Could you see if it does anything different?

> AddType application/x-httpd-php .php .html


<Directory /home/scott/public_html>
	Order Allow,Deny
	Allow from All 
</Directory>
<Files ~"^/.htacces">
	Order Deny,Allow
	Deny from All 
</Files>


---

### Post by sdowney717 on 2011-03-07
[http://localhost/index.htm](http://localhost/index.htm)
should show a simple menu bar

the z3950search.php a search page

---

### Post by sdowney717 on 2011-03-07
how about the hosts files? there are 3 of them

hosts
```
192.168.1.101	scott-desktop	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	scott-desktop	localhost6.localdomain6	localhost6
127.0.1.1	scott-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

hosts.allow
```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#

mysqld: ALL
ALL: ALL

```

hosts.deny
```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
```

---

### Post by sdowney717 on 2011-03-07
there are a few errors in error.log
what is the relevance here:

[Mon Mar 07 12:51:28 2011] [error] [client 98.214.209.29] File does not exist: /etc/apache2/htdocs

```
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: taggs in /home/scott/public_html/z3950display.php on line 182, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 5 in /home/scott/public_html/z3950display.php on line 182, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 8 in /home/scott/public_html/z3950display.php on line 182, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 35 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 906 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 955 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 10 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 20 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 28 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 40 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 42 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 50 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 245 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 246 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 250 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 260 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 300 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 505 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 650 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 700 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 953 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined offset: 991 in /home/scott/public_html/z3950display.php on line 190, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 191, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: additup in /home/scott/public_html/z3950display.php on line 287, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:12:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined property: DOMElement::$hasChildNodes in /home/scott/public_html/z3950display.php on line 311, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&kdup=%3D001+1090548&rpos=35&recordcount=10000&write=%3DLDR++01532cam+a2200289+a+4500%0D%0A%3D001+1090548%0D%0A%3D005+20100909092346.0%0D%0A%3D008+920312s1992++++gauab++++++++f000+0+eng++%0D%0A%3D035++__%249%28DLC%29+++92060115%0D%0A%3D010++__%24a+++92060115+%0D%0A%3D040++__%24aDLC%24cDLC%24dDLC%0D%0A%3D043++__%24aap-----%24an-us---%24aa-iq---%0D%0A%3D050++00%24aDS79.724.U6%24bA16+1992%0D%0A%3D082++00%24a956.704%2F4242%24220%0D%0A%3D245++00%24a24th+Mechanized+Infantry+Division+Combat+Team+historical+reference+book+%3A%24ba+collection+of+historical+letters%2C+briefings%2C+orders%2C+and+other+miscellaneous+documents+pertaining+to+the+defense+of+Saudi+Arabia+and+the+attack+to+free+Kuwait.%0D%0A%3D260++__%24a%5BFort+Stewart%2C+Ga.+31314-5000%5D+%3A%24bThe+Team%2C%24c%5B1992%5D%0D%0A%3D300++__%24a1+v.+%28various+pagings%29+%3A%24bill.%2C+maps+%3B%24c29+cm.%0D%0A%3D500++__%24a%22Compiled+at+Fort+Stewart%2C+Georgia%2C+April+1991.%22%0D%0A%3D500++__%24a%22A+collection+of+selected+planning+documents%2C+briefings%2C+combat+orders%2C+intelligence+assessments%2C+and+executive+correspondence+produced+during+the+Desert+Shield+and+Desert+Storm+Campaigns%22--2nd+prelim.+leaf.%0D%0A%3D650++_0%24aPersian+Gulf+War%2C+1991%24xRegimental+histories%24zUnited+States.%0D%0A%3D610++10%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th%24xHistory%24y20th+century.%0D%0A%3D610++10%24aUnited+States.%24bArmy%24xHistory%24yPersian+Gulf+War%2C+1991.%0D%0A%3D710++1_%24aUnited+States.%24bArmy.%24bInfantry+Division%2C+24th.%0D%0A%0D%0A
[Mon Mar 07 06:31:34 2011] [error] [client 58.218.199.147] File does not exist: /etc/apache2/htdocs
[Mon Mar 07 06:46:45 2011] [error] [client 58.218.204.110] File does not exist: /etc/apache2/htdocs
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws1 in /home/scott/public_html/z3950search.php on line 18, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws2 in /home/scott/public_html/z3950search.php on line 19, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws3 in /home/scott/public_html/z3950search.php on line 20, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws4 in /home/scott/public_html/z3950search.php on line 21, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws5 in /home/scott/public_html/z3950search.php on line 23, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws6 in /home/scott/public_html/z3950search.php on line 24, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws7 in /home/scott/public_html/z3950search.php on line 25, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws8 in /home/scott/public_html/z3950search.php on line 26, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws9 in /home/scott/public_html/z3950search.php on line 27, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws10 in /home/scott/public_html/z3950search.php on line 28, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws11 in /home/scott/public_html/z3950search.php on line 29, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws12 in /home/scott/public_html/z3950search.php on line 30, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws13 in /home/scott/public_html/z3950search.php on line 32, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws14 in /home/scott/public_html/z3950search.php on line 33, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo1 in /home/scott/public_html/z3950search.php on line 36, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo2 in /home/scott/public_html/z3950search.php on line 37, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo3 in /home/scott/public_html/z3950search.php on line 38, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo5 in /home/scott/public_html/z3950search.php on line 40, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo6 in /home/scott/public_html/z3950search.php on line 41, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo7 in /home/scott/public_html/z3950search.php on line 42, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo8 in /home/scott/public_html/z3950search.php on line 43, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo9 in /home/scott/public_html/z3950search.php on line 44, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo10 in /home/scott/public_html/z3950search.php on line 45, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo11 in /home/scott/public_html/z3950search.php on line 46, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo12 in /home/scott/public_html/z3950search.php on line 47, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo13 in /home/scott/public_html/z3950search.php on line 48, referer: http://localhost/z3950display.php?request=http%3A%2F%2Flx2.loc.gov%3A210%2FLCDB%3Fversion%3D1.1%26operation%3DsearchRetrieve%26query%3Ddc.title%3D%22free%22&marctag=off&rpos=36&recordcount=10000
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws1 in /home/scott/public_html/z3950search.php on line 18, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws2 in /home/scott/public_html/z3950search.php on line 19, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws3 in /home/scott/public_html/z3950search.php on line 20, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws4 in /home/scott/public_html/z3950search.php on line 21, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws5 in /home/scott/public_html/z3950search.php on line 23, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws6 in /home/scott/public_html/z3950search.php on line 24, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws7 in /home/scott/public_html/z3950search.php on line 25, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws8 in /home/scott/public_html/z3950search.php on line 26, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws9 in /home/scott/public_html/z3950search.php on line 27, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws10 in /home/scott/public_html/z3950search.php on line 28, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws11 in /home/scott/public_html/z3950search.php on line 29, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws12 in /home/scott/public_html/z3950search.php on line 30, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws13 in /home/scott/public_html/z3950search.php on line 32, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws14 in /home/scott/public_html/z3950search.php on line 33, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo1 in /home/scott/public_html/z3950search.php on line 36, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo2 in /home/scott/public_html/z3950search.php on line 37, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo3 in /home/scott/public_html/z3950search.php on line 38, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo5 in /home/scott/public_html/z3950search.php on line 40, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo6 in /home/scott/public_html/z3950search.php on line 41, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo7 in /home/scott/public_html/z3950search.php on line 42, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo8 in /home/scott/public_html/z3950search.php on line 43, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo9 in /home/scott/public_html/z3950search.php on line 44, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo10 in /home/scott/public_html/z3950search.php on line 45, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo11 in /home/scott/public_html/z3950search.php on line 46, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo12 in /home/scott/public_html/z3950search.php on line 47, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo13 in /home/scott/public_html/z3950search.php on line 48, referer: http://localhost/z3950search.php
[Mon Mar 07 07:30:36 2011] [error] [client 127.0.0.1] PHP Warning:  session_start(): Cannot send session cache limiter - headers already sent (output started at /home/scott/public_html/z3950search.php:175) in /home/scott/public_html/z3950search.php on line 210, referer: http://localhost/z3950search.php
[Mon Mar 07 07:37:21 2011] [notice] Graceful restart requested, doing restart
[Mon Mar 07 07:37:21 2011] [error] (9)Bad file descriptor: apr_socket_accept: (client socket)
[Mon Mar 07 07:37:21 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Mar 07 09:01:13 2011] [error] [client 58.218.199.147] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 10:31:58 2011] [error] [client 65.207.58.36] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 10:32:31 2011] [error] [client 65.207.58.36] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 10:32:57 2011] [error] [client 65.207.58.36] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 10:32:58 2011] [error] [client 65.207.58.36] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 10:45:07 2011] [error] [client 192.168.1.101] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:28:44 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:28:45 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:28:48 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:29:08 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:52:09 2011] [notice] caught SIGTERM, shutting down
[Mon Mar 07 11:52:10 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Mar 07 11:54:48 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:54:54 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:57:22 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 11:59:36 2011] [error] [client 98.214.209.29] client denied by server configuration: /etc/apache2/htdocs
[Mon Mar 07 12:02:20 2011] [notice] caught SIGTERM, shutting down
[Mon Mar 07 12:02:21 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws1 in /home/scott/public_html/z3950search.php on line 18
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws2 in /home/scott/public_html/z3950search.php on line 19
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws3 in /home/scott/public_html/z3950search.php on line 20
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws4 in /home/scott/public_html/z3950search.php on line 21
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws5 in /home/scott/public_html/z3950search.php on line 23
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws6 in /home/scott/public_html/z3950search.php on line 24
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws7 in /home/scott/public_html/z3950search.php on line 25
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws8 in /home/scott/public_html/z3950search.php on line 26
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws9 in /home/scott/public_html/z3950search.php on line 27
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws10 in /home/scott/public_html/z3950search.php on line 28
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws11 in /home/scott/public_html/z3950search.php on line 29
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws12 in /home/scott/public_html/z3950search.php on line 30
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws13 in /home/scott/public_html/z3950search.php on line 32
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws14 in /home/scott/public_html/z3950search.php on line 33
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo1 in /home/scott/public_html/z3950search.php on line 36
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo2 in /home/scott/public_html/z3950search.php on line 37
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo3 in /home/scott/public_html/z3950search.php on line 38
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo5 in /home/scott/public_html/z3950search.php on line 40
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo6 in /home/scott/public_html/z3950search.php on line 41
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo7 in /home/scott/public_html/z3950search.php on line 42
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo8 in /home/scott/public_html/z3950search.php on line 43
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo9 in /home/scott/public_html/z3950search.php on line 44
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo10 in /home/scott/public_html/z3950search.php on line 45
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo11 in /home/scott/public_html/z3950search.php on line 46
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo12 in /home/scott/public_html/z3950search.php on line 47
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo13 in /home/scott/public_html/z3950search.php on line 48
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws1 in /home/scott/public_html/z3950search.php on line 18, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws2 in /home/scott/public_html/z3950search.php on line 19, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws3 in /home/scott/public_html/z3950search.php on line 20, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws4 in /home/scott/public_html/z3950search.php on line 21, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws5 in /home/scott/public_html/z3950search.php on line 23, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws6 in /home/scott/public_html/z3950search.php on line 24, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws7 in /home/scott/public_html/z3950search.php on line 25, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws8 in /home/scott/public_html/z3950search.php on line 26, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws9 in /home/scott/public_html/z3950search.php on line 27, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws10 in /home/scott/public_html/z3950search.php on line 28, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws11 in /home/scott/public_html/z3950search.php on line 29, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws12 in /home/scott/public_html/z3950search.php on line 30, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws13 in /home/scott/public_html/z3950search.php on line 32, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws14 in /home/scott/public_html/z3950search.php on line 33, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo1 in /home/scott/public_html/z3950search.php on line 36, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo2 in /home/scott/public_html/z3950search.php on line 37, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo3 in /home/scott/public_html/z3950search.php on line 38, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo5 in /home/scott/public_html/z3950search.php on line 40, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo6 in /home/scott/public_html/z3950search.php on line 41, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo7 in /home/scott/public_html/z3950search.php on line 42, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo8 in /home/scott/public_html/z3950search.php on line 43, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo9 in /home/scott/public_html/z3950search.php on line 44, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo10 in /home/scott/public_html/z3950search.php on line 45, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo11 in /home/scott/public_html/z3950search.php on line 46, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo12 in /home/scott/public_html/z3950search.php on line 47, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo13 in /home/scott/public_html/z3950search.php on line 48, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:04 2011] [error] [client 127.0.0.1] PHP Warning:  session_start(): Cannot send session cache limiter - headers already sent (output started at /home/scott/public_html/z3950search.php:175) in /home/scott/public_html/z3950search.php on line 210, referer: http://localhost/z3950search.php
[Mon Mar 07 12:05:25 2011] [error] [client 127.0.0.1] (13)Permission denied: cannot read directory for multi: /home/scott/public_html/, referer: http://localhost/index.htm
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws1 in /home/scott/public_html/z3950search.php on line 18, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws2 in /home/scott/public_html/z3950search.php on line 19, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws3 in /home/scott/public_html/z3950search.php on line 20, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws4 in /home/scott/public_html/z3950search.php on line 21, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws5 in /home/scott/public_html/z3950search.php on line 23, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws6 in /home/scott/public_html/z3950search.php on line 24, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws7 in /home/scott/public_html/z3950search.php on line 25, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws8 in /home/scott/public_html/z3950search.php on line 26, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws9 in /home/scott/public_html/z3950search.php on line 27, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws10 in /home/scott/public_html/z3950search.php on line 28, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws11 in /home/scott/public_html/z3950search.php on line 29, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws12 in /home/scott/public_html/z3950search.php on line 30, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws13 in /home/scott/public_html/z3950search.php on line 32, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: ws14 in /home/scott/public_html/z3950search.php on line 33, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo1 in /home/scott/public_html/z3950search.php on line 36, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo2 in /home/scott/public_html/z3950search.php on line 37, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo3 in /home/scott/public_html/z3950search.php on line 38, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo5 in /home/scott/public_html/z3950search.php on line 40, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo6 in /home/scott/public_html/z3950search.php on line 41, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo7 in /home/scott/public_html/z3950search.php on line 42, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo8 in /home/scott/public_html/z3950search.php on line 43, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo9 in /home/scott/public_html/z3950search.php on line 44, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo10 in /home/scott/public_html/z3950search.php on line 45, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo11 in /home/scott/public_html/z3950search.php on line 46, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo12 in /home/scott/public_html/z3950search.php on line 47, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: wo13 in /home/scott/public_html/z3950search.php on line 48, referer: http://localhost/z3950search.php
[Mon Mar 07 12:06:13 2011] [error] [client 127.0.0.1] PHP Warning:  session_start(): Cannot send session cache limiter - headers already sent (output started at /home/scott/public_html/z3950search.php:175) in /home/scott/public_html/z3950search.php on line 210, referer: http://localhost/z3950search.php
[Mon Mar 07 12:51:28 2011] [error] [client 98.214.209.29] File does not exist: /etc/apache2/htdocs
```

---

### Post by sdowney717 on 2011-03-07
a file called mysite has this in there
does it look correct for the virtual host?

> <VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/scott/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/scott/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

here is apache2.conf
```
#http://serverfault.com/questions/216252/how-to-configure-apache-sites-available-vs-httpd-conf
#http://www.learncomputer.com/secure-apache/
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "foo.log"
# with ServerRoot set to "/etc/apache2" will be interpreted by the
# server as "/etc/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs/2.2/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
LockFile ${APACHE_LOCK_DIR}/accept.lock

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadLimit: ThreadsPerChild can be changed to this maximum value during a
#              graceful restart. ThreadLimit can only be changed by stopping
#              and starting Apache.
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include all the user configurations:
Include httpd.conf

# Include ports listing
Include ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/
```

---

### Post by bsntech on 2011-03-07
OK - I now get a "404 Not Found" error page - not a forbidden page.

Definitely have something messed up here.

Your apache2.conf file looks fine.
The "mysite" file you speak of - I'm not too sure why this is being used because I don't see it being called from your apache2.conf file anywhere - unless it is being called from the httpd.conf file.

Why not delete that "mysite" file and use the "httpd.conf" file for doing that?

Then, make the httpd.conf file as simple as you possibly can.  Do you really need to have the cgi-bin in there?  Do you really need to have the docs directory in there?  If not, do something in your httpd.conf file that is as simple as this:

<VirtualHost *:80>
ServerAdmin webmaster@localhost
DocumentRoot /home/scott/public_html
Options Indexes FollowSymLinks MultiViews
AllowOverride None

CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost> 

Brian S.

---

### Post by sdowney717 on 2011-03-07
did that and it blows up!

scott@scott-desktop:~/public_html$ sudo /etc/init.d/apache2 restart
Syntax error on line 17 of /etc/apache2/httpd.conf:
AllowOverride not allowed here
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
scott@scott-desktop:~/public_html$

---

### Post by sdowney717 on 2011-03-07
I reversed the changes, and it restarts ok
I got that mysite file following an ubuntu apache2 setup guide when I first set up apache2 last month.

scott@scott-desktop:~/public_html$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
scott@scott-desktop:~/public_html$

Ok, I redid the changes and commented out the troublesome line and it restarted ok

here is httpd.conf

<VirtualHost *:80>
ServerAdmin webmaster@localhost
DocumentRoot /home/scott/public_html
Options Indexes FollowSymLinks MultiViews
#AllowOverride None

CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

---

### Post by bsntech on 2011-03-07
OK - still getting a "404 Not Found" error when trying to pull up the site.

Go into your /etc/apache2 directory and run this:

sudo grep -r "DocumentRoot" *

See what files are returned.

You said that this is still working on your internal computers, right - or is it broken?  I'm thinking that there still has to be some kind of configuration somewhere that is setting the DocumentRoot elsewhere than the /home/scott/public_html folder.

Or - make sure that you indeed have your web files in the /home/scott/public_html folder.

Because we are getting a 404 Not Found error instead of a Forbidden error, it does seem like we have the permissions issues taken care of... now it is a matter of nailing down the right DocumentRoot path where the files are located at.

Brian S.

---

### Post by sdowney717 on 2011-03-07
still working fine on localhhost
these files are most definitely in home/scott/public_html

scott@scott-desktop:/etc/apache2$ sudo grep -r "DocumentRoot" *
[sudo] password for scott: 
httpd.conf:DocumentRoot /home/scott/public_html
sites-available/default:	DocumentRoot /home/scott/public_html
sites-available/mysite:	DocumentRoot /home/scott/public_html
sites-available/default-ssl:	DocumentRoot /var/www
scott@scott-desktop:/etc/apache2$

---

### Post by bsntech on 2011-03-07
Very confused at this point.  Looks like the only place you have the DocumentRoot set is in your httpd.conf directory.

Let's try one more thing:

Go to your /etc/apache2 folder and type in:

sudo grep -r "DirectoryIndex" *

See what you get for that.  You should get something like index.htm, index.html, index.php, or something like that.

Now, go into your /home/scott/public_html directory and do a:

touch <file>

Where <file> is the index.htm, index.html, or whatever the DirectoryIndex was set to.  Or, just create a file in that directory if you are using a GUI.

Now, open the file and just type something in - maybe like "It Works!" or something similar - then save it.  Ensure the permissions are set so that the www-data user & www-data group owns the file with at least 755 permissions.

Now, restart apache (/etc/init.d/apache2 restart) and let us know when done.

Basically what I'm after here - so to be able to just type in:

[http://24.254.241.192:8080/](http://24.254.241.192:8080/)

And have a page come up.

Brian S.

---

### Post by bsntech on 2011-03-07
Alright - stupid me - I just saw another glaring mistake here...

Are you connecting to this Apache web server internally using port 80 or port 8080?

In the httpd.conf file, we set the <VirtualHost *:80> line.  That should be <VirtualHost *:8080>.

So, if you are running the server internally on port 80, keep the current VirtualHost line in there - but just make a duplicate of it - and change the <VirtualHost *:80> to <VirtualHost *:8080>

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/432-the-greening-of-it.html")

---

### Post by sdowney717 on 2011-03-07
ok set to this and restarted apache

<VirtualHost *:8080>
ServerAdmin webmaster@localhost
DocumentRoot /home/scott/public_html
Options Indexes FollowSymLinks MultiViews
#AllowOverride None

CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

---

### Post by sdowney717 on 2011-03-07
scott@scott-desktop:/etc/apache2$ sudo grep -r "DirectoryIndex" *
[sudo] password for scott: 
conf.d/phpmyadmin.conf:	DirectoryIndex index.php
mods-available/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
mods-enabled/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
scott@scott-desktop:/etc/apache2$

ok, did this too

scott@scott-desktop:~/public_html$ touch index.html

---

### Post by bsntech on 2011-03-07
It is now working!

I put in:

[http://24.254.241.192:8080/](http://24.254.241.192:8080/)

I can now see a black bar across the top and when I hover over a link, menus drop down.

Note that the rest of the page isn't there though...

---

### Post by sdowney717 on 2011-03-07
localhost is now running on port 8080, port 80 is file not found
[http://localhost:8080/z3950search.php](http://localhost:8080/z3950search.php)

---

### Post by sdowney717 on 2011-03-07
wow!
ok, can you do the file 
z3950search.php

the menu bar is just a small test index file

IF you can, please do a search, get a 20 record list. Click more on this, get the expanded view and click save to file
It will save a marc record file locally on my PC

---

### Post by bsntech on 2011-03-07
Yep, that link works without a problem.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/decatur-il-website-design-a-website-hosting.html")

---

### Post by sdowney717 on 2011-03-07
cool.
I wrote this to use Library of Congress free MARC record retrieval.
So, you can get the MARC data, save it to a file and then import it into a database for a library.

---

### Post by sdowney717 on 2011-03-07
So how would i put localhost back on port 80 and leave WAN on port 8080?

interestingly, my public_html is now owned by me but I cant do anything with it except as root
IS this due to apache running, so if I stop apache, I will be able to edit these php files again?

---

### Post by bsntech on 2011-03-07
In your /etc/apache2/httpd.conf file - did you leave both VirtualHosts?  One with *:80 and the other with *:8080?

If so, it should be working.

You may also take a look at the /etc/apache2/ports.conf file and ensure you have:

Listen 80
Listen 880

In there.

Brian S.

---

### Post by sdowney717 on 2011-03-07
ok, it is now and back on 80 for localhost.

Any idea on the file access being blocked?
If I simply open that folder as me, there are no files listed.
But open as root and they are all there.

---

### Post by bsntech on 2011-03-07
Do this:

sudo chmod -R 755 /home/scott/public_html
sudo chown -R www-data.www-data /home/scott/public_html

This will make it so that the www-data user (which Apache runs as) has read/write access to the files - but everyone else has only read access.

If you want to be able to update the files with your account, you'll have to do this instead:

sudo chmod -R 777 /home/scott/public_html
sudo chown -R www-data.www-data /home/scott/public_html

---

### Post by sdowney717 on 2011-03-07
perfect!
that works, nice to be able to go in as me and work on them.
Thanks for going thru this with me to get it working.
I will need to review what we did to understand where the hangup was.

---

### Post by BkkBonanza on 2011-03-07
I wouldn't recommend 777 for /home/scott/public_html as any random user who can gain access will be able to modify any and all files there. You would be better to use the group ownership to allow apache to read files. 

I usually set ownership to my account and the group to www-data. Then with 755 apache can read files and I can edit them. Only files that apache needs to write need more permission and I usually limit that to a specific directory.

---

### Post by sdowney717 on 2011-03-08
ok, I did the 755 and will see how that goes.
I made a duplicate of the entire folder for backup.
How could anyone do anything at all unless apache let them?
Is that how?

---

### Post by BkkBonanza on 2011-03-08
If you have 7 permission on the "other" user then any user with access to the system could read,write,exec on files. Apache doesn't control that and this isn't the same as a web user accessing thru Apache. 

But if the system has a security vulnerability such that a user does gain access then their abilities would include editing your web files. By restricting permissions to only you and apache it reduces the scope for what can be done. They have to gain access as you to do the editing, which implies cracking your passsword (or root). 

It's best to give as little permission as needed for things to work correctly.

---

