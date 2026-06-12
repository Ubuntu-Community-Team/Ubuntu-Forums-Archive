---
title: "How to browse VM"
date: 2009-12-01
forum: Virtualisation
---

### Post by satimis on 2009-12-01
Hi folks,


KVM - virtualization software
SugarCRM
host OS - Debian 5.0
VMs (guest) OS - Ubutun 9.04
Single(one) external IP


This is an experiment.

There are 4 VMs, each running SugarCRM which is a web-base CRM.  Each VM has its own host name and internal IP.  Desktops on local network(Intranet) can browse each VM on;```

local_ip/sugarcrm

```
without problem.

Now my further test is how can remote-desktops connect/browse the VMs?  Because there is only ONE external IP.  Suggestion and pointer would be appreciated.  TIA

B.R.
satimis

---

### Post by fouadatmeh on 2009-12-01
Hello,
By internal network, do you mean the network existing between the VMs or a LAN between the host and other PC's (same question goes for the external ip address)?

If you mean a LAN between PC's, then there must be a router/firewall that has the external address on it.. on which you can configure port forwarding.. Can you give more details on your LAN topology?

---

### Post by satimis on 2009-12-01
> **fouadatmeh said:**
> Hello,
By internal network, do you mean the network existing between the VMs or a LAN between the host and other PC's (same question goes for the external ip address)?

Hi fouadatmeh,

The networking conf is as follows;
vm1 ip=192.168.0.101
vm2 ip=192.168.0.102
vm3 ip=192.168.0.103
vm4 ip=192.168.0.104

host ip=192.168.0.100


Desktop on LAN;
browser```

192.168.0.101/sugarcrm
192.168.0.102/sugarcrm
etc.

```

can start Sugarcrm on vm1/vm2/etc.locally.


> 
If you mean a LAN between PC's, then there must be a router/firewall that has the external address on it.. on which you can configure port forwarding.. Can you give more details on your LAN topology?
Router connection:

ISP -> Modem -> Router -> PC


B.R.
satimis

---

### Post by fouadatmeh on 2009-12-01
Great,
You just have to configure port forwarding on your router; On the router, you will have to map a port on the external ip address to the port you use on the VM to access the CRM

Example:
- external ip address is 1.1.1.1 (url: [www.something.com](www.something.com))
- you access the VMs (192.168.0.101 & 102) via http (port 80)
- you want to use ports 2000 and 2001 on your external ip address

You will need to map port 2000 on 1.1.1.1 to forward to port 80 on 192.168.0.101 (and port 2001 to port 80 on 192.168.0.102)
**(for most SOHO routers, this can be simply configured via port forwarding on router's configuration webpage)
now to enter VM 1's webpage from the outside, you will need to type [http://1.1.1.1:2000](http://1.1.1.1:2000) (or [http://www.something.com:2000](http://www.something.com:2000))
and for V 2's page, "http://1.1.1.1:2001"

---

### Post by satimis on 2009-12-01
> **fouadatmeh said:**
> Great,
You just have to configure port forwarding on your router; On the router, you will have to map a port on the external ip address to the port you use on the VM to access the CRM

Example:
- external ip address is 1.1.1.1 (url: [www.something.com](www.something.com))
- you access the VMs (192.168.0.101 & 102) via http (port 80)
- you want to use ports 2000 and 2001 on your external ip address

You will need to map port 2000 on 1.1.1.1 to forward to port 80 on 192.168.0.101 (and port 2001 to port 80 on 192.168.0.102)
**(for most SOHO routers, this can be simply configured via port forwarding on router's configuration webpage)
now to enter VM 1's webpage from the outside, you will need to type [http://1.1.1.1:2000](http://1.1.1.1:2000) (or [http://www.something.com:2000](http://www.something.com:2000))
and for V 2's page, "http://1.1.1.1:2001"
Hi fouadatmeh,

Thanks for your advice.

The router is supplied by ISP.

On router
Forwarding Rules -> Virtual Server
No of "Service Ports" =	20

Most of them already used by
22, 25, 80, 110, 143, 443, 465, 8080, etc. forwarded to local IPs

There are sufficient spare "Service Ports" for 4 VMs.  However this arrangement will not be suitable serving >100 VMs


B.R.
satimis

---

### Post by fouadatmeh on 2009-12-01
Bummer :(

Maybe you can have a server that all VM traffic is forwarded to and then it diverts the traffic to the correct VM ? (if that is possible)
Or if you can replace the ISP router with a better one (cisco for example)?

Glad to have been of help :)

---

### Post by bodhi.zazen on 2009-12-01
Use a revers proxy.

Forward port 80 to the reverse proxy. The reverse proxy will then serve as many back end serves as you wish.

You can use pound or nginx. I recently switched to nginx ;)

[http://intranation.com/entries/2008/09/using-nginx-reverse-proxy/](http://intranation.com/entries/2008/09/using-nginx-reverse-proxy/)

[https://help.ubuntu.com/community/Nginx/ReverseProxy](https://help.ubuntu.com/community/Nginx/ReverseProxy)

---

### Post by satimis on 2009-12-02
> **bodhi.zazen said:**
> Use a revers proxy.

Forward port 80 to the reverse proxy. The reverse proxy will then serve as many back end serves as you wish.

You can use pound or nginx. I recently switched to nginx ;)

[http://intranation.com/entries/2008/09/using-nginx-reverse-proxy/](http://intranation.com/entries/2008/09/using-nginx-reverse-proxy/)

[https://help.ubuntu.com/community/Nginx/ReverseProxy](https://help.ubuntu.com/community/Nginx/ReverseProxy)

Hi bodhi.zazen,

Thanks for your advice and URL

I suppose nginx should run on host of the virtual machine.  However the host is only a basic desktop without Apache2.  Or running nginx on a VM for this purpose?  In the later case shall I make a VM as reverse proxy server.  Then port 80 should be forwarded to this server NOT to the host as it is now.

If I'm wrong please correct me.  TIA

B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-02
nginx is quite secure (designed to be) and runs on less then 10 Mb RAM. Personally I run it in a VPS using minimal RAM.

Forward port 80 to the machine running nginx.

---

### Post by satimis on 2009-12-02
> **bodhi.zazen said:**
> nginx is quite secure (designed to be) and runs on less then 10 Mb RAM. Personally I run it in a VPS using minimal RAM.

Forward port 80 to the machine running nginx.
Hi bodhi.zazen,

I don't have web server running as VM on this virtual machines.  All VMs are either running SugarCRM or PSPP/SPSS/R-Project (Statistical computing).  I have to create a basic/simple web server as VM for running nginx.

What packages will need to install on this VM?  Apache2 and PHP5 only?  Do I need MySQL and Iptables?

TIA

B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-02
For the machine running nginx all you need is nginx

---

### Post by satimis on 2009-12-05
Hi bodhi.zazen,


KVM
host - Debian 5.0
VM - Ubuntu 9.04


I was following;
Using Nginx as reverse proxy
[http://intranation.com/entries/2008/09/using-nginx-reverse-proxy/](http://intranation.com/entries/2008/09/using-nginx-reverse-proxy/)

to install Nginx, nginx-0.7.64


First I cloned a new VM on an existing VM with Ubuntu9.04 running which was previously net-installed on mini.iso, including Apache2.  


I was stucked on "Swap Apache and Nginx"

# sudo apache2ctl stop
No complaint

# /usr/local/sbin/nginx 
No complaint.  Did nginx start?

I didn't see the “Welcome to Nginx!” message. Great!"

# cat /etc/apache2/ports.conf ```

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```

# nano /etc/apache2/ports.conf 
changing it as ```

NameVirtualHost *:8080
Listen 8080

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```

# apache2ctl start```

[Sat Dec 05 16:35:11 2009] [warn] NameVirtualHost *:8080 has no VirtualHosts

```

# apache2ctl stop```

[Sat Dec 05 16:37:13 2009] [warn] NameVirtualHost *:8080 has no VirtualHosts

```


Then I reverted ports.conf to its original settings

# apache2ctl start```

(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

Whether I need to change```

Listen 443

```

to;```

Listen 8080
?

```

Here I have some confusion.

$ uname -a```

Linux vm21 2.6.28-16-generic #57-Ubuntu SMP Wed Nov 11 09:47:24 UTC 2009 i686 GNU/Linux

```

I couldn't find Ubuntu version.  Instead I found;

$ cat /etc/debian_version ```

5.0

```

Please help.  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-05
You do not need to do that, switching the port for apache is only required if you are using apache and nginx on the same machine.

Lets assume you are running nginx on 192.168.0.10 and apache on 192.168.0.11 and 192.168.0.12

(nginx reverse proxy 2 web servers).

Forward port 80 from your router to 192.168.1.10 (nginx)

and proxy 192.168.0.11 and 192.168.0.12 

everything runs on port 80, nginx, and both apache instances.

---

### Post by satimis on 2009-12-05
> **bodhi.zazen said:**
> You do not need to do that, switching the port for apache is only required if you are using apache and nginx on the same machine.

Lets assume you are running nginx on 192.168.0.10 and apache on 192.168.0.11 and 192.168.0.12

(nginx reverse proxy 2 web servers).

Forward port 80 from your router to 192.168.1.10 (nginx)

and proxy 192.168.0.11 and 192.168.0.12 

everything runs on port 80, nginx, and both apache instances.

Hi bodhi.zazen,

I don't need running Apache2 on this VM which is created solely for running nginx.  It just happens the VM being cloned having Apache2 there.

Whether moving on to;

Configure Nginx ?

Forward port 80 on the router to this VM?  Its IP address is 196.168.0.27

Then which file shall I config to redirect all incoming requests from the remote desktops to their own VMs?  TIA

B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-05
I would completely remove apache from the nginx machine.

To proxy see this :

[https://help.ubuntu.com/community/Nginx/ReverseProxy](https://help.ubuntu.com/community/Nginx/ReverseProxy)

---

### Post by satimis on 2009-12-05
> **bodhi.zazen said:**
> I would completely remove apache from the nginx machine.

To proxy see this :

[https://help.ubuntu.com/community/Nginx/ReverseProxy](https://help.ubuntu.com/community/Nginx/ReverseProxy)

Hi bodhi.zazen


I'll perform following steps;

sudo apt-get remove apache2

sudo mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.orginal

copy follows on a text file and save it as /etc/nginix/nginx.conf```

# smart default nginx (Ubuntu 7.10)

user                www-data www-data;
worker_processes    2;

error_log           /var/log/nginx/error.log warn;
pid                 /var/run/nginx.pid;

events {
    worker_connections  1024;
    use epoll;
}

http {
    # allow long server names
    server_names_hash_bucket_size 64;
    
    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    log_format main '$remote_addr - $remote_user [$time_local] '
                    '"$request" $status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';

    access_log          /var/log/nginx/access.log;
    
    # spool uploads to disk instead of clobbering downstream servers
    client_body_temp_path /var/spool/nginx-client-body 1 2;
    client_max_body_size 32m;
    client_body_buffer_size    128k;
    
    server_tokens       off;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         off;

    keepalive_timeout   5;
    
    ## Compression
    gzip on;
    gzip_http_version 1.0;
    gzip_comp_level 2;
    gzip_proxied any;
    gzip_min_length  1100;
    gzip_buffers 16 8k;
    gzip_types text/plain text/html text/css application/x-javascript \
        text/xml application/xml application/xml+rss text/javascript \
        image/gif image/jpeg image/png;
    # Some version of IE 6 don't handle compression well on some mime-types, 
    # so just disable for them
    gzip_disable "MSIE [1-6].(?!.*SV1)";
    # Set a vary header so downstream proxies don't send cached gzipped 
    # content to IE6
    gzip_vary on;
    
    # proxy settings
    proxy_redirect     off;

    proxy_set_header   Host             $host;
    proxy_set_header   X-Real-IP        $remote_addr;
    proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    proxy_max_temp_file_size 0;

    proxy_connect_timeout      90;
    proxy_send_timeout         90;
    proxy_read_timeout         90;

    proxy_buffer_size          4k;
    proxy_buffers              4 32k;
    proxy_busy_buffers_size    64k;
    proxy_temp_file_write_size 64k;

    include             /etc/nginx/sites-enabled/*;

}

```


To test that this configuration works.  Add a simple localhost configuration file:

sudo mkdir /etc/nginx/sites-enabled

copy follows on a text file and save it as /etc/nginx/sites-enabled/localhost.conf

```

server {
    listen       80;
    server_name  localhost;

    location / {
        root   html;
        index  index.html index.htm;
    }
}

```


copy follows on a text file and save it as /etc/nginx/proxy.conf
```

proxy_redirect          off;
proxy_set_header        Host            $host;
proxy_set_header        X-Real-IP       $remote_addr;
proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
client_max_body_size    10m;
client_body_buffer_size 128k;
proxy_connect_timeout   90;
proxy_send_timeout      90;
proxy_read_timeout      90;
proxy_buffers           32 4k;

```


The server names on this test are;```

vm22	192.168.0.22
vm23	192.168.0.23
vm28	192.168.0.28
vm29	192.168.0.29
etc.

```


copy follows on a text file and save it as /etc/nginx/sites-available/proxy_pass
```

server {
        listen   80;
        server_name  vm22 vm23 vm28 vm29;

        access_log  /var/log/nginx/access.log;


        location / {
                proxy_pass      http://172.27.0.2/;
                include         /etc/nginx/proxy.conf;
        }
}

```


Here I'm not very clear "proxy_pass      http://172.27.0.2/"


The IP of the vm21 running ngnix is "192.168.0.21". Whether replace "http://172.27.0.2/" with "ttp://192.168.0.21"?

TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-06
You are getting closer, but ...

Lets start with the basics, you have a public IP address, you need first to point your DNS to the public IP address. The DNS needs to be a FQDN , such as server1.com or foo.net 

You then forward port 80 to your nginx VM (nginx is acting as a reverse proxy).

Your nginx file looks fine, well except where you define your server name as "localhost" , but I do not think that really matters.

Now each server you are going to proxy has a unique config file defined in /etc/nginx/sites-available, foo.net for example.

In /etc/mginx/sites-available/foo.net you put :

```

server {
        listen   80;
        server_name  foo.net www.foo.net;

        access_log  /var/log/nginx/foo/access.log;

        location / {
                proxy_pass      http://192.168.0.22/;
                include         /etc/nginx/proxy.conf;
        }
}
```Here I uses one of your servers as an example.

Now you can type "foo.net" in a browser, DNS sends the request to your public IP, your router forwards port 80 to nginx, nginx forwards to 192.168.0.22 , 

192.168.0.22 is running apache and serves the content of foo.net

---

### Post by satimis on 2009-12-06
> **bodhi.zazen said:**
> ..
Lets start with the basics, you have a public IP address, you need first to point your DNS to the public IP address. The DNS needs to be a FQDN , such as server1.com or foo.net 


Sorry, here I'm not very clear.

Whether you meant at the site of the Domain Name Register?  On the said Register's website, the Domain Name is pointing at the public IP address.  All request to the Domain Name will be forwarded to the public IP.

On Register's website```

A (Host)
Host	Points To
@	public IP

```


> 
You then forward port 80 to your nginx VM (nginx is acting as a reverse proxy).


Yes, on router I'll forward the port 80 to 192.168.0.21 (nginx VM IP address)

nginx VM=vm21


> 
Your nginx file looks fine, well except where you define your server name as "localhost" , but I do not think that really matters.


On vm21 (nginx VM)

cat /etc/hostname ```

127.0.0.1       localhost
127.0.1.1       vm21.satimis.com        vm21
.....

```

Shall I replace "localhost" with "vm21.satimis.com" or just "vm21"?

> 
Now each server you are going to proxy has a unique config file defined in /etc/nginx/sites-available, foo.net for example.

In /etc/mginx/sites-available/foo.net you put :
....

I'll take vm22 as example;

cat /etc/hostname ```

127.0.0.1       localhost
127.0.1.1       vm22.satimis.com        vm22
.....

```

Copy follows on a text file and save it as /etc/mginx/sites-available/vm22.satimis.com```

server {
        listen   80;
        server_name  vm22.satimis.com www.vm22.satimis.com;

        access_log  /var/log/nginx/foo/access.log;

        location / {
                proxy_pass      http://192.168.0.22/;
                include         /etc/nginx/proxy.conf;
        }
}

```


Or can I use the short servername "vm22" instead?

Copy follows on a text file and save it as /etc/mginx/sites-available/vm22```

server {
        listen   80;
        server_name  vm22 www.vm22.satimis.com;

        access_log  /var/log/nginx/foo/access.log;

        location / {
                proxy_pass      http://192.168.0.22/;
                include         /etc/nginx/proxy.conf;
        }
}

```

> 
Now you can type "foo.net" in a browser, DNS sends the request to your public IP, your router forwards port 80 to nginx, nginx forwards to 192.168.0.22 , 

192.168.0.22 is running apache and serves the content of foo.net

On the host's browser?  Then what shall I type on remote browser?

```

public_IP/192.168.0.22

```
?

TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-06
Lets walk through this with a single VPS, say VM22.

First, nginx is serving as a proxy ? or are you serving content from nginx ? I assume it is a proxy only.

You can point "satimis.com" at the nginx server and serve some static content such as a front page.

Now, vm22.satimis.com

First on your DNS, point vm22.satimis.com to your public IP, usually by adding vm22 as an A name. If you do not know how to do this, speak to your DNS provider, they all offer assistance.

Now in nginx :

make a file : /etc/mginx/sites-available/vm22.satimis.com

Put the relevant info in it :

```
server {
        listen   80;
        server_name vm22.satimis.com [www.vm22.satimis.com;]("http://www.vm22.satimis.com;")

        access_log  /var/log/nginx/vm22.satimis.com/access.log;

        location / {
                proxy_pass      [http://192.168.0.22/;](http://192.168.0.22/;)
                include         /etc/nginx/proxy.conf;
        }
}
```

Now, link it to sites availavle

sudo ln -s /etc/nginx/sites-available/vm22.satimis.com /etc/nginx/sites-available/vm22.satimis.com

Make a log file 

sudo mkdir /var/log/nginx/vm22.satimis.com
sudo touch /var/log/nginx/vm22.satimis.com/access.log

Restart nginx

sudo service nginx restart

Now in any browser, put 

vm22.satimis.com in the address bar, same place you would put ubuntuforums.org, and you should get the content .

Half the issue is I do not get the impression you know how to configure a public web server, review that first (ie domain names, DNS, FQDN).

Next be sure you understand forwarding port 80 from your router to nginx.

Last, the configuration of nginx is simple, it is a short file where you define the server name, using the FQDN, ie "server_name FQDN"

Make a log file

and forward the request to your private IP

proxy_pass private_ip

---

### Post by satimis on 2009-12-07
> **bodhi.zazen said:**
> You are getting closer, but ...

Lets start with the basics, you have a public IP address, you need first to point your DNS to the public IP address. The DNS needs to be a FQDN , such as server1.com or foo.net 

You then forward port 80 to your nginx VM (nginx is acting as a reverse proxy).

Your nginx file looks fine, well except where you define your server name as "localhost" , but I do not think that really matters.

Now each server you are going to proxy has a unique config file defined in /etc/nginx/sites-available, foo.net for example.

In /etc/mginx/sites-available/foo.net you put :

```

server {
        listen   80;
        server_name  foo.net www.foo.net;

        access_log  /var/log/nginx/foo/access.log;

        location / {
                proxy_pass      http://192.168.0.22/;
                include         /etc/nginx/proxy.conf;
        }
}
```Here I uses one of your servers as an example.

Now you can type "foo.net" in a browser, DNS sends the request to your public IP, your router forwards port 80 to nginx, nginx forwards to 192.168.0.22 , 

192.168.0.22 is running apache and serves the content of foo.net

Hi bodhi.zazen,

Redo following steps.  But it still fails unable to browse VMs;
vm22  192.168.0.22
vm23  192.168.0.23


On router```

Service Port	Server IP
80		192.168.0.21

```

forward port 80 to nginx VM


On Domain Name provider's website

made following changes;
```

A Host				Points To/Goes To		TTL
[] @				111.222.333.444			1 Hour
[] vm21				111.222.333.444			1 Hour

CNAMES (Aliases)
www				@				1 Hour

MX (Mail Exchange)
Priority	Host		Goes To	
[]		@		vm21.satimis.com		1 Hour

```

1)
Remark: I don't think it is necessary making change on "Priority"?  If NO, I'll change it back to its original setting.

2)
nginx VM = vm21
Also tried "A Host"=vm21.satimis.com (fqdn)


satimis@vm21:~$ sudo apt-get remove apache2


satimis@vm21:~$ sudo mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.original

satimis@vm21:~$ sudo nano /etc/nginx/nginx.conf

copied follows on it and saved it```

# smart default nginx (Ubuntu 7.10)

user                www-data www-data;
worker_processes    2;

error_log           /var/log/nginx/error.log warn;
pid                 /var/run/nginx.pid;

events {
    worker_connections  1024;
    use epoll;
}

http {
    # allow long server names
    server_names_hash_bucket_size 64;
    
    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    log_format main '$remote_addr - $remote_user [$time_local] '
                    '"$request" $status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';

    access_log          /var/log/nginx/access.log;
    
    # spool uploads to disk instead of clobbering downstream servers
    client_body_temp_path /var/spool/nginx-client-body 1 2;
    client_max_body_size 32m;
    client_body_buffer_size    128k;
    
    server_tokens       off;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         off;

    keepalive_timeout   5;
    
    ## Compression
    gzip on;
    gzip_http_version 1.0;
    gzip_comp_level 2;
    gzip_proxied any;
    gzip_min_length  1100;
    gzip_buffers 16 8k;
    gzip_types text/plain text/html text/css application/x-javascript \
        text/xml application/xml application/xml+rss text/javascript \
        image/gif image/jpeg image/png;
    # Some version of IE 6 don't handle compression well on some mime-types, 
    # so just disable for them
    gzip_disable "MSIE [1-6].(?!.*SV1)";
    # Set a vary header so downstream proxies don't send cached gzipped 
    # content to IE6
    gzip_vary on;
    
    # proxy settings
    proxy_redirect     off;

    proxy_set_header   Host             $host;
    proxy_set_header   X-Real-IP        $remote_addr;
    proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    proxy_max_temp_file_size 0;

    proxy_connect_timeout      90;
    proxy_send_timeout         90;
    proxy_read_timeout         90;

    proxy_buffer_size          4k;
    proxy_buffers              4 32k;
    proxy_busy_buffers_size    64k;
    proxy_temp_file_write_size 64k;

    include             /etc/nginx/sites-enabled/*;

}

```


Add a simple localhost configuration file:

satimis@vm21:~$ sudo mkdir /etc/nginx/sites-enabled
satimis@vm21:~$ sudo nano /etc/nginx/sites-enabled/localhost.conf

copied follows on it and saved it.

```

server {
    listen       80;
    server_name  localhost;

    location / {
        root   html;
        index  index.html index.htm;
    }
}

```


satimis@vm21:~$ sudo nano /etc/nginx/proxy.conf

coped follows on it and saved it.
```

proxy_redirect          off;
proxy_set_header        Host            $host;
proxy_set_header        X-Real-IP       $remote_addr;
proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
client_max_body_size    10m;
client_body_buffer_size 128k;
proxy_connect_timeout   90;
proxy_send_timeout      90;
proxy_read_timeout      90;
proxy_buffers           32 4k;

```


Full Qualified Domain Name (FQDN);```

vm21	nginx VM	vm21.satimis.com
vm22	SugarCRM	vm22.satimis.com
vm23	SugarCRM	vm23.satimis.com
etc.

```


satimis@vm21:~$ sudo mkdir /etc/nginx/sites-available

satimis@vm21:~$ sudo nano /etc/nginx/sites-available/vm22.satimis.com

copied follows on it and save it.
```

server {
        listen   80;
        server_name  vm22.satimis.com www.vm22.satimis.com;

        access_log  /var/log/nginx/access.log;


        location / {
                proxy_pass      http://192.168.0.22/;
                include         /etc/nginx/proxy.conf;
        }
}

```


satimis@vm21:~$ sudo nano /etc/nginx/sites-available/vm23.satimis.com

copied follows on it and save it.
```

server {
        listen   80;
        server_name  vm23.satimis.com www.vm23.satimis.com;

        access_log  /var/log/nginx/access.log;


        location / {
                proxy_pass      http://192.168.0.23/;
                include         /etc/nginx/proxy.conf;
        }
}

```

etc.

> 
sudo ln -s /etc/nginx/sites-available/vm22.satimis.com /etc/nginx/sites-available/vm22.satimis.com


I suppose it should be;

satimis@vm21:~$ sudo ln -s /etc/nginx/sites-available/vm22.satimis.com /etc/nginx/sites-enabled/vm22.satimis.com

satimis@vm21:~$ sudo ln -s /etc/nginx/sites-available/vm23.satimis.com /etc/nginx/sites-enabled/vm23.satimis.com


Create log files;

satimis@vm21:~$ sudo mkdir /var/log/nginx/vm21.satimis.com
satimis@vm21:~$ sudo touch /var/log/nginx/vm21.satimis.com/access.log

Do I need to create a log file for vm21 (nginx VM) ?

satimis@vm21:~$ sudo mkdir /var/log/nginx/vm22.satimis.com
satimis@vm21:~$ sudo touch /var/log/nginx/vm22.satimis.com/access.log

satimis@vm21:~$ sudo mkdir /var/log/nginx/vm23.satimis.com
satimis@vm21:~$ sudo touch /var/log/nginx/vm23.satimis.com/access.log


Reboot nginx VM

On nginx VM
satimis@vm21:~$ sudo service nginx restart```

$nginx: unrecognized service

```

On host
satimis@vm0:~$ sudo service nginx restart```

[sudo] password for satimis: 
sudo: service: command not found

```

Again on nginx VM

satimis@vm21:~$ sudo shutdown -r now```

[sudo] password for satimis: 

Broadcast message from satimis@vm21
	(/dev/pts/0) at 15:23 ...

The system is going down for reboot NOW!

```


On nginx VM

root@vm21:/home/satimis# /usr/local/sbin/nginx```

[warn]: duplicate MIME type "text/html" in /etc/nginx/nginx.conf:49
[warn]: duplicate MIME type "\
" in /etc/nginx/nginx.conf:49
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: still could not bind()

```


On host browser:- fails, unable to browse VMs
All log files are empty.


Please help.  TIA


Edit:

root@vm21:/home/satimis# cat /var/log/nginx/error.log ```

2009/12/07 12:53:40 [warn] 2760#0: duplicate MIME type "text/html" in /etc/nginx/nginx.conf:49
2009/12/07 12:53:40 [warn] 2760#0: duplicate MIME type "\
" in /etc/nginx/nginx.conf:49
2009/12/07 12:53:40 [emerg] 2760#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 12:53:40 [emerg] 2760#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 12:53:40 [emerg] 2760#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 12:53:40 [emerg] 2760#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 12:53:40 [emerg] 2760#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 12:53:40 [emerg] 2760#0: still could not bind()
2009/12/07 16:13:26 [warn] 2830#0: duplicate MIME type "text/html" in /etc/nginx/nginx.conf:49
2009/12/07 16:13:26 [warn] 2830#0: duplicate MIME type "\
" in /etc/nginx/nginx.conf:49
2009/12/07 16:13:26 [emerg] 2830#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 16:13:26 [emerg] 2830#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 16:13:26 [emerg] 2830#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 16:13:26 [emerg] 2830#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 16:13:26 [emerg] 2830#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2009/12/07 16:13:26 [emerg] 2830#0: still could not bind()

```


line 49```

        image/gif image/jpeg image/png;

```

```

 gzip_types text/plain text/html text/css application/x-javascript \
        text/xml application/xml application/xml+rss text/javascript \
        image/gif image/jpeg image/png; (line 49)

```



B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-07
your config files look "OK" , with the exception of your logs.

Personally I log each proxy separate so as not to use one big log. In your sites you are using 

"access_log  /var/log/nginx/access.log;"

But I would advise you use

"access_log  /var/log/nginx/**vm22.satimis.com**/access.log;"

Your DNS is not working , when I put your domain name into my browser I get :

> While trying to retrieve the URL: [http://vm22.satimis.com/](http://vm22.satimis.com/) 
 The following error was encountered: 

[LIST]
[*] ** Could not resolve Hostname "vm22.satimis.com"**
[/LIST]


your main site, satimis.com, times out, so you need to fix your DNS.

In terms of your error messages when starting nginx, sounds as if either nginx is already running or something is using port 80 already.

what is the output of {code]sudo netstat -ntulp[/code] ?

---

### Post by satimis on 2009-12-07
> **bodhi.zazen said:**
> your config files look "OK" , with the exception of your logs.

Personally I log each proxy separate so as not to use one big log. In your sites you are using 

"access_log  /var/log/nginx/access.log;"

But I would advise you use

"access_log  /var/log/nginx/**vm22.satimis.com**/access.log;"

Your DNS is not working , when I put your domain name into my browser I get :



your main site, satimis.com, times out, so you need to fix your DNS.

In terms of your error messages when starting nginx, sounds as if either nginx is already running or something is using port 80 already.

what is the output of {code]sudo netstat -ntulp[/code] ?

Hi bodhi.zazen,


First I must make sure whether nginx is working.


Made following changes;

satimis@vm21:~$ sudo nano /etc/nginx/sites-available/vm22.satimis.com

```

        access_log  /var/log/nginx/vm22.satimis.com/access.log;

```


satimis@vm21:~$ sudo nano /etc/nginx/sites-available/vm23.satimis.com
```

        access_log  /var/log/nginx/vm23.satimis.com/access.log;

```


satimis@vm21:~$ sudo invoke-rc.d nginx reload```

invoke-rc.d: unknown initscript, /etc/init.d/nginx not found.

```

It didn't work.  I don't know how to restart nginx.  I have to reboot nginx VM (vm21)


satimis@vm21:~$ sudo shutdown -r now

ssh-relogin vm21
satimis@vm0:~$ ssh 192.168.0.21

satimis@vm21:~$ sudo /usr/local/sbin/nginx ```

[warn]: duplicate MIME type "text/html" in /etc/nginx/nginx.conf:49
[warn]: duplicate MIME type "\
" in /etc/nginx/nginx.conf:49
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)
[emerg]: still could not bind()

```

I have no idea whether nginx is running.

On host browser;

[http://192.168.0.21](http://192.168.0.21)```

It Works

```

It seems Apache is running Not the welcome display of nginx


On ngnix VM (vm21)

satimis@vm21:~$ apt-cache policy apache2```

apache2:
  Installed: (none)
  Candidate: 2.2.11-2ubuntu2.5
  Version table:
     2.2.11-2ubuntu2.5 0
        500 http://hk.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
     2.2.11-2ubuntu2 0
        500 http://hk.archive.ubuntu.com jaunty/main Packages

```

Apache2 already removed.


satimis@vm21:~$ sudo netstat -ntulp```

[sudo] password for satimis: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      2336/dovecot    
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      2336/dovecot    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      2272/mysqld     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      2336/dovecot    
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      2336/dovecot    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2644/apache2    
tcp        0      0 192.168.0.21:53         0.0.0.0:*               LISTEN      2160/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      2160/named      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2182/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2547/cupsd      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      2160/named      
tcp6       0      0 :::53                   :::*                    LISTEN      2160/named      
tcp6       0      0 :::22                   :::*                    LISTEN      2182/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      2547/cupsd      
tcp6       0      0 ::1:953                 :::*                    LISTEN      2160/named      
udp        0      0 0.0.0.0:57347           0.0.0.0:*                           2516/avahi-daemon: 
udp        0      0 192.168.0.21:53         0.0.0.0:*                           2160/named      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           2160/named      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           2516/avahi-daemon: 
udp6       0      0 :::53                   :::*                                2160/named      

```

Apache2 is still there?

Please advise how to fix the problem removing all relevant packages of Apache2 .  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-07
For Ubuntu 9.04 you would start / stop services with :

sudo /etc/init.d/service start|stop|restart|reload

```
sudo /etc/init.d/apache2 start
/etc/init.d/apache2 stop
/etc/init.d/nginx start
```Looking at the output of you netstat, apache is indeed running and that is why you can not stop nginx.

> tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2644/apache2    Remove apache with the purge option (install then purge):

```
sudo apt-get purge apache2
sudo apt-get autoremove
```

---

### Post by satimis on 2009-12-07
> **bodhi.zazen said:**
> For Ubuntu 9.04 you would start / stop services with :

sudo /etc/init.d/service start|stop|restart|reload

```
sudo /etc/init.d/apache2 start
/etc/init.d/apache2 stop
/etc/init.d/nginx start
```Looking at the output of you netstat, apache is indeed running and that is why you can not stop nginx.

Remove apache with the purge option (install then purge):

```
sudo apt-get purge apache2
sudo apt-get autoremove
```

Hi bodhi.zazen,

satimis@vm21:~$ sudo apt-get install apache2

satimis@vm21:~$ sudo apt-get purge apache2

satimis@vm21:~$ sudo apt-get autoremove```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

On host browser
[http://192.168.0.21/](http://192.168.0.21/)```

It works!

```

Apache2 seems still running


On nginx VM (vm21)
satimis@vm21:~$ sudo shutdown -r now

to reboot vm21

ssh-relogin nginx VM (vm21)

satimis@vm21:~$ sudo netstat -ntulp```

[sudo] password for satimis: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      2291/dovecot    
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      2291/dovecot    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      2223/mysqld     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      2291/dovecot    
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      2291/dovecot    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2592/apache2    
tcp        0      0 192.168.0.21:53         0.0.0.0:*               LISTEN      2111/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      2111/named      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2133/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2497/cupsd      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      2111/named      
tcp6       0      0 :::53                   :::*                    LISTEN      2111/named      
tcp6       0      0 :::22                   :::*                    LISTEN      2133/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      2497/cupsd      
tcp6       0      0 ::1:953                 :::*                    LISTEN      2111/named      
udp        0      0 192.168.0.21:53         0.0.0.0:*                           2111/named      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           2111/named      
udp        0      0 0.0.0.0:36574           0.0.0.0:*                           2472/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           2472/avahi-daemon: 
udp6       0      0 :::53                   :::*                                2111/named      

```


On host browser
[http://192.168.0.21/](http://192.168.0.21/)```

It works!

```

Very funny.  Apache2 is still there.

On nginx VM

satimis@vm21:~$ sudo /etc/init.d/apache2 status```

 * Apache is running (pid 2592).

```

Apache2 is still running

satimis@vm21:~$ sudo /etc/init.d/nginx start```

sudo: /etc/init.d/nginx: command not found

```


satimis@vm21:~$ which nginx```

/usr/local/sbin/nginx

```

I'm at loss


B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-08
stop apache

```
sudo /etc/init.d/apache2 stop
```

remove apache (apache is a metapackage, so we need to find all the packages you have installed}

```
sudo apt-get purge apache2.2-bin
```

You can find any additional packages left behind with :

```
sudo apt-get autoremove
dpkg -l | grep apache
```

Remove those as well ;)

---

### Post by satimis on 2009-12-08
> **bodhi.zazen said:**
> stop apache

```
sudo /etc/init.d/apache2 stop
```

remove apache (apache is a metapackage, so we need to find all the packages you have installed}

```
sudo apt-get purge apache2.2-bin
```

You can find any additional packages left behind with :

```
sudo apt-get autoremove
dpkg -l | grep apache
```

Remove those as well ;)


satimis@vm21:~$ sudo /etc/init.d/apache2 stop```

 * Stopping web server apache2                                                           ... waiting                                                                     [ OK ]
```


satimis@vm21:~$ sudo apt-get purge apache2.2-bin```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2.2-bin

```

satimis@vm21:~$ sudo apt-get autoremove```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

satimis@vm21:~$ dpkg -l | grep apache```

ii  apache2-mpm-prefork                        2.2.11-2ubuntu2.5                 Apache HTTP Server - traditional non-threade
ii  apache2-utils                              2.2.11-2ubuntu2.5                 utility programs for webservers
ii  apache2.2-common                           2.2.11-2ubuntu2.5                 Apache HTTP Server common files
ii  libapache2-mod-php5                        5.2.6.dfsg.1-3ubuntu4.4           server-side, HTML-embedded scripting languag

```


satimis@vm21:~$ sudo apt-get purge apache2-mpm-prefork```

...
Removing apache2-mpm-prefork ...
 * Stopping web server apache2  

```

satimis@vm21:~$ sudo apt-get purge apache2-utils```

....
Removing apache2-utils ...
Processing triggers for man-db ...
Processing triggers for ufw ...

```

satimis@vm21:~$ sudo apt-get purge apache2.2-common```

....
Package apache2.2-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

satimis@vm21:~$ sudo apt-get purge libapache2-mod-php5```

.....
Package libapache2-mod-php5 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


Again;

satimis@vm21:~$ sudo apt-get autoremove```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

satimis@vm21:~$ dpkg -l | grep apache
No printout

satimis@vm21:~$ sudo shutdown -r now


ssh Relogin nginx VM (vm21)

satimis@vm21:~$ sudo netstat -ntulp```

[sudo] password for satimis: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      2285/dovecot    
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      2285/dovecot    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      2221/mysqld     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      2285/dovecot    
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      2285/dovecot    
tcp        0      0 192.168.0.21:53         0.0.0.0:*               LISTEN      2109/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      2109/named      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2131/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2496/cupsd      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      2109/named      
tcp6       0      0 :::53                   :::*                    LISTEN      2109/named      
tcp6       0      0 :::22                   :::*                    LISTEN      2131/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      2496/cupsd      
tcp6       0      0 ::1:953                 :::*                    LISTEN      2109/named      
udp        0      0 192.168.0.21:53         0.0.0.0:*                           2109/named      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           2109/named      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           2465/avahi-daemon: 
udp        0      0 0.0.0.0:55421           0.0.0.0:*                           2465/avahi-daemon: 
udp6       0      0 :::53                   :::*                                2109/named  
```    


Port 80 is not used.

nginx is not running.  On host browser;

[http://192.168.0.21/](http://192.168.0.21/)
blank page


satimis@vm21:~$ sudo /usr/local/sbin/nginx ```

[warn]: duplicate MIME type "text/html" in /etc/nginx/nginx.conf:49
[warn]: duplicate MIME type "\
" in /etc/nginx/nginx.conf:49

```

Again on host browser;

[http://192.168.0.21/](http://192.168.0.21/)```

Welcome to nginx!

```

nginx is now running


On host browser

[http://vm22.satimis.com/](http://vm22.satimis.com/)
Still blank page


On "Total DNS Control" of Domain Name register's website;

vm21 points at external IP.  On router port 80 is forwarded to nginx VM(vm21).


Performed following test;

On the "Total DNS Control" of Domain Name register's website

vm22 points at external IP.  On router port 80 is forwarded to vm22


On host browser;
satimis.com/sugarcrm

starts the login page of Sugarcrm which is running on vm22.


On host browser
vm22.satimis.com

doesn't work


I think vm22.satimis.com is the subdomain of satimis.com.  I'm now asking the Domain Name Register its setup allowing the subdomain pointing at the external IP.  However I fail to see my request will be entertained without registering the subdomain.


B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-08
In you DNS, use vm22 as an A name ;)

EDIT: Your DNS is now working as I can ping vm22.satimis.com ;)

One step closer.

---

### Post by satimis on 2009-12-09
> **bodhi.zazen said:**
> In you DNS, use vm22 as an A name ;)

EDIT: Your DNS is now working as I can ping vm22.satimis.com ;)

One step closer.
Hi bodhi.zazen,


Some funny thing happens here.

On "Total DNS Control" of Domain Name register's website;

```

A (Host)
Host	Points To
@	public IP
vm22	public IP
vm23	public IP

```


Performed following tests;


1)
Router - Port 80 forward to 192.168.0.22

nginx VM (vm21 - router IP=192.168.0.21) - running
SugarCRM VM (vm22 - router IP=192.168.0.22) - running
SugarCRM VM (vm23 - router IP=192.168.0.23) - not running


ping both;
vm22.satimis.com
vm23.satimis.com

works without problem.


On host browser both
[http://vm22.satimis.com](http://vm22.satimis.com)
[http://vm23.satimis.com](http://vm23.satimis.com)```

It Works !

```


On host browser
[http://vm22.satimis.com/sugarcrm](http://vm22.satimis.com/sugarcrm)
[http://vm23.satimis.com/sugarcrm](http://vm23.satimis.com/sugarcrm)

Both of them work, popup SugarCRM login page.  But only vm22 password can login.  So it indicates only connecting vm22 because port 80 forward to it.


2)
Router - Port 80 forward to 192.168.0.23

nginx VM (vm21 - router IP=192.168.0.21) - running
SugarCRM VM (vm22 - router IP=192.168.0.22) - running
SugarCRM VM (vm23) - router IP=192.168.0.23) running

ping both;
vm22.satimis.com
vm23.satimis.com

works without problem.


On host browser both
[http://vm22.satimis.com](http://vm22.satimis.com)
[http://vm23.satimis.com](http://vm23.satimis.com)```

It Works !

```


On host browser
[http://vm22.satimis.com/sugarcrm](http://vm22.satimis.com/sugarcrm)
[http://vm23.satimis.com/sugarcrm](http://vm23.satimis.com/sugarcrm)

Both of them work, popup SugarCRM login page.  But only vm23 password can login.  So it indicates only connecting vm23 because port 80 forward to it.


3)
Router - Port 80 forward to 192.168.0.21 (nginx VM)

nginx VM (vm21 - router IP=192.168.0.21) - running
SugarCRM VM (vm22 - router IP=192.168.0.22) - running
SugarCRM VM (vm23) - router IP=192.168.0.23) running

ping both;
vm22.satimis.com
vm23.satimis.com

works without problem.


On host browser both
[http://vm22.satimis.com](http://vm22.satimis.com)
[http://vm23.satimis.com](http://vm23.satimis.com)```

It Works !

```


On host browser
[http://vm22.satimis.com/sugarcrm](http://vm22.satimis.com/sugarcrm)
[http://vm23.satimis.com/sugarcrm](http://vm23.satimis.com/sugarcrm)

None of them can popup SugarCRM login page.  because port 80 forward to vm21, nginx VM.


Therefore the key point depends on port 80 to where it is forward.


B.R.
satimis

---

### Post by bodhi.zazen on 2009-12-09
First, I suggest you change the default index.html from "it works" to something a bit mroe meaningful, such as "nginx" , "vm22" , and "vm23" so this way you know what machine your are connecting to.

Second, it sounds as if your DNS is working.

If you forward port 80 to your nginx, you should then connect to the appropriate VM,

ie , "http://vm22.satimis.com" yields "vm22" (rather then "it works')
and, "http://vm23.satimis.com" yields "vm23" (rather then "it works')

If that is working, it is then an issue with configuration of sugar.

---

### Post by satimis on 2009-12-09
> **bodhi.zazen said:**
> First, I suggest you change the default index.html from "it works" to something a bit mroe meaningful, such as "nginx" , "vm22" , and "vm23" so this way you know what machine your are connecting to.

That was designed by SugarCRM.  I'll try to find a solution whether I can change them as suggested.


> 
If you forward port 80 to your nginx, you should then connect to the appropriate VM,

I can't check nginx VM on browser because Apache2 is NOT running there.  If port 80 forward to nginx VM, neither "vm22.satimis.com" nor "vm23.satimis.com" displays the test page of Apache2. "It Works!" on browser.


> 
ie , "http://vm22.satimis.com" yields "vm22" (rather then "it works')
and, "http://vm23.satimis.com" yields "vm23" (rather then "it works')

If that is working, it is then an issue with configuration of sugar.
If port 80 forward to 192.168.0.22 (IP of vm22) then I can login SugarCRM running on vm22 (vm22.satimis.com).  Its login password differs from that of vm23 (vm23.satimis.com).  It would rule out the mistake.  I can't login with password of vm23 (vm23.satimis.com).  Therefore I'm sure it is the SugarCRM running on vm22 NOT vm23.


Likewise if port 80 forward to 192.168.0.23 (IP of vm23) then I can login SugarCRM running on vm23 (vm23.satimis.com).  Its login password differs from that of vm22 (vm22.satimis.com).  I can't login with the password of vm22 (vm22.satimis.com).  Therefore I'm sure it is the SugarCRM running on vm23 NOT vm22.

The trick is on port 80 forwarding.

B.R.
satimis

---

