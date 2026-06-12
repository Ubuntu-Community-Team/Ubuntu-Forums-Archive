---
title: "How to create pki validation folder for nextcloud home server"
date: 2021-10-06
forum: Server Platforms
---

### Post by glasshalffull on 2021-10-06
Hi,
I installed Ubuntu Server edition 20.04 on a home computer and during the setup of Ubuntu Server I included the Nextcloud snap as part of the installation process.

Nextcloud is the only thing my Ubuntu Server is running, and the site is launching from a snap folder.

My nextcloud instance is working fine, and is running beautifully (kudos to the Ubuntu Server team to making this such a painless process).

I can access my nextcloud site fine on my local network and from outside of home using my public static IP, the only issue I have is lack of SSL.

All I need to do to get the SSL up and running is create a publicly accessible pki validation folder with a file in it to get my SSL cert.

I am new to Linux and to the terminal and I am really struggling to do this simple step. Maybe nextcloud locks folders and files down really tight?

What I need help with is the following questions;


[LIST=1]
[*]Where do I put the publicly accessible /.well-known/pki-validation/ folder and pki file? Do I put it in one of the snap folders e.g /snap/nextcloud/current/htdocs/ , there is no /var/www/ folder on this server, do I create a /var/www/ folder
[*]Once I have the correct answer to the above question I then need to copy the file from my ~/Downloads folder to that correct location
[*]I assume there might be some commands or .htaccess edits to nextclouds .htaccess file as well? If so I would like some advice here too.
[/LIST]

Hope this all makes sense, on paper it seems like a really simple setup. Public static IP's seem to freak users out when mentioned but they are quite common for home users in Australia, there are several ISP's here that include them as part of their plans (not an optional extra). These plans are often also cheaper than those from the biggest ISP's.

So don't be surprised if you hear of other Australian noob users asking similar questions here.

Also any prayers for myself and my fellow countrymen would be much appreciated, [things are pretty dire here at the moment.]("https://web.archive.org/web/20210903100812/https://www.iflscience.com/policy/australias-new-police-powers-allow-them-to-control-social-media-accounts-delete-data/")

---

### Post by TheFu on 2021-10-07
TLS certs are for the web server, not Nextcloud. Hence, they go where the web server needs them.  I don't use snaps, especially not for servers like this.  Also, I don't allow php webapps to be accessed over the internet unless a full VPN or at least an ssh-socks proxy with ssh-key-based authentication is used. There are just too many ways to hack into webapps, especially for some as complex as nextcloud.

I do run nextcloud.  In my setup, the LTS certs are handled by a reverse proxy server on a different system.  I use Let's Encrypt certs and keep them in /etc/nginx/ssl/{fqdn}/ directories for each website that the reverse proxy handles.  acme.sh (as opposed to certbot) is used to manage my LE certs. Also, I'm using Nginx, not apache, but the ideas are very similar.
```

$ ll /etc/nginx/ssl/nc.jdpfu.com/
total 24
drwxr-xr-x  2 root root 4096 Mar  7  2019 .
drwxr-xr-x 14 root root 4096 Jun 11  2019 ..
-rw-r--r--  1 root root 1838 Aug 30 22:09 cert.pem
-rw-r--r--  1 root root 5589 Aug 30 22:09 fullchain.pem
-rw-------  1 root root 1679 Aug 30 22:09 key.pem
```

You can see that the last updates were at the end of August.  nc.jdpfu.com isn't available over the internet. It can only be reached after the VPN is connected.

Inside the "sites-available/nc.jdpfu.com.conf file, under the **server** section for port 443, the TLS certs are:
```
   ssl_certificate  /etc/nginx/ssl/nc.jdpfu.com/fullchain.pem;
   ssl_certificate_key  /etc/nginx/ssl/nc.jdpfu.com/key.pem;
   ssl_trusted_certificate  /etc/nginx/ssl/nc.jdpfu.com/cert.pem;
```

And I use acme.sh to handle the Let's Encrypt cert requests and renewals.  That's more complex than I'm willing to say in this forum, but there are lots of guides.

Found this guide for running Nextcloud in a LXD container on Ubuntu. It has sections about LE certs and they use apache, which should be helpful.  Not polluting the OS on the physical computer is a very smart idea. Containers have very little overhead, while keeping the applications segmented apart from each other. This means if you ever install another service on the same machine, the dependency collisions will be none, since each should probably go into a container just for that system.  I have Wallabag and Nextcloud on the same system, but inside different containers. It didn't start that way and there were dependency collisions in the version of php and mariadb supported by each.
[https://www.kaisblog.de/2018/04/12/install-nextcloud-and-collabora-in-lxd-containers/](https://www.kaisblog.de/2018/04/12/install-nextcloud-and-collabora-in-lxd-containers/)
Why is this thread marked as solved?  If you solved it, can you please update with how?  That will help others with the same issue, especially for those using the snap package version.

---

