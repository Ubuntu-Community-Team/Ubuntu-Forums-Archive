---
title: "htaccess less hardcoded"
date: 2011-03-02
forum: Server Platforms
---

### Post by elad2109 on 2011-03-02
Hello,

I write server-side code.
There is a web-site which asks for a file named old.png
I want the server to check the reffere url. If it's [http://www.domain2.com/Bing](http://www.domain2.com/Bing) I want it to redirect that request to another file in a different path, named new.png
For some odd reason I cannot make it rigt. could you plsease help me understand my mistake?

from fiddler:
```

GET http://www.domain1.com/images/old.png HTTP/1.1
Accept: */*
Referer: http://www.domain2.com/Bing
Accept-Language: en-us
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.2; WOW64; Trident/4.0; .NET CLR 2.0.50727; .NET CLR 3.0.4506.2152; .NET CLR 3.5.30729)
Accept-Encoding: gzip, deflate
If-Modified-Since: Wed, 27 Oct 2010 10:12:22 GMT
If-None-Match: "087e171bf75cb1:0"
Host: www.domain1.com
Connection: Keep-Alive

```
i guess the website address domain1 because it's hard-coded path (My guess).

The strange thing is that i fired-up the whole scenario by tuping the url [http://www.domain2.com/Bing](http://www.domain2.com/Bing) , but the host is written:[www.domain1.com](www.domain1.com)  so it's all blur for me.

My htaccess file which is attaced to [http://www.domain2.com/](http://www.domain2.com/)
via ISAPI (IIS)
```

RewriteEngine On
RewriteCompatibility2 On
RepeatLimit 32
RewriteBase

RewriteRule ^\/Bing$ http://www.domain2.com [NC,L,P]

RewriteCond %{HTTP_REFERER} ^http://www.domain2.com/Bing [or]
RewriteCond %{HTTP_REFERER} ^http://www.domain2.com/bing
RewriteRule ^(.*)\/ActivitiesService.asmx\/GetLatest$ http://www.domain2.com/ActivitiesService.asmx/GetL... [NC,L,P]
RewriteRule ^http://www.domain1.com/images/old.png$ http://www.domain2.com/images/new.png [NC,L]

The rest is less relevant

```

Thanks for any asistance

---

