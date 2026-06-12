---
title: "How to reuse Lets Encrypt certificate for another application"
date: 2020-11-12
forum: Server Platforms
---

### Post by joshi82 on 2020-11-12
Greetings,

I am running Antmedia Server, which comes with Lets Encrypt support. I enabled that, everything is fine and fancy. Now I´d like to reuse these certificates for the same machine for my Cockpit installation (which is on another port, certainly). I assume it should work, and if I make a symbolic link from the source files to the destination files it should work. However, I just do not know how/where, as I am not having too much experience with certs and all these different formats.

This is the command to use according a german blog post ([https://blog.wydler.eu/2019/04/22/einrichten-von-cockpit-project-unter-ubuntu/](https://blog.wydler.eu/2019/04/22/einrichten-von-cockpit-project-unter-ubuntu/)) which looks promising:
```
acme.sh --issue --force --keylength 4096 --domain fqdn --standalone \--cert-file /etc/acme.sh/certs/fqdn.crt \
--key-file /etc/acme.sh/certs/fqdn.key \
--ca-file /etc/acme.sh/certs/fqdn.ca.crt \
--fullchain-file /etc/acme.sh/certs/fqdn.chain.pem \
--reloadcmd "cat /etc/acme.sh/certs/fqdn.chain.pem > /etc/cockpit/ws-certs.d/1-fqdn.cert \
cat /etc/acme.sh/certs/fqdn.key >> /etc/cockpit/ws-certs.d/1-fqdn.cert

```

The config file for my domain is /etc/letsencrypt/renewal/myserver.mydomain.com.conf and it contains:
```
version       = 0.27.0archive_dir  = /etc/letsencrypt/archive/myserver.mydomain.com
cert            = /etc/letsencrypt/live/myserver.mydomain.com/cert.pem
privkey       = /etc/letsencrypt/live/myserver.mydomain.com/privkey.pem
chain          = /etc/letsencrypt/live/myserver.mydomain.com/chain.pem
fullchain      = /etc/letsencrypt/live/myserver.mydomain.com/fullchain.pem
```

I assume if I use the files from myserver.mydomain.conf and use it with the command I should be ready to rumble, right? But which files do I have to use then? Or is there another way of achiving that?

Any help is highly appreciated.
Thanks
Joshi

---

### Post by LHammonds on 2020-11-12
If your web site is the exact same URL (and just on different ports) then yes, the cert can be used by multiple sites...no need to copy the files around, just point the sites config directly to the cert.  However, I cannot guarantee it will work since I am unfamiliar with both apps you are using.  My knowledge is from using certs with Apache, Tomcat, IIS.

But, if your cert is for myserver.mydomain.com and you are trying to use it for myotherdomain.mydomain.com it will not likely work (unless the cert is a wildcard cert such as *.mydomain.com).  If they are different FQDN, just create a new let's encrypt cert.  There is no cost involved.

LHammonds

---

### Post by SeijiSensei on 2020-11-13
I run a number of web sites on a single server. I installed certficates for each VirtualHost.  Running certbot-auto will present a list of sites for which a certificate may be issued.

---

### Post by TheFu on 2020-11-13
I use acme.sh too, mainly because I have a mix of static and dynamic websites. They all terminate on the same reverse proxy but the sites are run on multiple, different, systems.  Initially, I put each cert into a single request, but some of the non-public websites started getting hits that made no sense - attacks really.  

After the first certs expired, I switched back to 1 cert per virtual system.  The creation request appears to be missing a newline on the first line. That could break the request.  I'm not an expert on acme.sh, just know enough to have gotten it working here. Because I use nginx and at the time, nginx support didn't properly exist, I think these commands were used to create certs:
```
     # Issue cert
   sudo ./acme.sh --force --issue -d $DOMAIN -w /var/www/$DOMAIN 
     # Deploy cert
   sudo ./acme.sh --force --install-cert -d $DOMAIN \
               --cert-file /etc/nginx/ssl/$DOMAIN/cert.pem \
               --key-file /etc/nginx/ssl/$DOMAIN/key.pem \
               --fullchain-file /etc/nginx/ssl/$DOMAIN/fullchain.pem \
               --reloadcmd     "service nginx force-reload"
```

After that, every 3 months minus 2 weeks, I renew with:
```
sudo ./acme.sh --nginx --renew -d $DOMAIN  --force
```
or
```
sudo ./acme.sh --renew -d $DOMAIN  --standalone --force
```

Depending on whether the web server can be running or not during the cert renewal.  The standalone version has the acme.sh script running a tiny, bash-based, HTTP server.  Since that needs to listen on port 80, it must be run as root.

acme.sh warns against using sudo for any cert work, but because all my nginx config files are root:root owned, so are all the SSL cert files - so, if I want to update those, then sudo is mandatory. Also, the port 80 standalone version requires it too.

I have no clue about Antmedia Server, but I'd bet using the standalone solution will work. Just stop the Antmedia Server first, run the renewal, then restart it.

If you have any restrictive firewalls, know that since Feb 2020, Let's Encrypt requires access from multiple parts of the world for certs to be issued/renewed, so it might be needed to disable the firewall.  Also, port 80/tcp must be accessible from the internet, even if all your servers only work on port 443/tcp.  I think this is foolish, but there must be some reason why.

If using the web server method of authentication doesn't work, there are DNS TXT entry methods, but this requires programmatic access to the DNS records. I suppose manually adding a TXT record for the domain could be done, but I really don't want to login to my DNS provider every 3 months.

Hopefully, this isn't more confusing.

---

