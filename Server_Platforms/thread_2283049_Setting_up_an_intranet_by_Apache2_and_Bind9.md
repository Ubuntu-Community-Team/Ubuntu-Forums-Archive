---
title: "Setting up an intranet by Apache2 and Bind9"
date: 2015-06-18
forum: Server Platforms
---

### Post by Dario_de_Judicibus on 2015-06-18
I need some support to setup an intranet.


**ENVIRONMENT**


A LAN (192.168.1.x) conntected to Internet through an ADSL modem/router (192.168.1.1). 
An Ubuntu 14 server (192.168.1.111) is connected to the LAN too.


**WHAY I WISH TO DO**


Create an intranet domain (sample.lan) installing Apache2 and Bind9 on the server (server.sample.lan).
Apache2 will serve requests on port 80 for [www.sample.lan]("http://www.sample.lan") whereas w3.sample.lan will be redirected to server.sample.lan:888


**WHAT I DID **


1. I installed Apache2 and Bind9 on the server.
2. I created and configured a named.conf.options for bind9


```
    acl "trusted" {
        192.168.1.1;     # router
        192.168.1.111;    # server
    };


    options {
        directory "/var/cache/bind";


        recursion yes;                    
        allow-recursion { trusted; };    
        listen-on { 192.168.1.111; };    
        allow-transfer { none; };        


        forwarders {
            192.168.1.1;     # router
            8.8.8.8;        # Google
            91.80.35.166;    # ISP
        };


        dnssec-validation auto;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
    };

```

3. I created and configured a named.conf.local for bind9


```
    zone "sample.lan" {
        type master;
        file "/etc/bind/db.sample.lan";
    };


    zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
    };

```

4. I created and configured a db.sample.lan for bind9


```
    $TTL    604800
    @    IN    SOA    server.sample.lan. webmaster.sample.lan. (
                      3        ; Serial
                 604800        ; Refresh
                  86400        ; Retry
                2419200        ; Expire
                 604800 )    ; Negative Cache TTL
    ;
        IN    NS    server.sample.lan.
    ; Below are A Record addresses
    gateway.sample.lan.        IN    A    192.168.1.1
    server.sample.lan.        IN    A    192.168.1.111
    www.sample.lan.            IN    A    192.168.1.111
    w3.sample.lan.            IN    A    192.168.1.111
    ; Below are CNAME records addresses
    www.sample.lan.        IN    CNAME    sample.lan.

```

5. I created and configured a db.192 for bind9


  ```
  $TTL    604800
    @    IN    SOA    server.sample.lan. webmaster.sample.lan. (
                      3        ; Serial
                 604800        ; Refresh
                  86400        ; Retry
                2419200        ; Expire
                 604800 )    ; Negative Cache TTL
    ; name servers - NS records
        IN    NS    server.sample.lan.
    ; PTR records
    1    IN    PTR    gateway.sample.lan.
    111    IN    PTR    server.sample.lan.

```

6. I created and configured a httpd.conf for apache2


    ```
ServerName localhost

```

7. I created and configured a 000-default.conf for apache2 and activated by a2ensite command


    ```
<VirtualHost *:80>
        ServerAdmin webmaster@sample.lan
        ServerName www.sample.lan
        ServerAlias sample.lan
        DocumentRoot /var/www/html
        <Directory /var/www/html>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
            Order Allow,Deny
            Allow from All
        </Directory>
        LogLevel warn
        ErrorLog ${APACHE_LOG_DIR}/www.error.log
        CustomLog ${APACHE_LOG_DIR}/www.access.log combined
    </VirtualHost>

```

8. I created and configured a 001-w3.conf for apache2 and activated by a2ensite command


    ```
<VirtualHost *:80>
        ServerAdmin webmaster@sample.lan
        ServerName w3.sample.lan
        DocumentRoot /var/www/w3/
        <Directory /var/www/w3>
            AllowOverride None
            Order Deny,Allow
            Deny from All
        </Directory>
        <Proxy *>
            Order allow,deny
            Allow from all
        </Proxy>
        ProxyPass / http://server.sample.lan:888/
        ProxyPassReverse / http://server.sample.lan:888/
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/w3.access.log combined
    </VirtualHost>

```

I restarted/reloaded services when needed, rebooted when needed.


**RESULTS**


I can access server.sample.lan:888 but if I try to access


  ```
  www.sample.lan
    w3.sample.lan
    sample.lan

```

no page is loaded. What I did wrong?

---

### Post by darkod on 2015-06-19
Are your clients using the server as dns server? Don't forget, a public dns has no idea how to resolve those urls. Your router also.

PS. I would start with confirming dns works fine. Do you get the server ip as result if you run from a workstation:
nslookup www.sample.lan
nslookup w3.sample.lan

---

### Post by Dario_de_Judicibus on 2015-06-19
Of course clients have the server as primary DNS, the router as secondary DNS, but the problem occurs ALSO on the server itself, if I try to access those URLs from a browser. So it should be some DETAIL in one of the conf files, but which one?

---

### Post by darkod on 2015-06-19
Hmmm, it all depends what is actually failing. If the server itself is its own dns, and there is error in bind config, it might not open the web page even though it's on the same machine. It doesn't know it is on the same machine.

That's why you need to verify your dns is correctly translating [www.sample.lan](www.sample.lan) to server ip (hostname). If that works, you can probably rule out bind error and focus on apache config.

If the dns doesn't work as expected, you need to fix that first before continuing checking out apache. One step at a time.

From your answer it remains unclear if your bind resolves correctly.

As for apache config, I'm not an expert on it, but once you are sure you have an error in the config, there will be others to help too. Usually it's best to check the default web page of apache, just to make sure it's working ok. Before you continued configuring your sites. That would have also shown if bind is correct or not. I don't know if you checked this or not.

---

### Post by Dario_de_Judicibus on 2015-06-19
OK. I will make a check on Thursday, as I am back to office. The default web page of Apache works fine. No problems to access localhost. I can access also server.sample.lan:888 with no problem.

---

### Post by darkod on 2015-06-19
I think you have an error in db.sample.lan. I didn't catch it right away since I don't know bind in details. Comparing with ubuntu documentation it looks like an error.

The zone "sample.lan" from named.conf.local (or the forward zone file) specifies the domain you are configuring (in your case sample.lan). After that in db.sample.lan for the A records you include only the hostname without the domain suffix. Also the second line of db.sample.lan has a mistake which might be crucial. You do not put the server FQDN, you put just the domain and webmaster email. So your db.sample.lan should be something like:
```
@   IN   SOA   sample.lan. webmaster.sample.lan.   (
........
gateway   IN   A   192.168.1.1
server   IN   A   192.168.1.111
www   IN   A   192.168.1.111
w3   IN   A   192.168.1.111
.........
(you get the point)
```

Also your CNAME definition is wrong. On the left you put [www.sample.lan]("http://www.sample.lan") when on the left you put the "new, unexisting" name you want to alias to the name on the right. And again, you don't use the domain suffix. For example, instead of creating a w3 A record you can use:
```
w3   IN   CNAME   www
```

Don't forget, the name on the right in CNAME definition always has to exist as previously existing A record.

To alias sample.lan with [www.sample.lan]("http://www.sample.lan") (that's what you wanted with your CNAME definition), you simply create A record pointing to server IP:
```
@   IN   A   192.168.1.111
```

In fact, in most cases you can have only @ as A record pointing to server IP, and then use CNAME for www, w3, and all other names you want to point to the same server IP.

Reference of what I had written above:
[https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)
[https://help.ubuntu.com/lts/serverguide/dns-references.html#dns-record-types](https://help.ubuntu.com/lts/serverguide/dns-references.html#dns-record-types)

Hope it helps...

PS. You also have an error in your NS definition in db.sample.lan. You don't have the @ in front. It needs to be:
```
@   IN   NS   server.sample.lan.
```

---

### Post by Dario_de_Judicibus on 2015-06-19
Thank you Darko. So, if I understand correctly your suggestions, teh db.sample.lan configuration file should be
```

;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    sample.lan. webmaster.sample.lan. (
                  4        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL


@            IN    NS    server.sample.lan


; Below are A Record addresses


@            IN    A    192.168.1.111
gateway        IN    A    192.168.1.1
server        IN    A    192.168.1.111
www            IN    A    192.168.1.111
w3            IN    A    192.168.1.111


; Below are CNAME records addresses
w3            IN    CNAME    www

```

---

### Post by darkod on 2015-06-19
Yes, but there are again two errors:

1. In the NS definition you forgot the dot at the end, it needs to finish in a dot like server.sample.lan.

2. For w3 you either use the A record or the CNAME, not both.

---

### Post by Dario_de_Judicibus on 2015-06-23
Darko, thanks to your suggestions, I was able to fix the "bind" configuration. I can see now [www.sample.lan]("http://www.sample.lan"), server.sample.lan, and w3.sample.lan. Now the problem is Apache. In fact, all those URLs take me to the same page, the default Apache page. However, I wish to use w3.sample.lan as an alias of server.sample.lan:888 which takes to a specific application.

I can access that application by server.sample.lan:888, [www.sample.lan:888]("http://www.sample.lan:888"), and EVEN w3.sample.lan:888, but NOT from w3.sample.lan ONLY. I wish to redirect w3.sample.lan:80 to server.sample.lan:888, and I used the following configuration in sites-enabled, but it does not work. Where is the mistake?

```

<VirtualHost *:80>
        ServerAdmin [EMAIL="webmaster@sample.lan"]webmaster@sample.lan[/EMAIL]
        ServerName w3.sample.lan
        DocumentRoot /var/www/w3/
        <Directory /var/www/w3>
            AllowOverride None
            Order Deny,Allow
            Deny from All
        </Directory>
        <Proxy *>
            Order allow,deny
            Allow from all
        </Proxy>
        ProxyPass / [http://server.sample.lan:888/](http://server.sample.lan:888/)
        ProxyPassReverse / [http://server.sample.lan:888/](http://server.sample.lan:888/)
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/w3.access.log combined
    </VirtualHost>

```

---

### Post by darkod on 2015-06-23
You insist using port 80 for w3 too? Why not use port 888 in the vhost config and include it in the url / bookmark? Much cleaner...

---

### Post by Dario_de_Judicibus on 2015-06-24
Well, I have users that are confused by ports in URLs, so I wish to have a simple url like w3.sample.lan to access the application url that should be on port 888.  What exactly do you suggest to obtain that?

---

### Post by darkod on 2015-06-24
I am not apache expert... With a quick google search this is the only think I could find that looks like what you need:
[https://community.rackspace.com/products/f/18/t/1760](https://community.rackspace.com/products/f/18/t/1760)

According to that there needs to be a vhost definition for 888 (the other port) also. There is also a module to enable with a2enmod. Adjust it to your setup and give it a shot.

---

### Post by Dario_de_Judicibus on 2015-06-24
It worked! I had to enable the proxy and adda vhost def for 888. Great, darko, thank you.

---

### Post by darkod on 2015-06-24
Glad it worked. You can mark the thread solved in Thread Tools above the first post on any page.

---

