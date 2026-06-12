---
title: "[SOLVED] Apache2 doesn't appear to serve &amp;gt;2gb files?"
date: 2008-07-24
forum: Server Platforms
---

### Post by SJI on 2008-07-24
Hello everyone,

I'm grabbing some files from a  local server and everything is fine until I try to grab a file that's larger than 2gb.

Is there a config item somewhere for apache2 that allows it to serve > 2gb files?

Many thanks,

Stephen

---

### Post by weegee101 on 2008-07-24
What version of apache2 are you using?

---

### Post by hrod beraht on 2008-07-24
Yeah, what's your Apache version?
>2GB file support is a feature that was [[COLOR="Blue"]added in version 2.2[/COLOR]]("http://httpd.apache.org/docs/2.1/new_features_2_2.html")

Bob

---

### Post by SJI on 2008-07-24
Apache2 reports:

Server version: Apache/2.2.8 (Ubuntu)
Server built:   Jun 25 2008 13:54:13

---

### Post by weegee101 on 2008-07-25
Can you post a tail of your error_log after trying to download the file in question?

---

### Post by SJI on 2008-07-25
There's no entry in error.log for the action.

I've just tried grabbing a <2gb file and a >2gb file and I get the same "OK" entries in access.log.

```
192.168.0.2 - - [25/Jul/2008:14:56:23 +0100] "GET /store.tar HTTP/1.1" 200 21165047 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727; .NET CLR 3.0.04506.648; .NET CLR 3.5.21022; InfoPath.2)"
```

```
192.168.0.2 - - [25/Jul/2008:14:56:38 +0100] "GET /twbb.tar HTTP/1.1" 200 4541383374 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727; .NET CLR 3.0.04506.648; .NET CLR 3.5.21022; InfoPath.2)"
```

It's looking more like a problem with a windows client than the ubuntu server itself.

---

### Post by SJI on 2008-07-25
It seems that IE7 will accept a file of upto 4294967295 bytes from the apache2 server ok, but anything of 4294967296 and above are met with a 

"Internet Explorer cannot display the webpage 
   
   Most likely causes:
You are not connected to the Internet. 
The website is encountering problems. 
There might be a typing error in the address."

I'll mark this thread as solved as it doesn't seem to be a problem with apache itself.

---

