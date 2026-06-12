---
title: "HOWTO run an ssh server without a static IP address"
date: 2006-08-30
forum: Tutorials
---

### Post by celticmonkey on 2006-08-30
**HOWTO set up a ssh server with a dynamic ip address**

The problem: Your ISP changes your IP address and suddenly you can't use *ssh me@201.202.203.204* to login to your computer until you get home and find out your new IP address.

The solution: A domain name that always points to your constantly changing IP address. This will allow you to login to your computer with *ssh [email]username@mydomain.com[/email]* even if your ISP changes your IP address frequently. That also means no need to remember those crazy IP address numbers.

> This HOWTO assumes you already know how to set up an ssh server and use port forwarding. If not see this tutorials:

HOWTO set up the SSH server
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

HOWTO secure your SSH server
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

HOWTO forward ports on your router for SSH
[http://www.portforward.com/english/applications/port_forwarding/SSH/SSHindex.htm](http://www.portforward.com/english/applications/port_forwarding/SSH/SSHindex.htm)


Okay. First step. Get a domain name that points to your router.

Create a FREE account at [http://www.dyndns.com/](http://www.dyndns.com/)

Once you're registered, goto [https://dyndns.com](https://dyndns.com) --> My account --> My hosts --> add a dynamic dns

Pick a name like myname.homelinux.com or bananaflange.homeunix.net or whatever floats your boat. 

So far so good. But that domain name points to an IP address that your ISP could change tomorrow! If only there was a way to update this info automatically!

There is! (1) Create a shell script to automatically get your external IP address and update your account at [www.dyndns.com](www.dyndns.com) and (2) put that script in a /etc/cron.hourly where it will automatically be run every hour or /etc/cron.daily where it will run daily.

```
sudo gedit /etc/cron.hourly/dyndns.sh
```

Fill in the blanks for your username and password at DynDNS.

```
#!/bin/bash
# Set the username and password for the dyndns account
USERNAME=
PASSWORD=
# Set the system being used to either static or dynamic DNS
SYSTEM=dyndns
# Set the hostname for the record to change
DYNHOST=
# Set whether to wildcard the DNS entry, i.e. *.$DYNHOST
WILDCARD=OFF
############################################
## DO NOT EDIT ANYTHING BEYOND THIS POINT ##
############################################
if [ -z "$DYNDNS" ]; then
DYNDNS="$DYNHOST"
fi
if [ -z "$DNSWILD"]; then
DNSWILD="$WILDCARD"
fi
LOOKUP=`host $DYNHOST | awk '{print $4}'`
MYIP=`curl -s http://www.ipchicken.com | awk '/[0-9]*\.[0-9]*\.[0-9]*\.[0-9]*/ {print $1}'`
# Do the work
if [ "$LOOKUP" = "$MYIP" ]; then
echo "No change in DNS entry."
else
echo `lynx -auth=${USERNAME}:${PASSWORD} -source "http://members.dyndns.org:8245/nic/update?system=${SYSTEM}&hostname=${DYNDNS}&myip=${MYIP}&wildcard=${DNSWILD}"`
fi
```

From now on you can login to your ssh server with ssh [email]user@myname.homelinux.net[/email] (or another domain choice). Even if your ISP changes your IP address while you are away, things will right themselves within the hour.

Edit: The script was changed after it got me temporarily suspended from dyndns.org. An error caused it to update the dns entry every time the script was run, leading to a terse email from dyndns.org regarding bandwidth. This has been corrected. Also, the site for ip lookup has been changed from dyndns.org to ipchicken.com.

Bibliography:
[http://malvasiabianca.org/archives/2006/04/how-do-i-find-my-routers-external-ip-address](http://malvasiabianca.org/archives/2006/04/how-do-i-find-my-routers-external-ip-address)

---

### Post by BeachBum on 2006-11-27
Thanks for the howto!

It wasn't updating for me, and I searched the forums and found that cron scripts should not have an extension (no .sh).  See here:

[http://www.ubuntuforums.org/showthread.php?t=263842&page=2&highlight=cron.hourly](http://www.ubuntuforums.org/showthread.php?t=263842&page=2&highlight=cron.hourly)

Thanks again!

---

### Post by kjacks on 2006-11-30
Thanks for the great tutorial!  I never knew this could be so easy.  But I did have to add one step to get mine working:

chmod a+x /etc/cron.hourly/dyndns

:p

---

### Post by desimo on 2006-12-01
If you are interested in using your own domain name, zoneedit.com offers a free account with 5 free dns "zones" (for low traffic use) which work great for dynamic ips.  I use the following in a cron entry to "ping" the server every half-hour.
```

wget -O - --http-user=myusername --http-passwd=mypassword 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomainname.com'

```

I use mine for for an apache2 with mod-musicindex setup so I can stream music to my workplace from home...

---

### Post by celticmonkey on 2006-12-03
I've rewritten the dyndns updater as a Python script. It has the added benefit of working cross platform.

Just open a text editor, enter this code and save it as dyndns.py  

```
#!/usr/bin/env python

import os
import socket
import urllib
import urllib2
import re

#Put your own username, password and dynhost name here.
username='your_user_name'
password='your_password'
dynhost='yourdomain.whatever.com'
system='dyndns'
wildcard='OFF'

############################################
## DO NOT EDIT ANYTHING BEYOND THIS POINT ##
############################################

print '\nDyndns.org updater is running!!!\n'

#Find out what dynamic IP is currently set to. 
lookup=socket.gethostbyname(dynhost)
print 'DynDNS is set to' , lookup

#Find out what external IP really is.
ipchicken = urllib2.urlopen('http://www.ipchicken.com')
chicken = ipchicken.read(10000000)
ipchicken.close()
rawstr = r"""[0-9]*\.[0-9]*\.[0-9]*\.[0-9]*""" #regex for an IP address
myip_obj = re.search(rawstr, chicken)
myip = myip_obj.group()
print 'Your actual IP is' , myip

#Compare those IPs
if lookup == myip :
    print 'No change in DNS entry.'
else:
    #change the DNS entry 

    data = {}
    data['system'] = system
    data['hostname'] = dynhost
    data['wildcard'] = wildcard
    data['myip'] = myip
    url_values = urllib.urlencode(data)
            
    url = 'http://members.dyndns.org:8245/nic/update'
    full_url = url + '?' + url_values
      
    # create a password manager for loging into dyndns.org
    password_mgr = urllib2.HTTPPasswordMgrWithDefaultRealm()

    # Add the username and password.
    password_mgr.add_password(None, url, username, password)

    handler = urllib2.HTTPBasicAuthHandler(password_mgr)

    # create "opener" (OpenerDirector instance)
    opener = urllib2.build_opener(handler)

    # use the opener to fetch a URL
    opener.open(full_url)

    print "DNS updated."
```

---

### Post by blumagic on 2007-01-17
Hi,

I have just recently found your posts and I am now using your python script. It does work nicely. I am wondering however, if there is a way to get an email sent with the IP address details? I travel and dont always have a way to get the IP address if it has changed. So if the script could send a hourly or better daily  email, I would always have an up to date IP address.

Thanks,

blumagic

---

### Post by dmizer on 2007-01-18
> **blumagic said:**
> Hi,

I have just recently found your posts and I am now using your python script. It does work nicely. I am wondering however, if there is a way to get an email sent with the IP address details? I travel and dont always have a way to get the IP address if it has changed. So if the script could send a hourly or better daily  email, I would always have an up to date IP address.

Thanks,

blumagic

the WHOLE point of this howto is so you don't have to know your ip address ... ever.  so, no matter where you are, you can always get to your server by url instead of needing to know your ip address. (eg: ssh [email]user@yourname.dyndns.net[/email], [http://yourname.dyndns.net](http://yourname.dyndns.net), [ftp://yourname.dyndns.net](ftp://yourname.dyndns.net) ... and so forth)

if ALL you want to know is your ip address while you're on the road, you can always do this:
```
ping yourname.dyndns.net
```

---

### Post by blumagic on 2007-01-18
Geez,

I dont know why I didnt think to do that myself.
That is just what I need. 

Thanks,

blu.....

---

### Post by phillywize on 2007-01-18
This is really great...thank you!

I have a question (for anyone with an understanding of python, and how the python script works:  I often connect to my office over a pptp connection (using the network manager plugin).  Anyone have *any* idea (code) on how I could modify the python script to check whether the pptp connection is active before updating my ip at dyndns?  The issue is that if it updates while I'm connected over the pptp connection, it will set my ip address to my work's ip.  Bad for a number of reasons, not least of which that it breaks things.

Thanks.

Bob

---

### Post by ianmac on 2007-01-19
As an even easier solution, some routers have dyndns support built right in, so instead of setting up cron, etc...  you can configure your router to update dyndns whenever its IP changes.

Ian

---

### Post by phillywize on 2007-01-19
> **ianmac said:**
> As an even easier solution, some routers have dyndns support built right in, so instead of setting up cron, etc...  you can configure your router to update dyndns whenever its IP changes.

Ian


Ahhh, that's the ticket.   My router's got the client built in.   Thanks.

---

### Post by celticmonkey on 2007-01-19
> **blumagic said:**
> Hi,
 I am wondering however, if there is a way to get an email sent with the IP address details? 
blumagic

I originally rewrote it in python because I eventually wanted to do just that and python has some libraries that handle the SSL authentication necessary to use my ISP's mail server or a webmail account. However, I'm sure there's probably a simpler way of doing things via some command line magic with postfix or sendmail. But that would entail configuring a mail local mail server. I'm sure there's a FAQ somewhere in these forums about sendmail.

---

### Post by jvc26 on 2007-07-16
Brilliant work there, thanks very much - now I don't need to have a DynDNS Updater running from a different computer on the LAN the server can do the whole job. Thanks again,
Il

---

### Post by zool2005 on 2007-09-17
see below (with quote this time)

---

### Post by zool2005 on 2007-09-17
> **dmizer said:**
> the WHOLE point of this howto is so you don't have to know your ip address ... ever.  so, no matter where you are, you can always get to your server by url instead of needing to know your ip address. (eg: ssh [email]user@yourname.dyndns.net[/email], [http://yourname.dyndns.net](http://yourname.dyndns.net), [ftp://yourname.dyndns.net](ftp://yourname.dyndns.net) ... and so forth)

if ALL you want to know is your ip address while you're on the road, you can always do this:
```
ping yourname.dyndns.net
```

PING ! An excellent tip to quickly find your IP address from any internet ready computer!
However, I'd never have thought of using ssh [email]username@dyndnsdomain.com[/email]. Great tip

---

### Post by likerice on 2008-05-26
i'm not able to ssh to the DynDNS account that i set up. i'm receiving the message "ssh: connect to host xxx.yyy.com port 22: Connection refused" even though i've forwarded port 22 on my router.

i *am*, however, able to directly ssh across my LAN from a client to my host by using username@host-machine-name.

any suggestions? i'm a total n00b :-(

---

### Post by Dave_Connor on 2008-08-11
Sorry to bump this, did you look in /etc/hosts.allow and /etc/hosts.deny ? To see if your allowed on your system or that you may be blocked ?

---

### Post by mrThirteen on 2008-12-12
Great tips here, however I am having an issue with the python script.  It works when I make sure it's chmod a+x dyndns.py  and I type ./dyndns.py  but it will not fire off hourly when it is in /etc/cron.hourly.

Not sure why.  Any thoughts?

---

### Post by dravstone on 2009-05-07
> **mrThirteen said:**
> Great tips here, however I am having an issue with the python script.  It works when I make sure it's chmod a+x dyndns.py  and I type ./dyndns.py  but it will not fire off hourly when it is in /etc/cron.hourly.

Not sure why.  Any thoughts?

I realize this post is very old, but I recently ran into this problem and thought I'd reply anyway in the event someone else has the same issue.

-- Remove the '.py' extension for the script.

Also this is my first time posting to a forum so I hope I'm not breaking any rules or stepping on any toes, but I modified the Python script to work with DNS-O-Matic ([http://www.dnsomatic.com](http://www.dnsomatic.com)).

```

#!/usr/bin/env python
from base64 import  encodestring
from socket import gethostbyname
from urllib import urlencode
from urllib2 import Request, urlopen

#Put your  username, password and hostname  here.
username='your_user_name'
password='your_password'
hostname='your.hostname'
#See https://www.dnsomatic.com/wiki/api for explanation of the following parameter values and options
wildcard='NOCHG'
mx='NOCHG'
backmx='NOCHG'

############################################
## DO NOT EDIT ANYTHING BEYOND THIS POINT ##
############################################

print '\nDNS-O-Matic.com updater is running!!!\n'

#Get your current dynamic IP 
lookup=gethostbyname(hostname)
print 'DNS-O-Matic is set to', lookup

#Get actual external IP.
ip_external = urlopen('http://myip.dnsomatic.com')
myip = ip_external.read()
ip_external.close()
print 'Your actual IP is' , myip

#Compare those IPs
if lookup == myip :
    print 'No change in DNS entry.'
else:
    #change the DNS entry 

    data = {}
    data['hostname'] = hostname
    data['myip'] = myip
    data['wildcard'] = wildcard
    data['mx'] = mx
    data['backmx'] = backmx

    url_values = urlencode(data)

    url = 'https://updates.dnsomatic.com:443/nic/update?' + url_values
    request =  Request(url)

    base64string = encodestring(username + ':' + password)[:-1]
    request.add_header("Authorization", "Basic %s" % base64string)
    request.add_header('User-Agent',username + ' - Home User - 1.0')

    htmlFile = urlopen(request)
    htmlData = htmlFile.read()
    htmlFile.close()

    results = htmlData.split()
    if results[0] == 'good':
        print "DNS updated to " + results[1]
    else:
        print 'DNS update failed with error: ' + results[0]

```

---

### Post by celticmonkey on 2009-05-12
Thanks for updating the script! I haven't used it for a long time since my router has built in support for dyndns. But it's nice to see other people improving it.

---

### Post by Stian1979 on 2009-09-26
I would like to reverse this by using dyndns on my laptop.
I will use static IP on my ssh server and wish to use passwordless login with a key, but also set up the server so it only accept me.homelinux.com to log in.
I don't know if this is possible.

---

### Post by dmizer on 2009-09-27
> **Stian1979 said:**
> I would like to reverse this by using dyndns on my laptop.
I will use static IP on my ssh server and wish to use passwordless login with a key, but also set up the server so it only accept me.homelinux.com to log in.
I don't know if this is possible.

Use strong rsa encrypted keypairs, disable password protected login, and it will only allow your laptop.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

This is the BEST way to secure your ssh server from unwanted access.

---

### Post by flittermice on 2012-04-09
Some tweak for the **client** side:

If you don't want to get the message *"Permanently added the RSA host key for IP address ... to the list of known hosts."* every time the server IP address changes use the option **CheckHostIP** in your **.ssh/config**:

Host            my.server.dns.name
CheckHostIP     no

Flittermice

---

### Post by pete_l on 2012-04-18
> **celticmonkey said:**
> **HOWTO set up a ssh server with a dynamic ip address**

Okay. First step. Get a domain name that points to your router.

Create a _FREE account_ at [http://www.dyndns.com/](http://www.dyndns.com/)

This FAQ is obsolete as dyndns.com no longer offers a free DNS service. Does anyone know how it should be updated - or should it be removed?

---

### Post by dmizer on 2012-04-20
> **pete_l said:**
> This FAQ is obsolete as dyndns.com no longer offers a free DNS service. Does anyone know how it should be updated - or should it be removed?

There are still tons of other free dns services out there: [http://dnslookup.me/dynamic-dns/](http://dnslookup.me/dynamic-dns/)

For a more current howto, look here: [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

