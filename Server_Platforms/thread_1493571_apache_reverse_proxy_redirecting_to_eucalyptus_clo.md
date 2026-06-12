---
title: "apache reverse proxy redirecting to eucalyptus cloud settings confusion"
date: 2010-05-26
forum: Server Platforms
---

### Post by tapas_mishra on 2010-05-26
Hi,
 I am having a few websites running in a Reverse Proxy scenario on Ubuntu Server 10.04.
The configuration is like this 

```

                                |--------------192.168.1.1
                                |            (site1.abc.com)
                                |
                                |--------------192.168.1.2
                                |            (site2.abc.com)
                                |
                                |
                                |
                                |
                                |--------------192.168.1.3
                                |            (site3.abc.com)
                                | 
                                |
                                |
                                |
                                |--------------192.168.1.4
                                |            (site4.abc.com)
  (Public IP )                  |
            A-------------------|
(reverse proxy server)          |
  (192.168.1.25)                |
                                |--------------192.168.1.5
                                |            (site5.abc.com)
                                |


```

Except one all websites are running properly and being redirected to their respective domains.
Following is the configuration which I used
for each site define on server A a vhost file which contains following
```

#        ProxyPass / http://<Ip of Server>
#        ProxyPassReverse / http://<Ip of Server>

```
So if I have 5 websites then I have 5 vhost file on the gateway in above diagram A and in each of those file as above root of site is redirected to internal IP.
4 of them are running properly.
The fifth website is running on port 8080:/keyword
So in its vhost file on gateway I defined

```

#        ProxyPass / http://<Ip of Server>:8080/keyword
#        ProxyPassReverse / http://<Ip of Server>:8080/keyword

```
I can see on Lan http://<Ip of Server>:8080/keyword
but when from internet I try to see
[http://site5.abc.com](http://site5.abc.com)
I get redirected to a page is
[https://site5.abc.com:8443/](https://site5.abc.com:8443/) 
and it says ```

The webpage at https://site5.abc.com:8443/  might be temporarily down or it may have moved permanently to a new web address.

```
The site5.abc.com has a requirement to be run at port 8080 internally and it is not a Ubuntu server.(Red Hat based server)
While rest all are Ubuntu servers including gateway A.
So what can be error what more I need to do?

---

### Post by tapas_mishra on 2010-05-26
Sorry I forgot to enable site.
a2ensite every site is up and working.
Thanks all.

---

