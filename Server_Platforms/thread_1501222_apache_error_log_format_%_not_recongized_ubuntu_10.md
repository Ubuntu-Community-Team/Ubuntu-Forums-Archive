---
title: "apache error log format % not recongized ubuntu 10.04"
date: 2010-06-04
forum: Server Platforms
---

### Post by tapas_mishra on 2010-06-04
Hi
 I wanted to log some messages on Apache.
So I added in VirtualHost definition
```

CustomLog /var/log/apache2/site-resp_log resp
LogFormat "%{X-Forwarded-For} %D %t %T %v %O %b %A %B" resp

```

and restarted apache2.
I got following error
```

* Restarting web server apache2
Syntax error on line 33 of /etc/apache2/sites-enabled/site.com:
Unrecognized LogFormat directive % [fail]
root@server:/var/log/apache2# vi /etc/apache2/sites-available/sites.com


```
Here is a[ page]("https://httpd.apache.org/docs/2.2/mod/mod_log_config.html") I referred to.
I am not able to understand the syntax error can some one point me to right thing.

---

### Post by tapas_mishra on 2010-06-04
Ok here is what I found if I am removing 
%{X-Forwarded-For}
then every thing is working fine.
But I am using a reverse proxy environment.So 
I deleted every thing from above two lines in VirtualHost definition
```

CustomLog /var/log/apache2/site-resp_log resp
LogFormat "%D %t %T %v %O %b %A %B" resp

```
is working without any problem
but if I add
```

LogFormat "%{X-Forwarded-For} %D %t %T %v %O %b %A %B" resp

```
I am getting error any clues ?

---

### Post by tapas_mishra on 2010-06-04
Ok got the mistake 
I had to use
```

%{X-Forwarded-For}i

```
and not 
```

%{X-Forwarded-For}

```

Thanks every one.For reading.

---

