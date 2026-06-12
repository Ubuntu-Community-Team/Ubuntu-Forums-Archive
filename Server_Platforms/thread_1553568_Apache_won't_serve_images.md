---
title: "Apache won't serve images"
date: 2010-08-15
forum: Server Platforms
---

### Post by xianic on 2010-08-15
Hi
I've just set up a Ubuntu 10.04 LAMP server and put a couple of websites on it. It Seems to be working fine except that it won't serve any images. The strange thing is that it reports to have served it correctly: 

```

xian@valcan:~$ cat get_people.gif.http 
GET /tmp/people.gif HTTP/1.1
Host: domain.name.changed.for.forum

xian@valcan:~$ nc localhost 80 < get_people.gif.http | wc -c
0
xian@valcan:~$ tail -n 1 /var/log/apache2/ttaber-access.log 
127.0.0.1 - - [15/Aug/2010:14:03:18 +0100] "GET /tmp/people.gif HTTP/1.1" 200 3787 "-" "-"
xian@valcan:~$

```It apparently served a 3787 byte response which was not received by netcat! Not even headers. It's not the usual - permission etc as there is no line in the error log about this request.

This has me stumped. Any help would be appreciated.
Thanks in advance.

---

### Post by stlsaint on 2010-08-15
Does root have owner permissions to your /var/www directory?

---

### Post by xianic on 2010-08-15
Root owns /var/www and has 755 permissions. Virtual hosts are set up and /var/www is not used by anything.
I just tried copying the people.gif file to peope.css with same permissions (another css file in the same directory works fine) and Apache will serve people.css fine (gif data with content-type: text/css header).

---

### Post by FreedomOverdose on 2010-08-15
could you check your headers (with some tool like live http headers) while you're browsing the page? What are they?

---

### Post by xianic on 2010-08-15
From firebug the request headers are:
```

Host: domain.name.changed.for.forum
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-gb,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive
Referer: http://domain.name.changed.for.forum/tmp/

```There are no response headers.

---

### Post by xianic on 2010-08-16
An update: I tried the request using Fiddler to inspect the response and it is sending the GIF data but with no headers. Response begins: GIF89a...

---

### Post by koenn on 2010-08-16
does it work for other images ?

do you have an image/gif mime type  (somewhere in the relevant apache config fil) ?

---

### Post by xianic on 2010-08-17
I've just solved it by disabling sendfile in the Apache configuration.
See [http://ubuntuforums.org/showthread.php?t=1385583](http://ubuntuforums.org/showthread.php?t=1385583) it's the same problem.

---

