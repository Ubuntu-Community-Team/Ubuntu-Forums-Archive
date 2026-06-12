---
title: "LetsEncrypt - SSL certificate is not valid"
date: 2021-09-27
forum: Server Platforms
---

### Post by clusterix on 2021-09-27
[COLOR=#000000][FONT=&amp]Distributor Ubuntu 18.04.6 LTS Release: 18.04
[/FONT][/COLOR][COLOR=#2C3E50][FONT=Ubuntu]
since this morning I have found 5 domain names with following error message (LetsEncrypt certs)

[/FONT][/COLOR]```
[COLOR=#2C3E50][FONT=Consolas]SSL certificate is not valid: C = US, O = Internet Security Research Group, CN = ISRG Root X1 error 2 at 2 depth lookup: unable to get issuer certificate[/FONT][/COLOR]
```[COLOR=#2C3E50][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#2C3E50][FONT=Ubuntu]

[/FONT][/COLOR]I then deleted these Letsencrypt certificates, but the error occurs again when I request a new certificate. These certificates were listed as successfully renewed in the letsencrypt log file ...
 something seems to be wrong with the root CA or Apache. There have been some updates recently regarding openssl as well.


The problem only seems to occur with Ubuntu. With Debian 9 & 10 I cannot detect these errors.


Does anyone have an idea how to solve this problem?

---

### Post by LHammonds on 2021-09-27
Did you add a proxy since the last time the certificate was validated?

---

### Post by clusterix on 2021-09-27
no proxy, I have just activated HTTP/2 but it also happen when I disable HTTP/2 incl apache restart.
with Ubuntu the [COLOR=#000000][FONT=monospace]DST_Root_CA_X3 is disabled on Debian 9 it's still available[/FONT][/COLOR]
[FONT=monospace][COLOR=#ffffff]```

[/COLOR][/FONT][code][FONT=monospace][COLOR=#ffffff]/etc/ca-certificates.conf
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]!mozilla/DST_Root_CA_X3.crt[/COLOR]
[/FONT]
```[FONT=monospace][COLOR=#ffffff]


[/COLOR]
[/FONT]

---

### Post by clusterix on 2021-09-27
strange ... it only fails with Ubuntu [COLOR=#000000]18.04.6 LTS[/COLOR]
I use the same configuration with Debian 9 & 10 and there it works ...
that could be a worst case as i use many wordpress with letsencryt

---

### Post by clusterix on 2021-09-27
it happens also when I create a new certificate
is there anything I can do to solve the problem?

---

### Post by LHammonds on 2021-09-27
I have upgraded all my servers to 20.04 long ago.  I'm not experiencing that issue so I'm not sure what can be done to bandaid the issue if it really is an issue with certbot becoming out-of-date on Ubuntu 18.04.

I'll check what version of certbot I have installed on 20.04...

```
apt search certbot-apache
python3-certbot-apache/focal,focal,now 0.39.0-1 all [installed]
```

What version do you have installed?

---

### Post by clusterix on 2021-09-27
it shows
[FONT=monospace][COLOR=#18B218]python-certbot-apache[/COLOR][COLOR=#000000]/bionic,bionic,bionic,bionic 0.23.0-1 all[/COLOR]
  transitional dummy package

[COLOR=#18B218]python-certbot-apache-doc[/COLOR][COLOR=#000000]/bionic,bionic,bionic,bionic 0.23.0-1 all[/COLOR]
  Apache plugin documentation for Certbot

[COLOR=#18B218]python3-certbot-apache[/COLOR][COLOR=#000000]/bionic,bionic,bionic,bionic 0.23.0-1 all[/COLOR]
  Apache plugin for Certbot

[/FONT]

---

### Post by clusterix on 2021-09-27
but as I said, I can request or renew a cert without issues, but the status shows:
[COLOR=#2C3E50][FONT=Consolas]SSL certificate is not valid: C = US, O = Internet Security Research Group, CN = ISRG Root X1 error 2 at 2 depth lookup: unable to get issuer certificate[/FONT][/COLOR]

---

### Post by clusterix on 2021-09-27
[COLOR=#2C3E50][FONT=Ubuntu]it seems the user apache domain_ssl.conf is not created after a create or renew request ...[/FONT][/COLOR]

---

### Post by LHammonds on 2021-09-27
> **clusterix said:**
> it shows
[FONT=monospace][COLOR=#18B218]python-certbot-apache[/COLOR][COLOR=#000000]/bionic,bionic,bionic,bionic 0.23.0-1 all[/COLOR]
  transitional dummy package

[COLOR=#18B218]python-certbot-apache-doc[/COLOR][COLOR=#000000]/bionic,bionic,bionic,bionic 0.23.0-1 all[/COLOR]
  Apache plugin documentation for Certbot

[COLOR=#18B218]python3-certbot-apache[/COLOR][COLOR=#000000]/bionic,bionic,bionic,bionic 0.23.0-1 all[/COLOR]
  Apache plugin for Certbot

[/FONT]
I do not see the [installed] text at the end.  How did you install certbot?  Compiled from source?

Try these commands: 
```
certbot --version
certbot 0.40.0
```

```
which certbot
/usr/bin/certbot
```

---

### Post by clusterix on 2021-09-27
> **LHammonds said:**
> I do not see the [installed] text at the end.  How did you install certbot?  Compiled from source?

Try these commands: 
```
certbot --version
certbot 0.40.0
```

```
which certbot
/usr/bin/certbot
```

thanks for reply!

```

certbot 1.8.0
/usr/local/sbin/certbot


sudo wget https://raw.githubusercontent.com/certbot/certbot/7f0fa18c570942238a7de73ed99945c3710408b4/letsencrypt-auto-source/letsencrypt-auto
chmod a+x letsencrypt-auto
./letsencrypt-auto --dry-run

```

---

### Post by clusterix on 2021-09-27
certbot renew --dry-run works without any error output
maybe something wrong with the Intermediate Certificates?
[https://scotthelme.co.uk/lets-encrypt-old-root-expiration/](https://scotthelme.co.uk/lets-encrypt-old-root-expiration/)

---

### Post by clusterix on 2021-09-27
some more details

```

# [FONT=monospace][COLOR=#000000]openssl s_client -connect co2avatar.org:443 -servername co2avatar.org -showcerts[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]issuer=C = US, O = Let's Encrypt, CN = R3[/COLOR]

---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 4595 bytes and written 396 bytes
Verification: OK
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)

[/FONT][FONT=monospace][COLOR=#000000]---[/COLOR]
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 407F1D7B08AED29BE618126CF34381CC3247B5A889A22FC71389AE8DCD7763E4
    Session-ID-ctx:  
    Resumption PSK: 93350F9B4946873A683373870A0BAEDBC380E1CCA51FDB8298379C1E8BEC315800F6B1B621D604351CED2EBE29A5B7C1
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 5f 52 15 c7 eb 77 bf d2-fd 39 7a 90 ee 39 46 65   _R...w...9z..9Fe
    0010 - 15 36 a0 68 05 97 1b 64-ad 3f 6f ef dd d5 cf 80   .6.h...d.?o.....

    Start Time: 1632763996
    Timeout   : 7200 (sec)
    Verify return code: 0 (ok)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 81211663644805CE07998F7D255386F3F6431E35D4D4ACCF83B48A4D5BABE571
    Session-ID-ctx:  
    Resumption PSK: A7424C58C4746163739FCA829D7D50F1362A859BDD823BF7AD99D3603D1F2EE4CB19190165577A0794A8216E8A8E99C2
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 95 21 52 17 c3 3f 8a eb-23 1c ce e2 cc 71 f3 12   .!R..?..#....q..
    0010 - 64 f3 fe 85 d6 90 c2 f0-25 95 0e d1 d5 05 d9 c9   d.......%.......

    Start Time: 1632763996
    Timeout   : 7200 (sec)
    Verify return code: 0 (ok)
    Extended master secret: no
    Max Early Data: 0

[/FONT][FONT=monospace]
[/FONT]
```

---

### Post by LHammonds on 2021-09-27
```
ls -l /var/lib/letsencrypt/
```

My results:
```
drwxr-xr-x 2 root root 4096 Oct  5  2020 backups
drwxr-xr-x 2 root root 4096 Mar 31 18:22 http_challenges
```
When doing a cert request on my system, the web service (www-data) needs access to read the "http_challenges" folder during the challenge/response...which the permissions that are set allows (755).

Is this the same place it uses on your system and are the permissions correct?

Beyond this, I just don't know.  I've not needed to trouble-shoot certbot much except when there were permission problems or proxies involved.

LHammonds

---

### Post by clusterix on 2021-09-28
> **LHammonds said:**
> ```
ls -l /var/lib/letsencrypt/
```

My results:
```
drwxr-xr-x 2 root root 4096 Oct  5  2020 backups
drwxr-xr-x 2 root root 4096 Mar 31 18:22 http_challenges
```
When doing a cert request on my system, the web service (www-data) needs access to read the "http_challenges" folder during the challenge/response...which the permissions that are set allows (755).

Is this the same place it uses on your system and are the permissions correct?

Beyond this, I just don't know.  I've not needed to trouble-shoot certbot much except when there were permission problems or proxies involved.

LHammonds


thank you!
it just shows a backup folder
```

[FONT=monospace][COLOR=#000000]ls -l /var/lib/letsencrypt/[/COLOR]
total 4
drwxr-xr-x 2 root root 4096 Sep 27 17:47 [COLOR=#5454FF]**backups**[/COLOR]
[/FONT]
```

the certificates are created under /etc/letsencrypt/* but the apache2 vhost-ssl.conf is no longer created, it seems the validation process no longer works after the latest ubuntu updates
this system worked well for about 2 years ... something has probably changed because of the DST Root CA X3 Expiration (maybe preparations for the event on sept. 30)
[https://medium.com/geekculture/will-you-be-impacted-by-letsencrypt-dst-root-ca-x3-expiration-d54a018df257](https://medium.com/geekculture/will-you-be-impacted-by-letsencrypt-dst-root-ca-x3-expiration-d54a018df257)

ssl part apache vhost-ssl.conf
```

    SSLEngine On
    SSLCertificateFile      "/var/www/imscp/gui/data/certs/domainname.com.pem"
    Header always set Strict-Transport-Security "max-age=0; includeSubDomains"
    SuexecUserGroup vu1763 vu1763

```

---

### Post by clusterix on 2021-09-28
I have bought a standard certificate (PositiveSSL) for testing, it works without any issues ...
 so it cannot be caused due to apache config. something in openssl or root certificates (CA) prevents a successful validation w/ letsencrypt

---

### Post by clusterix on 2021-09-28
debug output points to CAfile
```

[Tue Sep 28 11:05:05 2021] [debug] iMSCP::Execute::execute: openssl pkey -in /tmp/mBG_0sclG3 -noout
[Tue Sep 28 11:05:05 2021] [debug] iMSCP::Execute::execute: openssl verify -CAfile /tmp/mzaB8wQu9V -purpose sslserver /tmp/hOq4QUp2Tb
[Tue Sep 28 11:05:05 2021] [debug] iMSCP::OpenSSL::validateCertificate: error /tmp/hOq4QUp2Tb: verification failed

```

---

### Post by clusterix on 2021-09-28
certs are created under /etc/letsencrypt/* now I have added by hand the certs into the controlpanel SSL cert section
same error message:


SSL certificate is not valid: C = US, O = Internet Security Research Group, CN = ISRG Root X1 error 2 at 2 depth lookup: unable to get issuer certificate


which shows that something does not work with the letsencrypt validation procedure, a purchased positive ssl certificate works

---

### Post by clusterix on 2021-09-28
this one is still active and working my web browser shows as valid cert
I have checked with openssl verify


Ubuntu 18.04.6 LTS result:
```

# openssl verify -CAfile fullchain1.pem cert1.pem
C = US, O = Let's Encrypt, CN = Let's Encrypt Authority X3
error 2 at 1 depth lookup: unable to get issuer certificate
error cert2.pem: verification failed

```


Debian 9 & 10 result:
```

# openssl verify -CAfile fullchain1.pem cert1.pem
cert1.pem: OK

```

---

### Post by clusterix on 2021-09-28
after copying following certificate from Debian to Ubuntu it works
/usr/lib/ssl/certs/2e5ac55d.0


why is the cert not present in Ubuntu 18.04.6 LTS?

---

### Post by LHammonds on 2021-09-29
Your installation of certbot is not how I have mine installed so I don't know the differences.

This is how I installed it on my servers:

```
sudo apt install certbot python3-certbot-apache
```

---

### Post by clusterix on 2021-09-29
Thanks for replying!
I've already tried this but the missing certificate was not installed
```

sudo apt-get --reinstall install certbot python3-certbot-apache ca-certificates libarray-diff-perl libconvert-asn1-perl libdatetime-format-strptime-perl

```

```

cat /usr/lib/ssl/certs/2e5ac55d.0

[FONT=monospace][COLOR=#000000]-----BEGIN CERTIFICATE-----[/COLOR]
MIIDSjCCAjKgAwIBAgIQRK+wgNajJ7qJMDmGLvhAazANBgkqhkiG9w0BAQUFADA/
MSQwIgYDVQQKExtEaWdpdGFsIFNpZ25hdHVyZSBUcnVzdCBDby4xFzAVBgNVBAMT
DkRTVCBSb290IENBIFgzMB4XDTAwMDkzMDIxMTIxOVoXDTIxMDkzMDE0MDExNVow
PzEkMCIGA1UEChMbRGlnaXRhbCBTaWduYXR1cmUgVHJ1c3QgQ28uMRcwFQYDVQQD
Ew5EU1QgUm9vdCBDQSBYMzCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEB
AN+v6ZdQCINXtMxiZfaQguzH0yxrMMpb7NnDfcdAwRgUi+DoM3ZJKuM/IUmTrE4O
rz5Iy2Xu/NMhD2XSKtkyj4zl93ewEnu1lcCJo6m67XMuegwGMoOifooUMM0RoOEq
OLl5CjH9UL2AZd+3UWODyOKIYepLYYHsUmu5ouJLGiifSKOeDNoJjj4XLh7dIN9b
xiqKqy69cK3FCxolkHRyxXtqqzTWMIn/5WgTe1QLyNau7Fqckh49ZLOMxt+/yUFw
7BZy1SbsOFU5Q9D8/RhcQPGX69Wam40dutolucbY38EVAjqr2m7xPi71XAicPNaD
aeQQmxkqtilX4+U9m5/wAl0CAwEAAaNCMEAwDwYDVR0TAQH/BAUwAwEB/zAOBgNV
HQ8BAf8EBAMCAQYwHQYDVR0OBBYEFMSnsaR7LHH62+FLkHX/xBVghYkQMA0GCSqG
SIb3DQEBBQUAA4IBAQCjGiybFwBcqR7uKGY3Or+Dxz9LwwmglSBd49lZRNI+DT69
ikugdB/OEIKcdBodfpga3csTS7MgROSR6cz8faXbauX+5v3gTt23ADq1cEmv8uXr
AvHRAosZy5Q6XkjEGB5YGV8eAlrwDPGxrancWYaLbumR9YbK+rlmM6pZW87ipxZz
R8srzJmwN0jP41ZL9c8PDHIyh8bwRLtTcm1D9SZImlJnt1ir/md2cXjbDaJWFBM5
JDGFoqgCWjBH4d1QB7wCCZAA62RjYJsWvIjJEubSfZGL+T0yjWW06XyxV3bqxbYo
Ob8VZRzI9neWagqNdwvYkQsEjgfbKbYK7p2CNTUQ
-----END CERTIFICATE-----
[/FONT]
```

---

### Post by LHammonds on 2021-09-29
Re-install of binaries won't fix any configuration issues.

MAKE SURE YOU HAVE A BACKUP

I would purge everything off the server related to certbot (especially its config files) and then install from scratch.

MAKE SURE YOU HAVE A BACKUP

LHammonds

---

### Post by clusterix on 2021-09-29
thank you!
for now it works, I will wait & see what happens after the LetsEncrypt changes on sept. 30 :P

---

### Post by TheFu on 2021-10-05
I had some issues a few years ago and switched from using certbot to using acme.sh.
About 18 months ago, Let's Encrypt changed some of their policies and started requiring that random sites around the world have access to the website or they wouldn't issue certs.  I was blocking access from many countries where attacks against my servers were originating with a huge set of ipset subnets.  For a few weeks, I couldn't understand that my firewall blocks was preventing VPS servers in these locations from access, so LE refused to renew certs.  Then I accidentally disabled the firewall and ran the update process ... and all the certs were renewed, quickly.  Instead of ~3min per cert, all of them were being renewed in under 2 minutes. It was amazing.  
The last 15+ months, I've disabled my ipset rules, run the cert renewal process, then re-enabled them every 75 days or so. Works well.

It is nice to spend just a few minutes on these things.  I don't really trust automation for something so important that happens so seldom.  My calendar has an entry to renew. That's the least I can do - watch a script run while it renews.

99% of the how-to guides explain how to get a new cert, but they all gloss over renewal. In theory, renewals should be trivial and much easier.  I also dislike how they say not to run as root ... if not as root, how can the renewal certs get placed where they have to be for nginx to pick up the new certs?  Riddle me that one Batman.

---

### Post by kevdog on 2021-10-06
@TheFu

Do you find acme.sh easier to work with than certbot?  I use a combination of both tools and can't figure out what I like better.  Acme.sh is very chatty as I see it modifies a lot of its own configuration files quite frequently.

---

### Post by TheFu on 2021-10-06
> **kevdog said:**
> @TheFu

Do you find acme.sh easier to work with than certbot?  I use a combination of both tools and can't figure out what I like better.  Acme.sh is very chatty as I see it modifies a lot of its own configuration files quite frequently.

There wasn't any grand scheme of thought involved.

Certbot wasn't working, likely due to my ignorance, since 1M+ other people use it fine. ;)  After screwing around with it for a few hours over a month and being unsuccessful at renewal, it was time to move on.

acme.sh was easier and more understandable **TO ME** for how things work. The code is right there to read.  I've changed from 1 cert per domain to 1 cert with all the CN in it and back to 1 cert per domain.  Seems that attackers are looking at certs to decide which domains to attack, so having an all-in-one cert wasn't helping combat attackers.  
Plus, I have certs on mixed systems and stand alone systems, some with multiple backends going through a reverse proxy/load balancer.  A few are not available on the internet, but we still wanted LE certs to keep the internal users from browser issues.   The acme.sh standalone method of renewal worked and was easy to get working.  I really should be using DNS to prove domain ownership, but that isn't easy to automate with multiple DNS providers - some only have web interfaces.  I'd rather bring down all the websites for 2 minutes every 77 days during renewal.

Did I mention that I use a mix of nginx, apache and custom web-apps that don't use either?

---

### Post by kevdog on 2021-10-07
Honestly just sounds like you would simply some things by using a Traefik for Caddy reverse proxy for auto certificate management.  I'm aware you might want the certificates for other reasons however.  In terms of multiple DNS providers -- yeah that kind of painful -- however just use the ones that integrate with DNS challenge (:p)

---

### Post by TheFu on 2021-10-08
> **kevdog said:**
> Honestly just sounds like you would simply some things by using a Traefik for Caddy reverse proxy for auto certificate management.  I'm aware you might want the certificates for other reasons however.  In terms of multiple DNS providers -- yeah that kind of painful -- however just use the ones that integrate with DNS challenge (:p)

a) we don't (won't) use docker. The idea of using dockerhub is just too scary.
b) it ain't broke, so why fix it?
c) I'm not anti-GoLang, but it would be something else to be installed. We decided against using Puppet and Chef over the Ruby requirement - I love Ruby, BTW.

---

