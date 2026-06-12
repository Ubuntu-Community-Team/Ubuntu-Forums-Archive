---
title: "A question on running &quot;svn co ..&quot;"
date: 2008-05-03
forum: Server Platforms
---

### Post by satimis on 2008-05-03
Hi folks,


Ubuntu 6.05.3 drake amd64


On running

$ svn co [http://LAMP/svn](http://LAMP/svn)```

svn: PROPFIND request failed on '/svn'
svn: PROPFIND of '/svn': Could not resolve hostname `LAMP': Host not found (http://LAMP)

```


However LAMP is the ServerName


$ cat /etc/apache2/httpd.conf | grep ServerName```

ServerName LAMP

```


"lampserver" is hostname

$ hostname
lampserver

$ hostname -f
lampserver


Please advise where shall I correct?  TIA


B.R.
satimis

---

### Post by ghostknife on 2008-05-03
You don't have the name "lamp" inside /etc/hosts

Add a line to this file reading:
[ip address] lamp

The ServerName in apache configuration is a way for apache to know which virtual host to load when the client sends a specific name. It has nothing to do with resolving. When you do a request to a hostname, ie "lamp", it first needs to resolve to an IP, for the software to know where to connect.

After this connection to the IP has been established the client software will tell the Apache server it connected to "Please give me /svn on the server named LAMP".

---

### Post by ghostknife on 2008-05-03
You don't have the name "lamp" inside /etc/hosts

Add a line to this file reading:
[ip address] lamp

The ServerName in apache configuration is a way for apache to know which virtual host to load when the client sends a specific name. It has nothing to do with resolving. When you do a request to a hostname, ie "lamp", it first needs to resolve to an IP, for the software to know where to connect.

After this connection to the IP has been established the client software will tell the Apache server it connected to "Please give me /svn on the server named LAMP".

---

### Post by satimis on 2008-05-04
> **ghostknife said:**
> You don't have the name "lamp" inside /etc/hosts

Add a line to this file reading:
[ip address] lamp

The ServerName in apache configuration is a way for apache to know which virtual host to load when the client sends a specific name. It has nothing to do with resolving. When you do a request to a hostname, ie "lamp", it first needs to resolve to an IP, for the software to know where to connect.

After this connection to the IP has been established the client software will tell the Apache server it connected to "Please give me /svn on the server named LAMP".
Thanks for your advice.


At this junction I expect to clarify follow first.

Whether ServerName is the hostname?

$ cat /etc/hosts```

127.0.0.1       localhost
127.0.1.1       lampserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


If YES, then I have to change;

$ cat /etc/apache2/httpd.conf```

ServerName lampserver

```

There is only ONE line on this file.  Thanks


B.R.
satimis

---

### Post by ghostknife on 2008-05-04
Correct, ServerName has to be resolvable to an IP address. If you have more than one name you want to use to open the same host, you put the primary name inside "ServerName", and the rest of the names inside "ServerAlias". Ex.

ServerName lampserver
ServerAlias lamp [www.lamp](www.lamp) [www.lampserver](www.lampserver)

Then all 4 lampserver, lamp, [www.lamp](www.lamp), [www.lampserver](www.lampserver) will open the virtual host. Note they will only work if each of them can resolve to the server's IP address.

Also note that the /etc/hosts file will only apply to the local machine. If you want other machines to be able to type "lampserver" to get to your virtual host, you need ot add it to their hosts files, or add it to a DNS server.

---

### Post by satimis on 2008-05-04
Hi ghostknife,


I'm following;
Version Control System
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/version-control-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/version-control-system.html)

to perform this test.


Steps performed previously;


Creating Environments:-

$ sudo mkdir /var/lib/svn

$ sudo mkdir /var/lib/svn/lamp

Remark:
svn = repos
lamp = ProjectName


$ sudo svnadmin create /var/lib/svn/lamp

$ svn co file:///var/lib/svn/lamp```

Checked out revision 0.

```


$ svn co file://localhost/var/lib/svn/lamp```

svn: 'lamp' is already a working copy for a different URL

```


In order to make things simple I retain ONE ServerName.


Edit /etc/apache2/httpd.conf

changing```

ServerName lampserver

```


$ sudo /etc/init.d/apache2 force-reload```

 * Forcing reload of apache 2.0 web server...                                   Apache/2.0.55 mod_ssl/2.0.55 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide us with the pass phrases.

Server lampserver:443 (RSA)
Enter pass phrase:

Ok: Pass Phrase Dialog successful.
                                                                         [ ok ]

```


$ svn co [http://lampserver/svn](http://lampserver/svn)```

svn: PROPFIND request failed on '/svn'
svn: PROPFIND of '/svn': Could not read status line: connection was closed by server. (http://lampserver)

```
Still fail.


However;

$ svn co [https://lampserver/svn](https://lampserver/svn)```

Error validating server certificate for 'https://lampserver:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
 - The certificate hostname does not match.
Certificate information:
 - Hostname: Stephen
 - Valid: from May  3 03:47:58 2008 GMT until May  3 03:47:58 2009 GMT
 - Issuer: IT, Satimis, HK
 - Fingerprint: 0c:3a:2f:08:a6:15:ff:24:28:6b:fb:52:7f:5d:6a:28:20:e9:c9:6e
(R)eject, accept (t)emporarily or accept (p)ermanently? svn: PROPFIND request fa
iled on '/svn'

```
"https" works but NOT "http".  Strange?


Because I have no idea what to select, just cancel it wiht [Ctrt]+C.  It prompts```

 PROPFIND request fa
iled on '/svn'
svn: PROPFIND of '/svn': Server certificate verification failed: certificate iss
ued for a different hostname, issuer is not trusted (https://lampserver)

```

Please advise how to fix the problem.  What shall I select?  TIA


> 
Correct, ServerName has to be resolvable to an IP address. 

What IP address I have enter on /etc/hosts?

Now
$ cat /etc/hosts```

127.0.0.1       localhost
127.0.1.1       lampserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


> 
If you have more than one name you want to use to open the same host, you put the primary name inside "ServerName", and the rest of the names inside "ServerAlias". Ex.

ServerName lampserver
ServerAlias lamp [www.lamp](www.lamp) [www.lampserver](www.lampserver)

Then all 4 lampserver, lamp, [www.lamp](www.lamp), [www.lampserver](www.lampserver) will open the virtual host. Note they will only work if each of them can resolve to the server's IP address.

Noted with thanks.


> 
Also note that the /etc/hosts file will only apply to the local machine. If you want other machines to be able to type "lampserver" to get to your virtual host, you need ot add it to their hosts files, or add it to a DNS server.
Could you please explain in more detail?  Thanks


B.R.
satimis

---

