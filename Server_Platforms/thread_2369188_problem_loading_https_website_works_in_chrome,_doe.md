---
title: "problem loading https website: works in chrome, does not work on IE and firefox."
date: 2017-08-19
forum: Server Platforms
---

### Post by openeye86 on 2017-08-19
Hello everyone,

First of all some information about the environment:

domain: biebelfoodies.global
Ubuntu version: 16.04
nginx version: nginx/1.10.3
PHP 7.0.22

firefox version:54.0.1 
chrome: [FONT=Roboto]60.0.3112.101
[FONT=arial]
Cert auth org: Let's encrypt![/FONT][/FONT]

The issue is that when I try to load the webpage in google chrome, it works perfectly.
In firefox, it just gives me a blank page.
On internet explorer it gives me a "cant reach the server."

You can check it here on this website:
[https://www.browserling.com/](https://www.browserling.com/)
Use windows 7 and the latest firefox and internet explorer


The nginx block:

```
server {

        listen 443 ssl http2;
        listen [::]:443 ssl http2;
        root /home/www/hosting/biebelfoodies.global/;
        index index.html index.htm index.php;
        server_name biebelfoodies.global;
        access_log /home/www/logs/biebelfoodies.global/access.log;
        error_log /home/www/logs/biebelfoodies.global/error.log;

location / {
        try_files $uri $uri/ =404;
}
ssl_certificate /etc/letsencrypt/live/biebelfoodies.global/fullchain.pem; # managed by Certbot
ssl_certificate_key /etc/letsencrypt/live/biebelfoodies.global/privkey.pem; # managed by Certbot
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        ssl_ciphers EECDH+CHACHA20:EECDH+AES128:RSA+AES128:<cut>
        ssl_dhparam  /etc/nginx/ssl/dhparam.pem;
        ssl_session_cache shared:SSL:20m;
        ssl_session_timeout 180m;
        resolver 8.8.8.8 8.8.4.4;
        add_header Strict-Transport-Security "max-age=31536000;
        #includeSubDomains" always;
location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.0-fpm.sock;
        fastcgi_param PHP_VALUE open_basedir="/home/www/:/var/lib/php/sessions";
}
location ~ /\.ht {
        deny all;
        }


}
server {
        listen         80;
        listen    [::]:80;
        server_name    biebelfoodies.global;
        return         301 https://$server_name$request_uri;

   # Redirect non-https traffic to https
     if ($scheme != "https") {
         return 301 https://$host$request_uri;
     } # managed by Certbot


        # Redirect non-https traffic to https
    # if ($scheme != "https") {
    #     return 301 https://$host$request_uri;
    # } # managed by Certbot

}


```

When checking the certificate on the digicert website, it gives me everything ok.

[HTML]DNS resolves biebelfoodies.global to 188.165.237.17HTTP Server Header: nginx/1.10.3 (Ubuntu)
SSL certificateCommon Name = biebelfoodies.global
Subject Alternative Names = biebelfoodies.global
Issuer = Let's Encrypt Authority X3
Serial Number = 04DD19AA8E82790E499D83938577588EA033
SHA1 Thumbprint = 4DDBC6BCC50732DF0029F2D92B9856F1EE186892
Key Length = 2048
Signature algorithm = SHA256 + RSA (excellent)
Secure Renegotiation: Supported
 SSL Certificate has not been revokedOCSP Staple: Not EnabledOCSP Origin: GoodCRL Status: Not Enabled
SSL Certificate expirationThe certificate expires November 17, 2017 (90 days from today)
Certificate Name matches biebelfoodies.global Subjectbiebelfoodies.globalValid from 19/Aug/2017 to 17/Nov/2017 IssuerLet's Encrypt Authority X3  SubjectLet's Encrypt Authority X3Valid from 17/Mar/2016 to 17/Mar/2021 IssuerDST Root CA X3 SSL Certificate is correctly installed Congratulations! This certificate is correctly installed.
 

Heartbleed VulnerabilityThis server is not vulnerable to the Heartbleed Bug.
 Protocol SupportTLS 1.2, TLS 1.1, TLS 1.0

[/HTML]

Because it seems that there is no issue with the certificate in itself, I think there is a problem with the way nginx sends the redirect.
I have tried to check it with the dev tools from firefox, but that did not really gave me anything that I could use to pinpoint the issue with my limited knowledge on this subject.

[IMG]https://i.imgur.com/KtI8aoL.png[/IMG]

Can someone with more knowledge assist me with this issue?

Thank you

---

