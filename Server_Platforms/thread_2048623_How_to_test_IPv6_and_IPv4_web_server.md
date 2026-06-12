---
title: "How to test IPv6 and IPv4 web server?"
date: 2012-08-27
forum: Server Platforms
---

### Post by THPubs on 2012-08-27
I have setup a web server (Nginx) and assigned an IPv4 address and an IPv6 address to it. In the DNS I have set an A record and an AAAA record. Now, I need to check whether its working. I need to check whether an IPv6 only client can view my site. Whether an IPv4 only client can view the site (I think IPv4 only clients can view because im IPv4 ).

How can I do this? I only have IPv4!

---

### Post by sandyd on 2012-08-27
Use something like [http://ipv6-test.com/validate.php](http://ipv6-test.com/validate.php)

You could also post the url - i have ipv6 here ;)

---

### Post by sanderj on 2012-08-27
> **THPubs said:**
> I have setup a web server (Nginx) and assigned an IPv4 address and an IPv6 address to it. In the DNS I have set an A record and an AAAA record. Now, I need to check whether its working. I need to check whether an IPv6 only client can view my site. Whether an IPv4 only client can view the site (I think IPv4 only clients can view because im IPv4 ).

How can I do this? I only have IPv4!

But your webserver has IPv6, hasn't it? Otherwise you can't usefully give it an IPv6 address and AAAA entry.


Post the URL (and IP addresses) here, and we can test it for you. Test is like below: with wget.

Or: use sixxs proxy service. To test [www.google.com](www.google.com), use this:
http://<your-ipv6-URL>.ipv4.sixxs.org/
That way you can access a IPv6-URL via your IPv4



```
sander@toverdoos:~$ 
sander@toverdoos:~$ wget -6 www.google.com
--2012-08-27 09:40:21--  http://www.google.com/
Resolving www.google.com... 2a00:1450:4007:803::1012
Connecting to www.google.com|2a00:1450:4007:803::1012|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.5'

    [ <=>                                                                                                  ] 10,910      --.-K/s   in 0s      

2012-08-27 09:40:21 (34.3 MB/s) - `index.html.5' saved [10910]

sander@toverdoos:~$ 
sander@toverdoos:~$ wget -4 www.google.com
--2012-08-27 09:40:24--  http://www.google.com/
Resolving www.google.com... 173.194.78.99, 173.194.78.105, 173.194.78.147, ...
Connecting to www.google.com|173.194.78.99|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.google.fr/ [following]
--2012-08-27 09:40:25--  http://www.google.fr/
Resolving www.google.fr... 173.194.78.94
Connecting to www.google.fr|173.194.78.94|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.6'

    [ <=>                                                                                                  ] 11,012      --.-K/s   in 0.001s  

2012-08-27 09:40:25 (15.6 MB/s) - `index.html.6' saved [11012]

sander@toverdoos:~$ wget www.google.com
--2012-08-27 09:40:30--  http://www.google.com/
Resolving www.google.com... 2a00:1450:4007:803::1012, 173.194.78.105, 173.194.78.147, ...
Connecting to www.google.com|2a00:1450:4007:803::1012|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.7'

    [ <=>                                                                                                  ] 10,934      --.-K/s   in 0.02s   

2012-08-27 09:40:30 (556 KB/s) - `index.html.7' saved [10934]

sander@toverdoos:~$ 

```

---

### Post by sanderj on 2012-08-27
PS:

You question makes me wonder: the webserver has full IPv6 connectivity, I hope? Easy way to check: Log in on the webserver with SSH, and then:

```
wget -6 www.google.com

```

should work on your webserver.

Yes, that is really the first check: has the webserver outside IPv6 connectivity?


And: see my signature how can you give your own Ubuntu system IPv6 connectivity too.

---

### Post by THPubs on 2012-08-27
> **sanderj said:**
> But your webserver has IPv6, hasn't it? Otherwise you can't usefully give it an IPv6 address and AAAA entry.


Post the URL (and IP addresses) here, and we can test it for you. Test is like below: with wget.

Or: use sixxs proxy service. To test [www.google.com](www.google.com), use this:
http://<your-ipv6-URL>.ipv4.sixxs.org/
That way you can access a IPv6-URL via your IPv4



```
sander@toverdoos:~$ 
sander@toverdoos:~$ wget -6 www.google.com
--2012-08-27 09:40:21--  http://www.google.com/
Resolving www.google.com... 2a00:1450:4007:803::1012
Connecting to www.google.com|2a00:1450:4007:803::1012|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.5'

    [ <=>                                                                                                  ] 10,910      --.-K/s   in 0s      

2012-08-27 09:40:21 (34.3 MB/s) - `index.html.5' saved [10910]

sander@toverdoos:~$ 
sander@toverdoos:~$ wget -4 www.google.com
--2012-08-27 09:40:24--  http://www.google.com/
Resolving www.google.com... 173.194.78.99, 173.194.78.105, 173.194.78.147, ...
Connecting to www.google.com|173.194.78.99|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.google.fr/ [following]
--2012-08-27 09:40:25--  http://www.google.fr/
Resolving www.google.fr... 173.194.78.94
Connecting to www.google.fr|173.194.78.94|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.6'

    [ <=>                                                                                                  ] 11,012      --.-K/s   in 0.001s  

2012-08-27 09:40:25 (15.6 MB/s) - `index.html.6' saved [11012]

sander@toverdoos:~$ wget www.google.com
--2012-08-27 09:40:30--  http://www.google.com/
Resolving www.google.com... 2a00:1450:4007:803::1012, 173.194.78.105, 173.194.78.147, ...
Connecting to www.google.com|2a00:1450:4007:803::1012|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.7'

    [ <=>                                                                                                  ] 10,934      --.-K/s   in 0.02s   

2012-08-27 09:40:30 (556 KB/s) - `index.html.7' saved [10934]

sander@toverdoos:~$ 

```

Hi, Thanks a lot for the help :) The site's address is : techhamlet.com
ip4 : 37.247.48.92
ip6 : 2a00:dcc0:eda:3748:247:48:90:2

---

### Post by sanderj on 2012-08-27
Both IPv4 and IPv6 work correctly. See below


```
sander@toverdoos:~$ wget -4 techhamlet.com
--2012-08-27 11:42:37--  http://techhamlet.com/
Resolving techhamlet.com... 37.247.48.92
Connecting to techhamlet.com|37.247.48.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.8'

    [  <=>                                                                                                 ] 58,129       220K/s   in 0.3s    

2012-08-27 11:42:38 (220 KB/s) - `index.html.8' saved [58129]

sander@toverdoos:~$ 
sander@toverdoos:~$ wget -6 techhamlet.com
--2012-08-27 11:42:42--  http://techhamlet.com/
Resolving techhamlet.com... 2a00:dcc0:eda:3748:247:48:90:2
Connecting to techhamlet.com|2a00:dcc0:eda:3748:247:48:90:2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.9'

    [  <=>                                                                                                 ] 58,129       208K/s   in 0.3s    

2012-08-27 11:42:43 (208 KB/s) - `index.html.9' saved [58129]

sander@toverdoos:~$ 

```

---

### Post by THPubs on 2012-08-27
> **sanderj said:**
> Both IPv4 and IPv6 work correctly. See below


```
sander@toverdoos:~$ wget -4 techhamlet.com
--2012-08-27 11:42:37--  http://techhamlet.com/
Resolving techhamlet.com... 37.247.48.92
Connecting to techhamlet.com|37.247.48.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.8'

    [  <=>                                                                                                 ] 58,129       220K/s   in 0.3s    

2012-08-27 11:42:38 (220 KB/s) - `index.html.8' saved [58129]

sander@toverdoos:~$ 
sander@toverdoos:~$ wget -6 techhamlet.com
--2012-08-27 11:42:42--  http://techhamlet.com/
Resolving techhamlet.com... 2a00:dcc0:eda:3748:247:48:90:2
Connecting to techhamlet.com|2a00:dcc0:eda:3748:247:48:90:2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.9'

    [  <=>                                                                                                 ] 58,129       208K/s   in 0.3s    

2012-08-27 11:42:43 (208 KB/s) - `index.html.9' saved [58129]

sander@toverdoos:~$ 

```

Perfect! Thanks a lot my friend! Now I understand the tests :)

---

### Post by sanderj on 2012-08-27
You said your own desktop hasn't IPv6? If it is Ubuntu (or Debian), can you

```
sudo apt-get install miredo
```


and then do the same two wget tests?

---

### Post by THPubs on 2012-08-27
> **sanderj said:**
> You said your own desktop hasn't IPv6? If it is Ubuntu (or Debian), can you

```
sudo apt-get install miredo
```


and then do the same two wget tests?

It works! I can even visit [http://ipv6.google.com/](http://ipv6.google.com/) :) What is that program?

---

### Post by sanderj on 2012-08-27
> **THPubs said:**
> It works! I can even visit [http://ipv6.google.com/](http://ipv6.google.com/) :) What is that program?

Miredo / Teredo is an automatic tunnel of IPv6 over IPv4. It is not as good as native IPv6 (it can be a bit shaky, your IPv6 address changes), but it is good enough for your first steps into Ipv6.

---

### Post by hawkmage on 2012-08-27
I use a free 6in4 tunnel Hurricane Electric for my IPv6 access since my ISP doesn't support it yet.  I had an Ubuntu server acting as the tunnel endpoint until I got it set-up on my firewall.  It is fairly easy to set up and works well.

---

