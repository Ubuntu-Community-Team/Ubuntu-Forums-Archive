---
title: "install nginx with naxsi on ubuntu 18.x"
date: 2018-06-01
forum: Server Platforms
---

### Post by mydiscogr on 2018-06-01
I'm trying to install naxsi on ubuntu 18.x.
After googling and trying I found:


nginx-naxsi is no more available for ubuntu, so you have to compile by yourserlf.
Well to understand which module and setup I've installed 


    ```
apt install nginx-extras

```

then 
    ```
nginx -V

```

and I found this:


    ```
nginx version: nginx/1.14.0 (Ubuntu)
    built with OpenSSL 1.1.0g  2 Nov 2017
    TLS SNI support enabled
    configure arguments: 


    --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-mcUg8N/nginx-1.14.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' \
    --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' \
    --prefix=/usr/share/nginx \
    --conf-path=/etc/nginx/nginx.conf \
    --http-log-path=/var/log/nginx/access.log \
    --error-log-path=/var/log/nginx/error.log \
    --lock-path=/var/lock/nginx.lock \
    --pid-path=/run/nginx.pid \
    --modules-path=/usr/lib/nginx/modules \
    --http-client-body-temp-path=/var/lib/nginx/body \
    --http-fastcgi-temp-path=/var/lib/nginx/fastcgi \
    --http-proxy-temp-path=/var/lib/nginx/proxy \
    --http-scgi-temp-path=/var/lib/nginx/scgi \
    --http-uwsgi-temp-path=/var/lib/nginx/uwsgi \ 
    --with-debug \
    --with-pcre-jit \
    --with-http_ssl_module \
    --with-http_stub_status_module \
    --with-http_realip_module \
    --with-http_auth_request_module \
    --with-http_v2_module \
    --with-http_dav_module \
    --with-http_slice_module \ 
    --with-threads \
    --with-http_addition_module \
    --with-http_flv_module \
    --with-http_geoip_module=dynamic \
    --with-http_gunzip_module \
    --with-http_gzip_static_module \
    --with-http_image_filter_module=dynamic \
    --with-http_mp4_module \
    --with-http_perl_module=dynamic \
    --with-http_random_index_module \
    --with-http_secure_link_module \
    --with-http_sub_module \
    --with-http_xslt_module=dynamic \
    --with-mail=dynamic \
    --with-mail_ssl_module \
    --with-stream=dynamic \
    --with-stream_ssl_module \
    --with-stream_ssl_preread_module \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-headers-more-filter \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-auth-pam \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-cache-purge \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-dav-ext \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-ndk \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-echo \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-fancyindex \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/nchan \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-lua \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/rtmp \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-uploadprogress \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-upstream-fair \
    --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-subs-filter 

```    
so I assembled into this batch


    ```
#!/usr/bin/env bash
      
    apt-get install -y libpcre3 libpcre3-dev libssl-dev unzip make \
      libgoogle-perftools-dev google-perftools jq gcc
    mkdir /tmp/ngxbuild
    cd /tmp/ngxbuild
    latestNginx=$(curl -s http://hg.nginx.org/nginx/tags |
      grep "^ *release-" | head -1 | cut -c 9-)
    latestNaxsi=$(curl -s https://api.github.com/repos/nbs-system/naxsi/releases |
      jq -r .[].tag_name | grep -v rc | head -1)
    wget -q http://nginx.org/download/nginx-${latestNginx}.tar.gz
    wget -q https://github.com/nbs-system/naxsi/archive/${latestNaxsi}.tar.gz
    tar xzf nginx-${latestNginx}.tar.gz
    tar xzf ${latestNaxsi}.tar.gz
    cd nginx*


    
    ./configure --conf-path=/etc/nginx/nginx.conf \
        --add-module=../naxsi-${latestNaxsi}/naxsi_src/ \
    
        --with-cc-opt='-g -O2 -fdebug-prefix-map=/b
        (... see up for complete list of parameters)
        ...
        --add-dynamic-module=/build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-subs-filter 


    make -j 4
    make install
```    
    
but errors arise...


    ```
--with-debug : unknow command
    --with-pcre-jit : unknow command
    
    ...
    --with-http_ssl_module : unknow command    



```    and module like /build/nginx-mcUg8N/nginx-1.14.0/debian/modules/http-subs-filter is from library or I've to download
    
so I just want to install nginx - naxsi on ubuntu 18.x, any solution??

---

