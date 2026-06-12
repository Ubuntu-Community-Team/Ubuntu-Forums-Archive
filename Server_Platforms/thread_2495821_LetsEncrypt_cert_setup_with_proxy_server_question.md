---
title: "LetsEncrypt cert setup with proxy server question"
date: 2024-03-02
forum: Server Platforms
---

### Post by Heeter on 2024-03-02
Hi all,

I have a functioning, existing webserver (Ubuntu22LTS/Nginx/PHP/Mysql/LetsEncrypt) that is directly behind the router. I am trying to put it behind a proxy server (Ubuntu22LTS/nginx/LetsEncrypt). The only extra function I would like the proxy to handle is the LE certs for all the servers that will be behind it.

I have setup the proxy server and have setup LE on it with all the domains that I am using, but I do have a question.

My question is about the existing webserver. How do I setup the webserver to use the LE certs? Should I just completely uninstall the certbot and somehow edit the /etc/nginx/sites-available/DOMAIN.conf file?

Can't really find a functional answer on my searches.

Regards

---

### Post by TheFu on 2024-03-02
I have nginx setup as a reverse proxy and it does all the TLS termination there. After that, the backend systems don't have encryption. They are all HTTP, though I have them generate HTTPS URLs, always.  I use acme.sh to manage my LE certs.  For local static websites that run directly from the proxy nginx instance, those can be applied while nginx is running.  

For the systems with back-ends on other systems, I shutdown my firewall and have acme.sh run a small web server to meet the needs of LE validation checks for the 3 minutes it takes for all my certs to be renewed.  That's the **acme.sh --standalone** method.

I don't do a wildcard cert and I don't do compound certs (with multiple domains specified) because it seems other people watch for them and try to attack internal-only sites protected by LE, but not available over the internet. 

I never got certbot working for my needs and got tired of fighting with it every 77 days  (that's when I renew). My renewals are not automated because I have to take the firewall rules (I use ipset due to how many subnets on the internet I need to block) for LE to allow certs.  They test access with 3 different locations around the world that change all the time.  We (LE and me) have a disagreement over allowing parts of the world to hack my websites, I guess.  Anyway, 3 minutes isn't too bad and those 3 minutes only get access to the acme.sh web-server, not my real internal websites.

Why 77 days?  A few times, I needed over a week to figure out the LE issues, so I didn't want to wait to the 90 day expiry.  And renewing every month is just extra, unneeded work, since I'm doing it manually, though it only takes about 4 minutes of my time now.  Well, not really manually anymore. I have a 25 line script. ;)

I create and update all certs from my HOME on the reverse proxy system. It creates a ~/.acme.sh/ directory. As part of the acme.sh update process, it copies those updates to /etc/nginx/ssl/.  I don't recall if I configured it for that or if that was the default when I told it "nginx".  Taking the IPset rules down is easy.  Rather than remembering how to bring them back up, I just reboot the system.

I don't remember if I or acme.sh modified the nginx config files. Sorry.  I think I manually did it.  I use include files for nginx where it makes sense - things like ssl_ciphers are included to specify the exact LTS version (TLSv1.3 and nothing else) I want and don't want to allow.  Also the SSL session caching and session timeouts are in there.

I'm not willing to post my exact configs, sorry.

---

### Post by Heeter on 2024-03-02
Hi TheFU

So if I understand your post, the proxy server handles the certs, so should I just uninstall and remove all the certbot and ssl cert folders from the existing webserver?

---

### Post by TheFu on 2024-03-03
> **Heeter said:**
> Hi TheFU

So if I understand your post, the proxy server handles the certs, so should I just uninstall and remove all the certbot and ssl cert folders from the existing webserver?

There are 500 different solutions.  My back-end webapps don't have any certs.  Of that, I'm 100% positive.

---

