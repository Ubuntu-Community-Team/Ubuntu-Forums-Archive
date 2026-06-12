---
title: "apache2 issue"
date: 2011-07-12
forum: Server Platforms
---

### Post by MissinasWorld on 2011-07-12
I was running an older version of Ubuntu until today and have been using Ubuntu desktop to host an apache server for years with no issues, so I guess I had them coming. Last night my site went off line so I backed it up and decided it was time to upgrade to Ubuntu 11.04. 
I did a nice clean, basic install of Ubuntu 11.04 and then used the terminal to install apache2. Apache2 installed with no issues. I went and did the [http://www.localhost/](http://www.localhost/) and my home page showed up so no big deal. I use cjb.net to redirect my sites address to my computer: [http://missina.cjb.net/](http://missina.cjb.net/) so I typed in my address and it came up. I went to another computer and...nothing..says unable to connect. 
so I ran ifconfig to make sure I had the right inet addr in my wireless router and I did. This is what it gave me:
```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:6a:3c:c4  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe6a:3cc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17871874 (17.8 MB)  TX bytes:1840032 (1.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1540561 (1.5 MB)  TX bytes:1540561 (1.5 MB)
```

On the same wireless router I do have a D-link wireless security cam that runs off port 800 and it is working fine if I type in missina.cjb.net:800/
So I know that the redirector is just not seeing port 80-or at least I think not. Honestly I'm kind of lost and have been looking online now since 4:30pm and its now 8:41pm so I am giving up and posting for help. 
just to cover some more bases:
I checked /etc/apache2/conf.d and it says ServerName localhost
There is apparently nothing under httpd.conf and its just a blank file
ports.conf says this:
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```

and i have no idea what might be relevant other then those files. I do not do anyting with sql or php,,I just run basic html pages with photos. I have Never had this much trouble before! So any and all help will be awesome. 

Missina

---

### Post by MissinasWorld on 2011-07-13
still having issues. I went back to the last LTS, 10.04, and reinstalled apache. the installation gave me an the same message I had been getting yesterday at some point in time:
"Setting up apache2-mpm-worker (2.2.14-5ubuntu8.4) ...
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

Setting up apache2 (2.2.14-5ubuntu8.4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place"

So I opened up the /etc/apache2/httpd.conf and added ServerName localhost and saved. the error message went away but still having issues. 
when I type in localhost in firefox i get the message saying it works. but if I go to another computer IN or OUT of the network it comes up with cannot connect. 
I have tried several solutions on line but not a one has worked. I feel like I am missing something simple but cannot figure it out. I even tried changing the permissions on the /var/www folder and nodda. 



Missina

---

### Post by MissinasWorld on 2011-07-13
Never mind it was something simple. It only too me since 4:30 yesterday to figure it out. I changed my computer from having a wireless card to being hard wired and apparently that meant I had to open port 80 up differently in my router then I had been. what a pain in the rear end. 

Missina

---

### Post by CharlesA on 2011-07-13
> **MissinasWorld said:**
> Never mind it was something simple. It only too me since 4:30 yesterday to figure it out. I changed my computer from having a wireless card to being hard wired and apparently that meant I had to open port 80 up differently in my router then I had been. what a pain in the rear end. 

Missina

Did the machine get a different IP? Glad you got it working in any case.

---

### Post by MissinasWorld on 2011-07-13
> **CharlesA said:**
> Did the machine get a different IP? Glad you got it working in any case.

:( I posted to soon. the pc kept the same IP but I changed it to single port forwarding instead of port range forwarding. It worked for all of about 5 minutes and now its not working again. I am beginning to wounder if its really the router and Not the computer or the apache2 server. the router is not old but stuff happens! I have a linksys E2000. maybe I will update the firmware in it and see if that helps. or try to find out how to keep the Ethernet from timing out. 

Update: I did a firmware update on my router, power cycled it, reset everything back up for my wireless and now..now my site works. I have no idea what created this issue in the first place but I would love to know. at least it was not ubuntu. :)

um and I have no idea how to change this type to solved so if an admin could be so kind?

Missina

---

### Post by CharlesA on 2011-07-13
You can mark threads as solved from thread tools. I've done so for you. :)

Glad you got it working.

---

