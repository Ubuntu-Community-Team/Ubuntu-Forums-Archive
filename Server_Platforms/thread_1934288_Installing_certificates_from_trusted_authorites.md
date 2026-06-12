---
title: "Installing certificates from trusted authorites"
date: 2012-03-01
forum: Server Platforms
---

### Post by niranjan_rao on 2012-03-01
Platform : Ubutnu 11.10 desktop and server

If I tried to use wget "https://localization.att.com", wget was failing on both platforms error message "Unable to verify the issuers authority".

On desktop, I firest tried connecting the site using browser. Bowser did not complain. Still wget failed.

After some investigation I managed to solve the problem by running "sudo dpkg-reconfigure ca-certificates" on desktop, but its not fixing problem for server edition.


How do I install the certificates on server so that wget runs. I am not interested in serving ssl traffic, but my application connects to some valid ssl sites and it fails as system does not recognize the certificate. 

I don't want to use --no-check-certificate option as these sites do have valid certificates - at least browser thinks so.

Thanks for the pointers

---

### Post by hawkmage on 2012-03-01
Do you know if the SSL CA certs for the site in the CA certificate directory?

If you run the following command it will show you the OpenSSL directory being used:
```
openssl version -d
```Under that directory you will find a directory/symlink anmed certs where you would put the CA certs you want to add and run the command:
```
sudo c_rehash /etc/ssl/certs/
```

Took a look at the certificate being presented by that site and oddly enough only the host certificate is being presented.  Usually the host certificate and the CA chain are presented by a server.  This is partly why wget is failing.  The CA certificate store on the system doesn't have the VeriSign intermediary certificates so it can not validate the certificate.

---

### Post by niranjan_rao on 2012-03-02
Thank you, that did the trick. I copied mozilla certificates (there were around 14 missing in server edition that were in the desktop edition). I guess firefox might be installing those.

---

