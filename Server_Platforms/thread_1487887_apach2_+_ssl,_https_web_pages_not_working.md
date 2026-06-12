---
title: "apach2 + ssl, https web pages not working"
date: 2010-05-19
forum: Server Platforms
---

### Post by Aruphonse on 2010-05-19
Hello everyone,

Im using Ubuntu Server 10.04 with, LAMP and OpenSSH installed, i need to configure
my site to serve both http and https.

I followed many configurations and tutorials with no ok results.
The last thing i tried was using the oficial documentation [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

It steps are enabling mod_ssl, then enable the default-ssl site, and finally restarting apache. After that the http works normally and https doesn't show up.

What i need is a guide or the steps or any help, to set up apache serving ssl and non-ssl content in ubuntu server 10.04.

I dont have a domain name yet, but i can access to the site through the public ip.

Thanks in advance,

---

### Post by cdenley on 2010-05-19
```

sudo a2enmod ssl
sudo a2ensite default-ssl
sudo service apache2 restart
sudo netstat -tlnp
nc -z -v -w 2 127.0.0.1 443
echo -e "GET / HTTP/1.0\n"|openssl s_client -quiet -connect 127.0.0.1:443
cat /etc/apache2/ports.conf

```

---

### Post by Aruphonse on 2010-05-19
After doing what you say i got the following results

The netstat comand
```

$sudo netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      719/mysqld      
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4114/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      760/sshd        
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      4114/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      760/sshd

```The netcat command
```

$nc -z -v -w 2 127.0.0.1 443
Connection to 127.0.0.1 443 port [tcp/https] succeded!

```The echo command
```

echo -e "GET / HTTP/1.0\n"|openssl s_client -quiet -connect 127.0.0.1:443
depth=0 /CN=hidden
verify error:num=18:self signed certificate
verify return:1
depth=0 /CN=hidden
HTTP/1.1 200 OK
Date: Wed, 19 May 2010 22:18:46 GMT
Server: Apache/2.2.14 (Ubuntu)
Last-Modified: Tue, 18 May 2010 19:51:39 GMT
ETag: "a00a26-aa-486e3ab7d2bfd"
Accept-Ranges: bytes
Content-Length: 170
Vary: Accept-Encoding
Connection: close
Content-Type: text/html
<html><body><h1>Happy Server</h1>
<p>Non Happy Ssl</p>
</body></html>

```And the ports.conf
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

Of what i can see everything seems fine ... but doing [https://myPublicIp](https://myPublicIp) from a remote computer won't show the webpage

What else can i do?

Thanks in advance,

---

### Post by cdenley on 2010-05-19
Are you on a LAN? Did you port forward 443? Did you configure your firewall to filter incoming connections? Are you attempting to connect to [https://publicip](https://publicip) from outside your LAN?

---

### Post by Aruphonse on 2010-05-20
I'm trying to access [https://myPublicIp](https://myPublicIp) from outside LAN,
I'm going to check if the port 443 is enabled for trafic ...

In any case i shouldn't need more configurations on apache, or is something else needed?

---

### Post by cdenley on 2010-05-20
> **Aruphonse said:**
> I'm trying to access [https://myPublicIp](https://myPublicIp) from outside LAN,
I'm going to check if the port 443 is enabled for trafic ...

In any case i shouldn't need more configurations on apache, or is something else needed?

The output you posted indicated you are serving encrypted content on port 443, and apache is listening for connections on all interfaces, so apache should be working correctly.

---

### Post by Aruphonse on 2010-05-20
Finally found the problem.
My ISP was blocking the https port.

After it was unblocked everything went fine.

Big thanx!

---

### Post by zappal on 2010-06-04
Not solved,
It seems close to a solution.
But now I just get a 404 Not Found when I try to view my site in SSL https mode
any ideas? :confused:

---

### Post by cdenley on 2010-06-04
> **zappal said:**
> Not solved,
It seems close to a solution.
But now I just get a 404 Not Found when I try to view my site in SSL https mode
any ideas? :confused:

This isn't your thread, and your problem isn't related. Either you configured apache wrong, or you're requesting a file that doesn't exist. If you still need help, create your own thread, and provide your configuration and the requests which result in a 404 error.

---

