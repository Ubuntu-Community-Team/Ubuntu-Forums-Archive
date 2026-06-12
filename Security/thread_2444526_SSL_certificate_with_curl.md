---
title: "SSL certificate with curl"
date: 2020-05-31
forum: Security
---

### Post by Sharkadder on 2020-05-31
Hi there,

I have a server which is running Ubuntu 14.04.

So i have recently updated an SSL certificate on the server and ever since i have done this, cURL doesn't seem to like it.  I have put the SSL certificate on and all websites do recognise the updated SSL and so i know that the SSL certificate is working fine.

When i run some cURL commands via a cron job they output the following:

```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: (60) SSL certificate problem: certificate has expired More details here: http://curl.haxx.se/docs/sslcerts.html

curl performs SSL certificate verification by default, using a "bundle"
 of Certificate Authority (CA) public keys (CA certs). If the default  bundle file isn't adequate, you can specify an alternate file  using the --cacert option.
If this HTTPS server uses a certificate signed by a CA represented in  the bundle, the certificate verification probably failed due to a  problem with the certificate (it might be expired, or the name might  not match the domain name in the URL).
If you'd like to turn off curl's verification of the certificate, use  the -k (or --insecure) option.
```


So i have tried a few things here.  

[LIST=1]
[*]Firstly i have tried downloading the new cacert.pem file from curl.haxx.se and updating the one in my /etc/ssl/certs folder and that didn't seem to work
[*]Secondly i replaced my certificate files in /usr/local/share/ca-certificates with the ones given by the SSL CA and that didn't work
[*]Then i tried updating cURL to the latest version and ran update-ca-certificates and that updated some certificates but still brings up the error
[*]I have also tried configuring the curl.cainfo and openssl.cafile variables from within php.ini to point to the /etc/ssl/certs/cacert.pem file and that didn't appear to do anything
[*]I then tried applying available updates to my Ubuntu and updated the certificates again using update-ca-certificates with the -f parameter and although it downloaded many certificates, the error remained
[/LIST]


Does anybody have any idea what else i can try to get out of this mess?  The only way i can get the scripts to run via cURL on a cron job at the moment is to use the -k option on cURL, but i appreciate that this is insecure and doesn't solve the problem long term.

p.s. if this is in the wrong section then could somebody kindly move it

Many thanks,

Mark

---

### Post by CharlesA on 2020-05-31
Hi,

Just a heads up, but 14.04 went end of life last year: [https://www.omgubuntu.co.uk/2019/04/ubuntu-14-04-end-of-life](https://www.omgubuntu.co.uk/2019/04/ubuntu-14-04-end-of-life)

It looks like /usr/local/share/ssl is for root certificates, not the certificate for your server.

How did you create the certificate? Have you verified the certificate chain is correct? You can use a site like [SSL Labs]("https://www.ssllabs.com/ssltest/") to verify that.

---

### Post by Sharkadder on 2020-06-01
Hi there and thank you for your response.  So the certificates were given to me by the CA and i put them onto the server.  I linked them using the SSL options within Apache using the previous private key, certificate authorities bundle and the new certificate.

As i say, the site shows that the SSL certificate is valid and i am just wondering what is wrong.  When i have gone to ssl labs it has said the following for the certificate chain:

Additional Certificates (if supplied)
Certificates provided	1 (1760 bytes)
Chain issues	Incomplete

I didn't want to paste some of the keys but the second point under trusted path one says this: "Extra Download" and then "Sectigo RSA Organization Validation Secure Server CA".  do i need to contact Sectigo for an additional download?  I know that they used to be Commodo and changed over last year.  Would that be causing it do you think?  Last year i just replaced the certificate and left the private key and authorities file alone.

---

### Post by Sharkadder on 2020-06-02
Just a bit of an update on this.  So i have gone into Webmin which is my admin control panel that i use on the server and have added in the following: 

Certificate Authorities file: SectigoRSAOrganizationValidationSecureServerCA.crt
I have put this in replace of the previous one i had: organizationvalidation-sha-2-intermediates.ca-bundle on all subdomains too.  I then restarted apache2

Now when i go on ssllabs i am not getting any chain issues.  However when i have taken the -k off the cURL scripts to run via cron job, i am still getting the same error shown below:
```
curl: (60) SSL certificate problem: certificate has expired
More details here: http://curl.haxx.se/docs/sslcerts.html
```

EDIT
Ok i have solved this problem now.  I followed the instructions from somebody to do the following:
export every certificate in the chain (in your case, you should get 3 files: mywebsite.crt, SectigoRSAOrganizationValidationSecureServerCA.crt, USERTrustRSAAAACA.crt)

To do so i ran the following cat command in the directory where the certificates are stored:
cat -- mywebsite.crt SectigoRSAOrganizationValidationSecureServerCA.crt USERTrustRSAAAACA.crt > mywebsite_cert.crt

I visited ssl shooper to clarify
[https://www.sslshopper.com/ssl-checker.html](https://www.sslshopper.com/ssl-checker.html)

I now have two chain certs (USERTrust and AAACertificate Services).  When i ran the cURL script again, all was working.

I would have never thought to have checked any of this and so thank you for pointing me into the right direction.

Many thanks,

Mark

---

### Post by CharlesA on 2020-06-02
That's great news. Glad you were able to get it fixed by adding the missing certificate.

---

