---
title: "Ubuntu Server and Apache2"
date: 2011-04-03
forum: Server Platforms
---

### Post by nesneros on 2011-04-03
Hello,

So please do not mind my lack of Linux knowledge.  But what I have done is set up a linux server at my home, using Ubuntu server.  I have given the server a static IP as you can see below:
> 
nathan@SORENSENSVR1:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:20:a7:8d:32
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:62a5:f143:0:213:20ff:fea7:8d32/64 Scope:Global
          inet6 addr: fe80::213:20ff:fea7:8d32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:765242 (765.2 KB)  TX bytes:522599 (522.5 KB)


Next I have installed Apache2 and have configred a site to listen on port 1024.  I have forwarded all traffic requests for port 104 to go to the server.

> 
<VirtualHost *:1024>
        ServerAdmin [email]meh[/email]

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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


I have confirmed that the port is open by checking it here at this open port checker site: [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

I can of course access the testsite from all pcs on my LAN by either browsing to 192.168.1.30:1024 or even 98.165.241.67:1024 (keep in mind the public IP doesn't even leave the network as it hits my router and is like "oh damn this is my network")

So I am a little confused as to what is wrong.  Using a program called Fiddler2 to monitor traffic from an external PC (where I am at now, work) I see that when making a request to 98.165.241.67:1024 the site returns a 502 (Bad Gateway) sounds like traffic is not even making it past my router, any suggestions?



UPDATE:
So I found something somewhat interesting.  From my phone using the vrizon network, I am able to access 98.165.241.67:1024 with Opera, but with IE on my phone it fails.  Sounds like outside networks can possibly access the site, is this true?  Can anyone with an ISP other than COX Phoenix try to browse to 98.165.241.67:1024?

---

### Post by koenn on 2011-04-03
It seems to work, 
what was your question again ?

---

### Post by nesneros on 2011-04-03
> **koenn said:**
> It seems to work, 
what was your question again ?

So it indeed works, how very odd that I cannot access the site from an external network other than my home network.  Note that the network I am using now is in the same state and using the same ISP.

Here is what I get:

[IMG]http://www.googmuff.com/images/ss57.jpg[/IMG]

---

### Post by elico on 2011-04-03
try using:
[http://98.165.241.67:1024](http://98.165.241.67:1024)

1024 is not an http port so explorer is might confused about it.

and another idea is that if the ISP is using some proxy for caching it might cause this thing.

---

