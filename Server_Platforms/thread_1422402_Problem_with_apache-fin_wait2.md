---
title: "Problem with apache-fin_wait2"
date: 2010-03-05
forum: Server Platforms
---

### Post by stanics on 2010-03-05
I installed Ubuntu server edition and LAMP PACKAGE on it. I configurates my router to redirect requests on server. 
Address for accessing the server is [http://ured.maglaj.net](http://ured.maglaj.net)
Everything works perfectly from local network, but from outside everythnig works except for the images. 
When requests from outside arrived for photo on the server, net stat shows fin_wait2.
 
I can't find the problem since everything works perfectly in LAN (photos loading also).

---

### Post by cdenley on 2010-03-05
We need more information. What happens when an image is requested? Does the server return an error? What is the error code? It would also help us help you if you provided the path of any page or image you are attempting to access.
```

tail /var/log/apache2/error.log

```

---

### Post by stanics on 2010-03-05
[SIZE=2]here is this:[/SIZE]
 
[SIZE=2]1. Attempt to open [http://ured.maglaj.net](http://ured.maglaj.net) now! [/SIZE][SIZE=2]You'll see a PHP file and a picture (logo.jpg)[/SIZE]
[SIZE=2]2. [/SIZE][SIZE=2]From the LAN I can see a picture and content php file, but with the internet I can only see a php file or text content, but the picture NO.[/SIZE]
 
[SIZE=2]error.log - no mistakes.[/SIZE]
 
[SIZE=2]I used the command > netstat --inet and I saw the error fin_wait2 when the request comes from the Internet(only request for a picture)[/SIZE]

[SIZE=2][/SIZE] 
[SIZE=2]**UPDATE**[/SIZE]
Now, when I reopened error.log, this is the result:
 

> [Fri Mar 05 19:40:05 2010] [error] [client 192.168.100.252] request failed: error reading the headers
[Fri Mar 05 19:40:23 2010] [error] [client 192.168.100.252] File does not exist: /var/www/roditelji/HTlogo.jpg

---

### Post by cdenley on 2010-03-05
That is odd indeed.
```

cdenley@ubuntu:~$ echo -e "GET /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 80
cdenley@ubuntu:~$ echo -e "HEAD /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 80 
HTTP/1.1 200 OK
Date: Fri, 05 Mar 2010 18:50:27 GMT
Server: Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch
Last-Modified: Tue, 02 Jun 2009 07:46:48 GMT
ETag: "81ca5-883c-46b58beba0a00"
Accept-Ranges: bytes
Content-Length: 34876
Connection: close
Content-Type: image/jpeg

```
Your ISP must be filtering it somehow. I wonder if the requests are getting through to your server.
```

echo -e "HEAD /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 80
echo -e "GET /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 80
tail -n 2 /var/log/apache2/access.log

```

---

### Post by stanics on 2010-03-05
first of all thanks for your help
 
these are results of this commands:
1.)echo -e "HEAD /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 
> invalid wait-time ured.maglaj.net
bash: echo: write error: Broken pipe
 
2.) echo -e "GET /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 80
> invalid wait-time ured.maglaj.net
bash: echo: write error: Broken pipe

---

### Post by cdenley on 2010-03-05
> **stanics said:**
> first of all thanks for your help
 
these are results of this commands:
1.)echo -e "HEAD /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 

 
2.) echo -e "GET /logo.jpg HTTP/1.0\n"|nc -w 3 ured.maglaj.net 80

The commands you posted are correct (except for the missing 80 at the end on #1), but judging from the output, the commands you actually ran were not. I tested them on both hardy and karmic, and they work as expected. No broken pipes or invalid wait times. Try running all 3 commands in order exactly as I posted them, and if you still have trouble, post the output for the command below.
```

lsb_release -id

```

---

### Post by stanics on 2010-03-05
I run this command directly from the server in LAN
 
> root@desk:/home/nina# echo -e "HEAD /logo.jpg HTTP/1.0\n"|nc -w ured.maglaj.net 80
invalid wait-time ured.maglaj.net
bash: echo: write error: Broken pipe

 
 
> root@desk:/home/nina# lsb_release -id
Distributor ID: Ubuntu
Description: Ubuntu 9.04
 
Do you want that I send you ssh access to a private message

---

### Post by cdenley on 2010-03-05
> **stanics said:**
> I run this command directly from the server in LAN

That is NOT the command I posted! You're missing a "3".

---

### Post by cdenley on 2010-03-05
Your server is working fine. You appear to have a port forwarding issue. I don't think your router is configured properly.

---

