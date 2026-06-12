---
title: "Use Docker app with existing LAMP installation"
date: 2022-03-27
forum: Virtualisation
---

### Post by lister171254 on 2022-03-27
I've posted this question in the Docker and Bitwarden forums, but have so far had only one suggestion

This either means that what I try to do is so simple that it's obvious or what I'm trying to do is so silly that nobody would do this.

I’m running my own mail and cloud server on the latest LTS Ubuntu Server.

I’m using Apache (with a letsencrypt cert) for the cloud (Nextcloud) and am looking at installing BitWarden to make pw management easier.

Bitwarden,however, only comes in Docker, which complicates things somewhat (at least for me).

I can’t seem to find a standard approach of interacting a docker instance with an non docker Webserver (Apache).

One suggestion I did find is to reverse proxy the Aapache Server, but even that suggestion was vague on what has to happen on the docker side (i.e. how can I use my letsencypt cert in Docker)

Any pointers are greatly appreciated

---

### Post by TheFu on 2022-03-27
The LE cert would terminate on the reverse proxy, not inside docker.

I don't use docker. Know it only from a high level.  I have no clue about bitwarden, but the idea of having password management in a webapp fails my smell test. Just seems like a very, very, very, bad idea.  It is up there with allowing a remote desktop using a web browser.  Terrible idea, at least for my "smells bad" test. I can't imagine running bitwarden (or a remote desktop) on someone else's hardware, on someone else's network, either. Heck, I run an email gateway in the cloud, but keep the email server itself on our hardware, on our network, in our building. Access by users to email requires using a full VPN. No VPN, no email access for our users.

I don't use apache.

I use nginx as both a static website server and as a reverse proxy for other back-ends.  It is pretty trivial, provided you already know how webservers and proxies work.  Some people might use ha-proxy or some other reverse proxy instead.  I suppose the trick is which reverse proxy supports LE certs? I know nginx does.

---

### Post by kevdog on 2022-04-04
What exactly are you having problems with?  Are you having problems reverse proxying from Apache to the Bitwarden docker container? Docker containers have an internal IP address within the container network, but depending on how you setup your compose file, they also can be reached using the docker host's IP address (or Domain name) with a specified port.  It's possible to reverse proxy on the local machine to the local machine and port used by the docker container.

---

### Post by TheFu on 2022-04-05
I just watched a Getting Started with Docker video and learned a bunch.

Docker containers get placed onto a subnet that only the host can see. I'm guessing it is a host-only non-routible subnet, 172.x.x.x.
When a Docker container is run, a port from the host IP to the container IP can be prequested using the -p option  **-p 80:8888** would forward all inbound port 80 on the host IP to the docker container port 8888.  Seems pretty simple.  You'll probably want to forward port 443:8443 if the LE cert has been installed **inside** the container itself.  If it were me, I'd run a TLS termination load balancer on the docker host, then forward unencrypted traffic to the different containers as needed.  This way, scaling out wouldn't be too hard and a new cert wouldn't be needed for each container.
So, if you need to use 2 docker containers then you'll want to forward to specific docker IPs and ports as needed.  There are many ways to accomplish this, but if you
load balancer/LE Cert termination runs on the host
The load balancer would use DNS name-based to forward traffic on 443 to the correct back-end after the TLS connection has been terminated there.  Different back-end servers can be handle by-name in nginx using the typical 'server' stanza with an upstream defined.
```
upstream myproxy {
       server 172.22.22.41:9000;
       server 172.22.22.41:9001;
}
server {
   listen 443 ssl ;
   server_name nc.your-domain.com
 .....
   location / {
      ...
      try_files $uri $uri/index $uri/index.html $uri.html @myproxy;
   }
   location @myproxy {
                proxy_set_header  X-Real-IP  $remote_addr;
                proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
                # proxy_set_header  Host $remote_addr;
                proxy_set_header  Host $http_host;
                proxy_redirect    off;
                proxy_cache       one;
                proxy_pass [http://myproxy](http://myproxy) ;
     }
}
```
And something similar for bitwarden.
Lots of details, which are specific to your needs would be necessary in the reverse proxy setup.  My file which includes the lines above, is 317 lines long. Much of that is for extra security to block sql-injection, bad referrers, and some other nasty attacks.  Plus, I have includes for more general stuff, like white listed subnets which get access.  I also use a micro-cache to speed performance when multiple clients are accessing the system. It is amazing how much the load can be reduced with a 15 second request cache.

I only know nginx, so if you choose something else, while the ideas will be similar, the exact commands and settings will be different.  My complete nginx setup isn't something I'm willing to share - security.  All of it was available by reading the nginx manual.

---

### Post by lister171254 on 2022-04-05
As I've set Docker up with ports 8080 and 8443 I have set Apache up as follows

```
<VirtualHost *:80>

	ServerName bitwarden.mydomain.com
        ServerAlias bitwarden.mydomain.com
	
	Redirect permanent / https://bitwarden.mydomain.com

```

```
<IfModule mod_ssl.c>
	<VirtualHost _default_:443>

                ServerName bitwarden.mydomain.com
                ServerAlias bitwarden.mydomain.com


 		ProxyPass / https://bitwarden.mydomain.com:8443/
 		ProxyPassReverse / https://bitwarded.mydomain.com:8443/
 		RewriteEngine on

 		SSLProxyEngine On
 		SSLProxyVerify none
 		SSLProxyCheckPeerCN off
 		SSLProxyCheckPeerExpire off

        SSLCertificateFile     /etc/letsencrypt/live/mydomain.com/fullchain.pem

        SSLCertificateKeyFile          /etc/letsencrypt/live/mydomain.com/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf
        </VirtualHost>

</IfModule>
```

It all works, I just want to check that I didn't do something stupid.

---

### Post by kevdog on 2022-04-06
@lister171254

I don't use Apache as a reverse proxy, however with any reverse proxy -- where do you want your encrypted TLS to terminate.  Reverse proxies by nature can be #1 TLS terminating - #2 TLS TCP Passthrough - or #3 TL terminating and re-encrypting.  @TheFu gave an example of #1 - a TLS terminating proxy.  With your reverse proxy lines ProxyPass ProxyPassReverse youare connecting to your bitwarden container using TLS.  You've basically in essence are writing your configuration as a TLS terminating and TLS re-encryption proxy.  With this setup you'll let SSL Certificates installed both at the reverse proxy and within the Bitwarden Container (which is totally fine -- but just wanted to let you know what you're writing).  Vaultwarden (formerly Bitwarden_RS) is my only setup which I run things as option #3 (decrypt-re-encrypt).

---

### Post by lister171254 on 2022-04-08
Hmmm,
My Bitwarden container has no SSL certificates.

---

### Post by kevdog on 2022-04-10
I dont know how Apache reverse proxies -- in the sense -- I don't know if it verifies the certificate (or lack of certificate) provided by the Bitwarden end.  I've used Nginx in the past and I think the setting is ProxySSLVerify however I don't know the equivalent Apache syntax.  

Ahhh relooking at your code from above:

```


 		SSLProxyEngine On
 		SSLProxyVerify none
 		SSLProxyCheckPeerCN off
 		SSLProxyCheckPeerExpire off

```

So basically you are telling apache dont verify the proxy (which is usually done against /etc/ssl/cert.pem which is a master list of the CA certificates), Dont check for any Expired Certificates.  In terms of the PeerCN -- I don't even know if this is valid for more Apache Modern Releases:

```

This directive sets whether the remote server certificate's CN field is compared against the hostname of the request URL. If both are not equal a 502 status code (Bad Gateway) is sent. SSLProxyCheckPeerCN is superseded by SSLProxyCheckPeerName in release 2.4.5 and later.

In all releases 2.4.5 through 2.4.20, setting SSLProxyCheckPeerName off was sufficient to enable this behavior (as the SSLProxyCheckPeerCN default was on.) In these releases, both directives must be set to off to completely avoid remote server certificate name validation. Many users reported this to be very confusing.

As of release 2.4.21, all configurations which enable either one of the SSLProxyCheckPeerName or SSLProxyCheckPeerCN options will use the new SSLProxyCheckPeerName behavior, and all configurations which disable either one of the SSLProxyCheckPeerName or SSLProxyCheckPeerCN options will suppress all remote server certificate name validation. Only the following configuration will trigger the legacy certificate CN comparison in 2.4.21 and later releases;

```

So basically if you're not validating the proxy, or checking for expired certificates -- then what is the point exactly of re-encrypting to the backend?

---

### Post by lister171254 on 2022-04-11
As I pointed out in my original post, I'm somewhat out of my knowledge zone when it comes to integrating a docker web site with and existing Apache server. 

I tried to follow what little info is on the web to do this and the proxy setup I have right now works with my existing wildcard letsencrypt cert.

Bitwarden running in Docker doesn't have a certificate and my limited understanding is that it doesn't need it. The proxy for me just maps the docker port to the standard apache port(s).

I could, of course, have all of this completely wrong

---

### Post by kevdog on 2022-04-11
You don't need a certificate per se to run Bitwarden on the backend. Right now you are just proxying a re-encrypted connection to a proxy on the backend that is verified.  Usually reverse proxies by default to verify the certificate presented by the backend server -- you usually have to configure your reverse proxy specifically to verify the backend certificate being presented. I'm only pointing this out to you not to bust your balls, but just point out how your current setup is configured.  I took me a long time to figure this out for myself actually.

---

### Post by lister171254 on 2022-04-14
I really appreciate your feedback but am somewhat surprised that with the vast number of Ubuntu users there is no more info on how to do this 'properly'.

When I go to [https://bitwarden.mydomain.com](https://bitwarden.mydomain.com) and check the certificate I get the attached, which looks correct.

[ATTACH=CONFIG]290286[/ATTACH]

---

### Post by kevdog on 2022-04-14
@lister171254 -- Thanks for keeping the thread alive.

A couple of things. Is your [https://bitwarden.mydomain.com](https://bitwarden.mydomain.com) URL the URL of the reverse proxy or the URL of the docker bitwarden installation?  Here's a couple of things I'm assuming and correct me if I'm wrong

1. You are running apache natively as your reverse proxy running on Machine A which listens on ports 80/443.
2. On the same Machine A - you are running docker bitwarden which is listening on which ports??
3. You are reverse proxying from Apache to Bitwarden on the same machine
4. On your network -- what controls your DNS lookups?

Thanks -- I just want to make sure I'm not confusing your setup.

---

### Post by lister171254 on 2022-04-14
I currently have a few websites (nextcloud.mydomain.com, mypics.mydomain.com, bitwarden.mydomain.com), all on the same server, set up as virual apache hosts.

The bitwarden virtual host is set up as per my Post #5 in this thread.

So when I go to bitwarden.mydomain.com, Apache proxies this to port [https://bitwarden.mydomain.com:8443/](https://bitwarden.mydomain.com:8443/), which is the port I set up in the Docker container for bitwarden.

Following are the answers to your questions

------------------------
1. You are running apache natively as your reverse proxy running on Machine A which listens on ports 80/443.
Correct
2. On the same Machine A - you are running docker bitwarden which is listening on which ports??
Bitwarden listens on 8443 only
3. You are reverse proxying from Apache to Bitwarden on the same machine
Correct
4. On your network -- what controls your DNS lookups?
I'm using Unbound as a local DNS resolver
-----------------------

Cheers

---

### Post by TheFu on 2022-04-15
> **lister171254 said:**
> I really appreciate your feedback but am somewhat surprised that with the vast number of Ubuntu users there is no more info on how to do this 'properly'. 

Most users here are desktop-only people.

When it comes to server setups, everyone has different knowledge and skills, because there is always 50 different ways to accomplish the same task.  We use what works for our needs, skills, and comfort.  The fact that it isn't fitting with your plans isn't surprising at all to me.

People who work in enterprises that might setup a similar solution are all ... er ... working. They have little desire to post on forums after hours.  When I was in the corporate world, I never posted on forums and I wasn't active in F/LOSS unless it directly related to my $dayjob.  That only happened once and it was just some software that was very popular at the time on all Unix systems using 1 vendor's compatibility libraries for about 20 different DBMS solutions.

---

### Post by kevdog on 2022-04-16
Could you post your compose file for Bitwarden? Or just the section used for the bitwarden service?

---

### Post by lister171254 on 2022-04-17
Following is the docker-compose.yml file

```

#
# Useful references:
# https://docs.docker.com/compose/compose-file/
# https://docs.docker.com/compose/reference/overview/#use--f-to-specify-name-and-path-of-one-or-more-compose-files
# https://docs.docker.com/compose/reference/envvars/
#
#########################################################################
# WARNING: This file is generated. Do not make changes to this file.    #
# They will be overwritten on update. If you want to make additions to  #
# this file, you can create a `docker-compose.override.yml` file in the #
# same directory and it will be merged into this file at runtime. You   #
# can also manage various settings used in this file from the           #
# ./bwdata/config.yml file for your installation.                       #
#########################################################################

version: '3'

services:
  mssql:
    image: bitwarden/mssql:1.47.1
    container_name: bitwarden-mssql
    restart: always
    stop_grace_period: 60s
    volumes:
      - ../mssql/data:/var/opt/mssql/data
      - ../logs/mssql:/var/opt/mssql/log
      - ../mssql/backups:/etc/bitwarden/mssql/backups
    env_file:
      - mssql.env
      - ../env/uid.env
      - ../env/mssql.override.env

  web:
    image: bitwarden/web:2.27.0
    container_name: bitwarden-web
    restart: always
    volumes:
      - ../web:/etc/bitwarden/web
    env_file:
      - global.env
      - ../env/uid.env

  attachments:
    image: bitwarden/attachments:1.47.1
    container_name: bitwarden-attachments
    restart: always
    volumes:
      - ../core/attachments:/etc/bitwarden/core/attachments
    env_file:
      - global.env
      - ../env/uid.env

  api:
    image: bitwarden/api:1.47.1
    container_name: bitwarden-api
    restart: always
    volumes:
      - ../core:/etc/bitwarden/core
      - ../ca-certificates:/etc/bitwarden/ca-certificates
      - ../logs/api:/etc/bitwarden/logs
    env_file:
      - global.env
      - ../env/uid.env
      - ../env/global.override.env
    networks:
      - default
      - public

  identity:
    image: bitwarden/identity:1.47.1
    container_name: bitwarden-identity
    restart: always
    volumes:
      - ../identity:/etc/bitwarden/identity
      - ../core:/etc/bitwarden/core
      - ../ca-certificates:/etc/bitwarden/ca-certificates
      - ../logs/identity:/etc/bitwarden/logs
    env_file:
      - global.env
      - ../env/uid.env
      - ../env/global.override.env
    networks:
      - default
      - public

  sso:
    image: bitwarden/sso:1.47.1
    container_name: bitwarden-sso
    restart: always
    volumes:
      - ../identity:/etc/bitwarden/identity
      - ../core:/etc/bitwarden/core
      - ../ca-certificates:/etc/bitwarden/ca-certificates
      - ../logs/sso:/etc/bitwarden/logs
    env_file:
      - global.env
      - ../env/uid.env
      - ../env/global.override.env
    networks:
      - default
      - public

  admin:
    image: bitwarden/admin:1.47.1
    container_name: bitwarden-admin
    restart: always
    depends_on:
      - mssql
    volumes:
      - ../core:/etc/bitwarden/core
      - ../ca-certificates:/etc/bitwarden/ca-certificates
      - ../logs/admin:/etc/bitwarden/logs
    env_file:
      - global.env
      - ../env/uid.env
      - ../env/global.override.env
    networks:
      - default
      - public

  icons:
    image: bitwarden/icons:1.47.1
    container_name: bitwarden-icons
    restart: always
    volumes:
      - ../ca-certificates:/etc/bitwarden/ca-certificates
      - ../logs/icons:/etc/bitwarden/logs
    env_file:
      - global.env
      - ../env/uid.env
    networks:
      - default
      - public

  notifications:
    image: bitwarden/notifications:1.47.1
    container_name: bitwarden-notifications
    restart: always
    volumes:
      - ../ca-certificates:/etc/bitwarden/ca-certificates
      - ../logs/notifications:/etc/bitwarden/logs
    env_file:
      - global.env
      - ../env/uid.env
      - ../env/global.override.env
    networks:
      - default
      - public

  events:
    image: bitwarden/events:1.47.1
    container_name: bitwarden-events
    restart: always
    volumes:
      - ../ca-certificates:/etc/bitwarden/ca-certificates
      - ../logs/events:/etc/bitwarden/logs
    env_file:
      - global.env
      - ../env/uid.env
      - ../env/global.override.env
    networks:
      - default
      - public

  nginx:
    image: bitwarden/nginx:1.47.1
    container_name: bitwarden-nginx
    restart: always
    depends_on:
      - web
      - admin
      - api
      - identity
    ports:
      - '8443:8443'
    volumes:
      - ../nginx:/etc/bitwarden/nginx
      - ../letsencrypt:/etc/letsencrypt
      - ../ssl:/etc/ssl
      - ../logs/nginx:/var/log/nginx
    env_file:
      - ../env/uid.env
    networks:
      - default
      - public


networks:
  default:
    internal: true
  public:
    internal: false

```

---

### Post by kevdog on 2022-04-17
@lister171254

I had to look at your compose file for awhile -- and then it dawned on me -- you are using the official bitwarden docker images.  I'm using vaultwarden and the setup is a lot different. 

I see within your docker compose file you actually have nginx listening on port 443.  I suppose in this context nginx is acting as a web server rather than a reverse proxy.  It's funny you have an Apache reverse proxy in front of an nginx web server -- probably could combine the two functions if you wanted although their are some advantages to keeping them separate.

---

### Post by lister171254 on 2022-04-18
Yep, a bog standard bitwarden install.

As I mentioned in post #13, as I already used apache for my nextcloud instances and I wanted to keep using the standard web ports, what I have right now seems to be the way to use a docker webapp.

---

