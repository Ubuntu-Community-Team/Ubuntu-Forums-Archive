---
title: "SOLVED: SSL | Letsencrypt | certbot on Apache on Raspbian Stretch | HTTPS"
date: 2018-03-31
forum: Server Platforms
---

### Post by adriaan4 on 2018-03-31
OK, I know this is the Ubuntu forum, but you may consider this helpful anyway:

I installed letsencrypt for secure HTTP on my little Raspberry Pi.

Got ± 60 mails the the automated renewal was not well, invoked by crontab enty
```
* 7,19 * * * certbot -q renew
```

So I got
> 
Cert is due for renewal, auto-renewing...
     Renewing an existing certificate
     Performing the following challenges:
     http-01 challenge for yourdomain.com
     Waiting for verification...
     Cleaning up challenges
     Unable to clean up challenge directory     /var/www/yourdomain/.well-known/acme-challenge
     Attempting to renew cert from     /etc/letsencrypt/renewal/yourdomain.com.conf produced an unexpected     error: Failed authorization procedure. yourdomain.com (http-01):     urn:acme:error:unauthorized :: The client lacks sufficient     authorization :: Invalid response from     [http://yourdomain.com/.well-known/acme-challenge/yourdomain.com]("http://dudeweb.nl/.well-known/acme-challenge/tJRdpwn_sgbhdaD30sVZRHeCfuq39cNAhswSLARIGuE"):     "<br><br><br><br><p><table     align="center" style="font-family: Verdana, Arial, Helvetica;     font-size: 10pt;"><tr><td>
     <h3>
     Error 40". Skipping.
     
     All renewal attempts failed. The following certs could not be     renewed:
       /etc/letsencrypt/live/yourdomain.com/fullchain.pem (failure)
     1 renew failure(s), 0 parse failure(s)
     
     IMPORTANT NOTES:
      - The following errors were reported by the server:
     
        Domain: yourdomain.com
        Type:   unauthorized
        Detail: Invalid response from
            [http://yourdomain.com/.well-known/acme-challenge/blablahashcode]("http://dudeweb.nl/.well-known/acme-challenge/tJRdpwn_sgbhdaD30sVZRHeCfuq39cNAhswSLARIGuE"):
        "<br><br><br><br><p><table     align="center" style="font-family:
        Verdana, Arial, Helvetica; font-size:     10pt;"><tr><td>
        <h3>
        Error 40"
     
     [COLOR=#ff0000]   To fix these errors, please make sure that       your domain name was
         entered correctly and the DNS A record(s) for that domain
         contain(s) the right IP address.[/COLOR]

After A LOT of time, the only thing I really needed to to was upgrade to new certbot.
```
*certbot --version*
```[I]
> certbot 0.10.2
[/I]```
*apt-get install python-certbot-apache -t stretch-backports*
```[I]
```
*certbot --version*
```
> *certbot 0.21.1*
[/I]

---

