---
title: "Setting up name-based virtual hosts on Apache Apache/2.4.6 (Ubuntu 12)"
date: 2013-12-11
forum: Server Platforms
---

### Post by vsiege2 on 2013-12-11
SETUP:
[B]Apache/2.4.6
Ubuntu 12.x[/B]

I am having trouble setting up any virtual hosts on my LAN. I want to have multiple name based virtual hosts. The first example vhost i am setting up is days.com. Unfortunately, when I type that address, **Apache/2.4.6** does not redirect the address to the vhost. 


Heres my days.com.conf (enabled) in **/etc/apache2/sites-available**:


```
<VirtualHost *:80>
        ServerName days.com
        ServerAlias www.days.com


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/zzz


        #ErrorLog ${APACHE_LOG_DIR}/error.log
        #CustomLog ${APACHE_LOG_DIR}/access.log combined


        <Directory />
                Options All
                AllowOverride All
                Require all granted
        </Directory>
</VirtualHost>
```

I enabled it using:
```
sudo a2ensite days.com.conf
sudo service apache2 reload
 * Reloading web server apache2 
```
If I run the following command I get this response:
```
apachectl -S

```VirtualHost configuration:
```
*:80                   is a NameVirtualHost
         default server localhost (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost localhost (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost days.com (/etc/apache2/sites-enabled/days.com.conf:1)
                 alias www.days.com

```

Heres my **/etc/hosts** file setup:
```

#127.0.0.1      localhost
#Virtual Hosts
127.0.0.1       days.com www.days.com duck.dev
days.com        days.com www.days.com
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-l   ocalnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

What am I doing wrong?

FYI: 
The only two conf files in **/etc/apache2/sites-available** and **/etc/apache2/sites-****enabled** are:
```
[I]000-default.conf
days.com.conf[/I]
```

---

### Post by CharlesA on 2013-12-11
Remove this line:

```
days.com        days.com www.days.com
```

The hosts file is only used for ip address to host name resolution.

---

### Post by vsiege2 on 2013-12-12
OK. I removed that line, but my vhost is not working yet. Here's exactly what i did:
Removed this line from /etc/hosts :
```
days.com        days.com [www.days.co]("http://www.days.co")m
```

Reloaded apache2.4.6:
```
:~$ sudo service apache2 reload
 * Reloading web server apache2                                                                                                                                                                              * 
```

IN my browser:
1. Cleared cache
2. Typed [www.days.com]("http://www.days.com") in address field

FYI: I also tried:
```
[COLOR=#000000][FONT=Verdana]sudo service apache2 restart
[/FONT][/COLOR]* Restarting web server apache2 
```

---

### Post by CharlesA on 2013-12-12
What does it say after you try to access days.com ?

Run this after you try to access it:

```
tail /var/log/apache2/access.log
```

I think that's right, I don't use Apache, so I'm not 100% sure.

---

### Post by vsiege2 on 2013-12-12
I don't see anything get updated in the access log when I type: [http://days.com](http://days.com) or days.com or [www.days.com](www.days.com)

The only things that appear:
```
127.0.0.1 - - [12/Dec/2013:12:14:57 -0800] "OPTIONS * HTTP/1.0" 200 125 "-" "Apache/2.4.6 (Ubuntu) PHP/5.5.6-1+debphp.org~precise+2 (internal dummy connection)"127.0.0.1 - - [12/Dec/2013:12:14:57 -0800] "OPTIONS * HTTP/1.0" 200 125 "-" "Apache/2.4.6 (Ubuntu) PHP/5.5.6-1+debphp.org~precise+2 (internal dummy connection)"
127.0.0.1 - - [12/Dec/2013:12:14:57 -0800] "OPTIONS * HTTP/1.0" 200 125 "-" "Apache/2.4.6 (Ubuntu) PHP/5.5.6-1+debphp.org~precise+2 (internal dummy connection)"
127.0.0.1 - - [12/Dec/2013:12:14:57 -0800] "OPTIONS * HTTP/1.0" 200 125 "-" "Apache/2.4.6 (Ubuntu) PHP/5.5.6-1+debphp.org~precise+2 (internal dummy connection)"
127.0.0.1 - - [12/Dec/2013:12:14:57 -0800] "OPTIONS * HTTP/1.0" 200 125 "-" "Apache/2.4.6 (Ubuntu) PHP/5.5.6-1+debphp.org~precise+2 (internal dummy connection)"
192.168.16.170 - - [12/Dec/2013:13:48:13 -0800] "GET /fake/dev/ HTTP/1.1" 200 735 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36"
192.168.16.170 - - [12/Dec/2013:13:48:13 -0800] "GET /favicon.ico HTTP/1.1" 404 502 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36"
192.168.16.170 - - [12/Dec/2013:13:52:46 -0800] "GET /fake/dev/ HTTP/1.1" 200 735 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36"
192.168.16.170 - - [12/Dec/2013:13:52:47 -0800] "GET /fake/dev/ HTTP/1.1" 200 734 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36"
192.168.16.170 - - [12/Dec/2013:13:53:42 -0800] "GET /fake/dev/ HTTP/1.1" 200 735 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36"
```

---

### Post by CharlesA on 2013-12-12
What machine are you trying to access the days.com site from?

---

### Post by vsiege2 on 2013-12-13
Im accessing the address from another box on my LAN. Its a mac. The Ubuntu server has a static IP while everything else has a dynamic IP. I'm actually kind of amazed it's taken me this long to get this working. If I type the address of the server in, then put the relevant directory, I can see the site located in www directory.

---

### Post by CharlesA on 2013-12-13
> **vsiege2 said:**
> Im accessing the address from another box on my LAN. Its a mac. The Ubuntu server has a static IP while everything else has a dynamic IP. I'm actually kind of amazed it's taken me this long to get this working. If I type the address of the server in, then put the relevant directory, I can see the site located in www directory.

Which machine were you modifying the hosts file on?

---

### Post by pascalfares on 2013-12-13
what is the result of this command?

dig days.com ?

---

### Post by vsiege2 on 2013-12-13
I was modifying the ubuntu server hosts file over ssh from my osx box


DIG:

; <<>> DiG 9.8.1-P1 <<>> days.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44317
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;days.com.            IN    A


;; ANSWER SECTION:
days.com.        3600    IN    A    xx.xxx.xx.xx


;; Query time: 6 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Dec 13 11:12:36 2013
;; MSG SIZE  rcvd: 42

---

### Post by CharlesA on 2013-12-13
> **vsiege2 said:**
> I was modifying the ubuntu server hosts file over ssh from my osx box

You need to modify the hosts file of whatever machine you are accessing the test machine from, as it is local only.

---

### Post by vsiege2 on 2013-12-16
Thank you. I have it up and running now. The only thing thats not getting picked up from the hosts file is the wildcard I have added for any subdomains for *.days.com

```

127.0.0.1      localhost


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-l   ocalnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
iff02::2 ip6-allrouters


#Virtual Hosts
127.0.0.1       days.com www.days.com *.days.com

```

---

### Post by CharlesA on 2013-12-16
> **vsiege2 said:**
> Thank you. I have it up and running now. The only thing thats not getting picked up from the hosts file is the wildcard I have added for any subdomains for *.days.com

```

127.0.0.1      localhost


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-l   ocalnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
iff02::2 ip6-allrouters


#Virtual Hosts
127.0.0.1       days.com www.days.com *.days.com

```

As far as I know, you can't use wildcards in the hosts file, so you would need to reference each subdomain individually.

---

