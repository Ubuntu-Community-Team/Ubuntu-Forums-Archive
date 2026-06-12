---
title: "Nginx does not reveal real IP to Apache"
date: 2014-05-05
forum: Server Platforms
---

### Post by demontager on 2014-05-05
Ubuntu 14.04 server running on Nginx 1.4.6 as frontend and Apache 2.4 as backend. The problem in getting real ip in apache logs, there showing local ip 127.0.0.1 instead real. Also in phpinfo() _SERVER["REMOTE_ADDR"] value set to 127.0.0.1
nginx.conf
```


    server {
    listen        80 default;
    server_name    localhost;

    location / {
        proxy_pass        http://127.0.0.1:8080/;
        proxy_redirect    off;
        proxy_set_header    Host        $host;
        proxy_set_header    X-Real-IP    $remote_addr;
        proxy_set_header    X-Forwarded-For    $proxy_add_x_forwarded_for;
    }

    }
 

    include  sites-enabled/*.conf;
    
}

```

/etc/apache2/mods-enabled/rpaf.conf
```

<IfModule rpaf_module>

  RPAFenable On

    # When enabled, take the incoming X-Host header and
    # update the virtualhost settings accordingly:
    RPAFsethostname On

    # Define which IP's are your frontend proxies that sends
    # the correct X-Forwarded-For headers:
    RPAFproxy_ips 127.0.0.1 ::1

    # Change the header name to parse from the default
    # X-Forwarded-For to something of your choice:

    RPAFheader X-Forwarded-For
</IfModule>



```
Also tried to define 
RPAFheader X-Real-IP
RPAFheader Remote-Addr
 
not helped

---

