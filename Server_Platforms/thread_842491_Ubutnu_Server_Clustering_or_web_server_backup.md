---
title: "Ubutnu Server Clustering or web server backup"
date: 2008-06-27
forum: Server Platforms
---

### Post by theonegod on 2008-06-27
Good morning all

I am wondering if there is a way for me to have a backup Ubuntu LAMP server to my primary one that would somehow be configured to be used when and if my primary server became unable to process web requests. 

Is there a way to configure this without buying extra software or hardware? I have a Cisco PIX  working as my firewall and router and then several servers behind them. A relatively basic setup.

We have alot of dynamic content and process real time leads. If our main server is down we would like to redirect traffic to a secondary server that would have a static page which essentially provided the lead affiliates with a reject response as the alternative is a timeout which results in them turning our feeds off. The second server doesn't therefore have to be a clone of the first. I just need o find a way to automatically redirect traffic to a second server in the event a first is unable to respond.

---

### Post by jonabyte on 2008-06-27
I would think that this would have to be done at the router or maybe even where your dns server/settings are.

I am not sure if the server can do something like this.

---

### Post by theonegod on 2008-06-27
I am thinking this would be some sort of web proxy designed to provide this service. I am hoping to find a software solution I can put on a server of my own but it may be that a device will be the only option. 

An example of something similar is this seems to be Squid. I am looking into it to see if it can do what I am looking for.

---

### Post by DFord425 on 2008-06-27
this link might help you [http://www.linux-mag.com/search.php?q=High+Availiblity](http://www.linux-mag.com/search.php?q=High+Availiblity)

---

### Post by theonegod on 2008-06-27
One of our programmers had an idea that could be a solution. He proposed that I setup a bind server and set it as the authoritative name server for the sensitive domains and then run a script on it that checks the production web server for a response. If it finds no response the script would overwrite the bind config file with a prepared replacement that would point to the second server and then restart bind.

My only unknown would be if internet propagation would render this solution to be impractical. If a script could make a change to our router config that would be more ideal but I dont think a script can manage that.

---

### Post by molotov00 on 2008-06-27
theonegod:

A script could do it. Python is a language I've looked into lately and I have it set up to log into websites that have authentication. Python scripts can also be run from the cli, just like any other script.

Edit: the more I think about this the more I think this is your best approach. There'd be no need for more hardware. There are a bunch of neat/simple python examples out there. I'd say you could get it up in a couple hours with minimal programming experience.

---

### Post by molotov00 on 2008-06-27
Ok. This is a bit long for a forum, but I wouldn't post it if I didn't think it was useful. Here, I connect to my router (where there's HTTP authentication [like most routers]).

It displays my "status page" by default.

I didn't write it, but found it (sorry forgot source) and verified that it works for logging into routers.

After installing python, call this from the commandline.

```

import urllib2
import sys
import re
import base64
from urlparse import urlparse

theurl = 'http://192.168.0.1/Status_Router.asp'
# if you want to run this example you'll need to supply
# a protected page with your username and password

username = 'admin'
password = 'somepass'            # a very bad password

req = urllib2.Request(theurl)
try:
    handle = urllib2.urlopen(req)
except IOError, e:
    # here we *want* to fail
    pass
else:
    # If we don't fail then the page isn't protected
    print "This page isn't protected by authentication."
    sys.exit(1)

if not hasattr(e, 'code') or e.code != 401:
    # we got an error - but not a 401 error
    print "This page isn't protected by authentication."
    print 'But we failed for another reason.'
    sys.exit(1)

authline = e.headers['www-authenticate']
# this gets the www-authenticate line from the headers
# which has the authentication scheme and realm in it


authobj = re.compile(
    r'''(?:\s*www-authenticate\s*:)?\s*(\w*)\s+realm=['"]([^'"]+)['"]''',
    re.IGNORECASE)
# this regular expression is used to extract scheme and realm
matchobj = authobj.match(authline)

if not matchobj:
    # if the authline isn't matched by the regular expression
    # then something is wrong
    print 'The authentication header is badly formed.'
    print authline
    sys.exit(1)

scheme = matchobj.group(1)
realm = matchobj.group(2)
# here we've extracted the scheme
# and the realm from the header
if scheme.lower() != 'basic':
    print 'This example only works with BASIC authentication.'
    sys.exit(1)

base64string = base64.encodestring(
                '%s:%s' % (username, password))[:-1]
authheader =  "Basic %s" % base64string
req.add_header("Authorization", authheader)
try:
    handle = urllib2.urlopen(req)
except IOError, e:
    # here we shouldn't fail if the username/password is right
    print "It looks like the username or password is wrong."
    sys.exit(1)
thepage = handle.read()

#display the page
print thepage
```

One last thing. To change settings all you're doing is sending a POST request. So this script can be easily modified. Just look for how to send post requests in Python and merge with this script. I'm heading out now but later I will try getting it to work. Hope this helps!

---

### Post by windependence on 2008-06-27
Why not just set up MySQL replication to the second box. Then, in case of a failure you can just run on the second box until the main is back online and replicate all the changed data back to the first one.

[http://dev.mysql.com/doc/refman/5.0/en/replication.html](http://dev.mysql.com/doc/refman/5.0/en/replication.html)

[http://www.howtoforge.com/mysql_database_replication](http://www.howtoforge.com/mysql_database_replication)

You ma also br interested in CARP for automatice failover

[http://en.wikipedia.org/wiki/Common_Address_Redundancy_Protocol](http://en.wikipedia.org/wiki/Common_Address_Redundancy_Protocol)

or heartbeat:

[http://packages.ubuntu.com/dapper/admin/heartbeat](http://packages.ubuntu.com/dapper/admin/heartbeat)

There are many ways to do this.

-Tim

---

### Post by molotov00 on 2008-06-27
ok buddy ;) I figured I'd try the Python route because I've never tried doing it before.
```

import urllib2, urllib
# Create an OpenerDirector with support for Basic HTTP Authentication...
auth_handler = urllib2.HTTPBasicAuthHandler()
auth_handler.add_password(realm='home',
                          uri='https://192.168.0.1/',
                          user='admin',
                          passwd='MYPASS')
opener = urllib2.build_opener(auth_handler)
# ...and install it globally so it can be used with urlopen.
urllib2.install_opener(opener)
#form POST request

"""
I want to change port forwarding, just as an example. Here's the important part of the HTML form (just check browser and go "view source")
<FORM name=portRange method=post action=apply.cgi>
<input type=hidden name=submit_button>
<input type=hidden name=action>
<input type=hidden name="forward_port" value="10">
I'm just going to forward one port for this example.
application (name0=apache)
start (to0=80)
end (from0=80)
protocol (pro0=both)
ip address(ip0=206)
and "enable" toggle (enable0=on).

There's some javascript but at the end it turns out that JS's just defining action as 'Apply' (you can see the hidden field above)

It's REALLY important that you identify all of the relevant input fields. Since I only have one forward it's easy, but if you have advanced configuration
then you will have to replicate all ten/whatever forwards below. i.e. name1, name2, etc.

Form POST request.
"""

url = 'http://192.168.0.1/apply.cgi'
values = {'submit_button' : 'Forward',
	'action' : 'Apply',
	'forward_port' : '10',
	'name0' : 'apache',
	'to0' : '80',
	'from0' : '80',
	'pro0' : 'both',
	'ip0' : '206',
	'enable0' : 'off'}

data = urllib.urlencode(values)
req = urllib2.Request(url, data)
response = urllib2.urlopen(req)
the_page = response.read()
print the_page
#urllib2.urlopen('http://www.example.com/login.html')
```

That is a simpler version of the script I posted earlier. This one changes an existing port forward to port 80 to my 192.168.0.206. Of course this is unique to my router (wrt54g), but should require minimal adjustment to get it to work on others. I could give you a hand but if you have a programmer buddy he should find it pretty straightforward since most of the work's been done.

Hopefully you'll find this useful. It was much easier than I thought. If you just throw the whole script in an "if" statement to check whether the server is online, then add it to crontab to run every 5 mins, you'd have *exactly* what you want.

M

---

### Post by theonegod on 2008-06-27
Wow alot of replies. The reason I do not use MySQL replication is that we are working with a MS SQL server.

In regard to the python script that certainly sounds interesting. The router that it would be conencting to though (at this right now) has no web interface and is a Cisco Pix. The script would have to be able to telnet to the pix, authenticate, enter privilaged mode, enter terminal config mode, and then remove the old static lines and put in new static lines (yes this is an old pix). It would then have to be able to execute a reload command on the pix to make the static entries take effect right away.

I am working to replace this Pix with an Adtran NetVanta 3430. It also can have some of this done via telnet. 

Will the Python script be able to do as I stated above?
It will essentially have to do as follows

----------

Oh my god the web server is not responding!
telnet 192.168.0.1
(enter password)
enable
(enter password)
config t
no static (DMZ,outside) x.x.x.x 192.168.0.3 netmask 255.255.255.255 0 0
static (DMZ,outside) x.x.x.x 192.168.0.4 netmask 255.255.255.255 0 0
write mem
reload
(send an ENTER for confirmation)

After all this it then has to email me to tell me it had to do it so I can go in and fix it.

---

### Post by Chayak on 2008-06-28
It's actually a lot simpler than many are making it.  Use the heartbeat package with IP failover.

If the secondary web server doesn't get a heartbeat packet it will then take over the web server IP address and replace it.  Your database isn't on the same box as the web servers so this should work.  The only issue is that now your database is the single point of failure rather than your web server...

[http://www.linuxjournal.com/article/5862]("http://www.linuxjournal.com/article/5862")
is a how-to on setting it up.

---

### Post by molotov00 on 2008-06-28
Yeah a python script could easily do telnet.

As far as doing the heartbeat... it's not "a lot simpler"... as it involves adding two NICs: (from your link)

"According to the accompanying documentation, you need to install a second NIC on both nodes and connect them with a cross overcable."

I actually think that a little script would be the better choice for his needs. Also notice that it doesn't have to be a true cluster.

All you need is a script that goes every couple mins/seconds, checks to see if the server is up. If it isn't up, modify the router to redirect to the secondary server. As a proof of concept I wrote the script for my router, and I'll probably implement it. You make heartbeat sound simple... it requires buying and installing two NICs; and is a true cluster (which is not required) did you even read you own article?

---

### Post by theonegod on 2008-06-28
Heartbeat is one meathod but keep in mind that both of these servers are blade servers in the same enclosure. So a second nic isn't technically needed as each already has 2 nics within each blade. 

It is a good solution but one that would probably be alittle more complicated then a script to modify the 1-to-1 NAT in the PIX.

---

### Post by Chayak on 2008-06-28
Any decent server comes with two nic's on the board already.  It's a tried and true solution that's deployed a lot and is simpler than worrying about custom scripts because if your server does fail you're going to have to reset everything manually when the failed unit comes back up.  A failover cluster will take care of that for you.

You also have the issue that if the server is compromised you have the password to your firewall stored on the system

---

### Post by windependence on 2008-06-28
> **Chayak said:**
> Any decent server comes with two nic's on the board already.  It's a tried and true solution that's deployed a lot and is simpler than worrying about custom scripts because if your server does fail you're going to have to reset everything manually when the failed unit comes back up.  A failover cluster will take care of that for you.

You also have the issue that if the server is compromised you have the password to your firewall stored on the system

I totally agree here. For replication, you could use a simple rsync script and run a cron job every so often to keep the data current. The first copy would take a long time, but then after that rsync is really quick since it only writes the data that has changed. If you run this say every 15 minutes you should be OK.

-Tim

---

### Post by windependence on 2008-06-28
> **theonegod said:**
> Wow alot of replies. The reason I do not use MySQL replication is that we are working with a MS SQL server.

In regard to the python script that certainly sounds interesting. The router that it would be conencting to though (at this right now) has no web interface and is a Cisco Pix. The script would have to be able to telnet to the pix, authenticate, enter privilaged mode, enter terminal config mode, and then remove the old static lines and put in new static lines (yes this is an old pix). It would then have to be able to execute a reload command on the pix to make the static entries take effect right away.

I am working to replace this Pix with an Adtran NetVanta 3430. It also can have some of this done via telnet. 

Will the Python script be able to do as I stated above?
It will essentially have to do as follows

----------

Oh my god the web server is not responding!
telnet 192.168.0.1
(enter password)
enable
(enter password)
config t
no static (DMZ,outside) x.x.x.x 192.168.0.3 netmask 255.255.255.255 0 0
static (DMZ,outside) x.x.x.x 192.168.0.4 netmask 255.255.255.255 0 0
write mem
reload
(send an ENTER for confirmation)

After all this it then has to email me to tell me it had to do it so I can go in and fix it.

Ok I am really confused here. You said:

> I am wondering if there is a way for me to have a backup **Ubuntu LAMP server** to my primary one that would somehow be configured to be used when and if my primary server became unable to process web requests.

That's not MSSQL. If you are running a LAMP server unless there is something I don't know about MSSQL running on Linux, you would be running MySQL. Are we talking about a Linux box here or a Windoze box?

-Tim

---

### Post by theonegod on 2008-06-29
Lets pretend it is posible that my setup has 2 servers. A LAMP server which of course does have MySQL on it. And a second windows Box that has a MS SQL server on it. 90% of my sites access a database on the Windows MS SQL box. 1 of my sites access a MySQL database.  It is really not very confusing. 

Now, the last few posts are good in theory but I am NOT looking for a solution that mirrors the server. Because the database server could also go down. If either server goes down the result is TIMEOUTS to our affiliates that are sending us leads 24/7. What I want is a failover to a NON mirrored server that instead of having the dynamic content has a static page that gives our affiliates a reject instead of a timeout. 

In the event of a timeout they turn off the feed. This costs us money. I will be notified of the problem when it occurs and I can fix it. If it happened at all.  But while any problem IS happening I need a failover that results in a reject to our affiliates. 

This is why I want a failover that is not to a mirrred server. The important database is on a standalone MS SQL server which is not and can not really be mirrored. 

Because of this the scrypt that resets the router settings gets done what I need. The heartbeat meathod also would. Both are good solutions.

---

### Post by windependence on 2008-06-29
Much clearer. The heartbeat solution is great because it is made for this situation and has been proven in enterprise environments. Like you said eith one would work, but a custom script may be harder to maintain as opposed to a "stock" solution like heartbeat.

-Tim

---

### Post by theonegod on 2008-06-30
In order to get either of these setups to be working well it would seem I will need to have valid SSLs on 2 servers at once. I have not set SSLs on 2 servers before and it was my impression before this point that an SSL has to be unique to a single server. Is it possible to have a SSL setup and valid on 2 different servers for the same domain? 

Also in reading about heartbeat as  method I come across at least 2 reasons it my not work well in my situation. 

1) My problem in the past has more been that Apache itself or some other services become locked up and stop responding. The server does not go down however and Heartbeat would not necessarily know something was wrong if it's method of checking is similar to a ping. Also sometime the issue may not be the web server at all but rather the SQL server that is down. This still results in a need for me to bring up a second web server so the content I am serving reflects the SQL servr being down.

2) If number 1 was not an issue and it was somehow able to monitor connection by service and not just a ping then since the Server 1 was still up does it remove the virtul interfaces on server 1 before setting them up on server 2? If not I would get IP conflicts. 

For the above 2 reasons I think in my case the script that changes my 1-to-1 NAT may end up working better for me. It will allow me to check connectivity based on http requests which will give me the same result whether the problem is my primary web server or my SQL server (once the apache que fills up waiting on the SQL machine for responses).

---

