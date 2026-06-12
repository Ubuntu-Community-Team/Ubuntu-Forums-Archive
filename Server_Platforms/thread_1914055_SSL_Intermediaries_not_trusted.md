---
title: "SSL Intermediaries not trusted?"
date: 2012-01-23
forum: Server Platforms
---

### Post by sandyd on 2012-01-23
I just setup ssl with Comodo PossitiveSSL.
The validation is fine on IE/Chrome, but fails on Firefox.

This means that I have to install the intermediaries as well, so I grabbed the bundle from [http://www.positivessl.com/ssl-certificate-support/cert_installation/ssl-certificate-index.html](http://www.positivessl.com/ssl-certificate-support/cert_installation/ssl-certificate-index.html)

Since im using nginx, most guides just tell you to concatanate the crt and the CA Bundle together. Ive done that. Its still giving out the "unverified" error, and as you can see below, the chains aren't manifesting themselves properly.

---

### Post by hawkmage on 2012-01-24
I have not dug into how Chrome deals with certificates but IE and Safari  do deal with certificate validation in a different manor than FireFox.   FireFox has issues with dealing with multiple CA certificates with the same CN which looks like what we are dealing with here.

Looking at the CA cert in the bundle from the site you listed the and the CA certificate in my Firefox trust store they are different.  

For the certificate with the CN "AddTrust External CA Root" the SKI (Subject Key Identifier) on the certificate in the bundle doesn't match the SKI on the certificate in FireFox.  Also the certificate in FireFox is a Root certificate while the one in the bundle from the site is signed by a Root certificate with the CN of "UTN-USERFirst-Hardware"

So the certificate with the CN "AddTrust External CA Root" in FireFox will not validate the certificate root certifiate on your certificate chain.  You may want to add the certificate with the CN of "UTN-USERFirst-Hardware" to the end of your certificate bundle file.  This may help but since "UTN-USERFirst-Hardware" is probally not in the FireFox trust store it will likely fail.

---

