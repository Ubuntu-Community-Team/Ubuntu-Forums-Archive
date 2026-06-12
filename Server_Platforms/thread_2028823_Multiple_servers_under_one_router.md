---
title: "Multiple servers under one router"
date: 2012-07-18
forum: Server Platforms
---

### Post by Redsting on 2012-07-18
Hello,

I have been looking for a nice solution to this problem but haven't really found one yet.

Basically, I am hosting a website, and have two servers. The primary server is the public front, the secondary is a development server.
They are within the same LAN, and therefore share the same public IP from my modem.
The router is properly port forwarding all necessary ports to the primary router.

My goal is to use a subdomain to access the second server using the same ports.
For example :
```

    www.domain.com:80 --> 192.168.1.2:80
        domain.com:22 --> 192.168.1.2:22
    sub.domain.com:80 --> 192.168.1.3:80
    sub.domain.com:22 --> 192.168.1.3:22

```

The subdomain is registered with DreamHost.
> "sub" -- CNAME -- "domain.com"

I altered /etc/hosts to accept the subdomain, but this only works if I am within the server using SSH. I can't access the subdomain outside of that box.

Would setting up a DNS using bind9 in the primary server accomplish this?
I know using apache2 VirtualHost I can achieve this for :80 and :443 using ProxyPass, but this can't work for for SSH/FTP.

Any advice is welcome.

Thanks,
~Redsting

---

### Post by CharlesA on 2012-07-18
DNS doesn't deal with ports. You could just point all those domain names to the proper external IP and then use port forwarding to forward the proper ports to the proper IPs.

You can't have a different domain accessing different ports because you can only point one port to one IP.

---

### Post by sandyd on 2012-07-18
Since CharlesA has already explained, Ill tell you how you can do it

[LIST=1]
[*]Setup a Nginx proxy with virtualhosts
[*]Use the proxy to point towards the dev/stable server, depending on the virtualhost
[*]Set the subdomain to point at the nginx proxy.
[/LIST]
Something like
```
server {
 
        #replace <your_ip_here> with your ip address.
        listen   <your_ip_here>:80; ## listen for ipv4; this line is default and implied
        #listen   [::]:80 default ipv6only=on; ## listen for ipv6
 
        #location of your files
        index index.html index.htm;
        access_log off;
        error_log off;
 
        # The name of your domain (virtual hosts)
        server_name localhost;
        location / {
        proxy_pass http://<internal-server-ip>:80;
                 proxy_set_header   Host             $host;
                 proxy_set_header   X-Real-IP        $remote_addr;
                 proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
          
        }
}

```

---

### Post by spynappels on 2012-07-19
For ssh, you could map a high external port such as 2222 on your external IP to the default 22 on your dev server by port forwarding. You do not always have to forward an external port to the same port on a LAN host.

---

### Post by BkkBonanza on 2012-07-19
The proper name for what you need is "reverse proxy". Nginx is very good at that, as explained above, due to it's very low overhead. But also Nginx is an excellent web server in itself. So you could run Nginx on your public server and just add a subdomain that proxies to your dev server. Almost no extra config or extra server needed. Only drawback is that if the main public server needs to go down then it can't proxy for dev while it's down.

For ssh there isn't a reverse proxy way. Using different ports is simplest but you can also use the tunnelling built into ssh to connect to your dev machine via the main public one. It would be just one extra command to run.

---

