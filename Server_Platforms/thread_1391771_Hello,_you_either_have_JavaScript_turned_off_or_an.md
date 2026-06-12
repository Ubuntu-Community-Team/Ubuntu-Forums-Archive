---
title: "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Playe"
date: 2010-01-27
forum: Server Platforms
---

### Post by dranick on 2010-01-27
Hello,

I have an Ubuntu server 9.10 set up as router on my network.

When accessing [www.youtube.com](www.youtube.com) from my Windows 7 box I get this error: 

```

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 

```

however if I connect the Windows box directly to the internet I can open Youtube just fine.

The server is set up to do ipv4_forward as I have a class allocated, routed directly (no masquerading). I don't have iptables installed on the linux box.

Please help.

Regards,

Nick

---

### Post by cdenley on 2010-01-27
Unless you're filtering web traffic on the router with squid or something, it wouldn't interfere with youtube. A simple router would treat all port 80 traffic the same, and leave anything flash or javascript related untouched.

---

### Post by dranick on 2010-01-27
I don't have any proxy cache software installed. All traffic goes directly through the router with no NAT or masquerading.

This is how the youtube page looks like:

[IMG]http://www.selfnet.org/1.jpg[/IMG]

Regards,

Nick

---

### Post by cdenley on 2010-01-27
Run these commands, then post the files result.txt and js.txt.
```

echo -e "GET /watch?v=bPfPK59weT8 HTTP/1.0\nHost: www.youtube.com\n"|nc www.youtube.com 80 > result.txt
echo -e "GET /yt/jsbin/www-csi-vfl139962.js HTTP/1.0\nHost: s.ytimg.com\n"|nc s.ytimg.com 80 > js.txt

```
Even better yet, post them for both with the router and without.

---

### Post by dranick on 2010-01-27
I can post the results.txt but when I run:

```

echo -e "GET /yt/jsbin/www-csi-vfl139962.js HTTP/1.0\nHost: s.ytimg.com\n"|nc s.ytimg.com 80 > js.txt

```

I get the following error:

```

 echo -e "GET /yt/jsbin/www-csi-vfl139962.js HTTP/1.0\nHost: s.ytimg.com\n"|nc s.ytimg.com 80 > js.txt
static.cache.l.google.com [82.137.43.21] 80 (www) : No route to host

```

and js.txt is empty.

The linux box is the router. I can't run the above commands in Windows.

Please see the attached results.txt

Nick

---

### Post by cdenley on 2010-01-27
> **dranick said:**
> I can post the results.txt but when I run:

```

echo -e "GET /yt/jsbin/www-csi-vfl139962.js HTTP/1.0\nHost: s.ytimg.com\n"|nc s.ytimg.com 80 > js.txt

```

I get the following error:

```

 echo -e "GET /yt/jsbin/www-csi-vfl139962.js HTTP/1.0\nHost: s.ytimg.com\n"|nc s.ytimg.com 80 > js.txt
static.cache.l.google.com [82.137.43.21] 80 (www) : No route to host

```

and js.txt is empty.

The linux box is the router. I can't run the above commands in Windows.

Please see the attached results.txt

Nick

Well then, that is your problem! You cannot connect to the web server "s.ytimg.com". That will result in the problem you are experiencing. Something is filtering traffic to that server on your network (assuming you configured the network interface correctly), because the "s.ytimg.com" server is working fine.

---

### Post by dranick on 2010-01-27
Thank you for your help. I have managed to find the issue. I had too many frames added on the same NIC.

Cheers,

Nick

---

