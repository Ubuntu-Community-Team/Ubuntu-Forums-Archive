---
title: "SSL problem"
date: 2007-05-09
forum: Server Platforms
---

### Post by gtorino on 2007-05-09
I'm moving a secure server (SSL) from an Apache2 server running Fedora 4 to a revamped Apache2 server running Ubuntu 6.06 LTS and I'm having a problem with the "intermediate certificate".

We use a Verisign certificate to reassure visitors to our secure site. In ssl.conf on Ubuntu the settings are correct for SSLCertificateFile, SSLCertificateKeyFile and SSLCACertificateFile, but that last setting, with SSLCACertificateFile pointing to Verisign's intermediate certificate, returns an error at Apache2 startup:

Unable to configure verify locations for client authentication
[[error] SSL Library Error: 33558541 error:0200100D:system library:fopen:Permission denied
error] SSL Library Error: 537317378 error:2006D002:BIO routines:BIO_new_file:system lib
[error] SSL Library Error: 185090050 error:0B084002: x509 certificate routines:X509_load_cert_crl_file:system lib

This happens even though ssl.conf is not requiring client authentication, with those lines commented out:
#SSLVerifyClient require
#SSLVerifyDepth  10

Apparently there's something else calling for client authentication on Ubuntu. These settings have worked fine for years on Fedora 4 but fail on Ubuntu. Has anyone seen this before and know how to fix it? Moving the intermediate certificate to the SSLCertificateChainFile directive also doesn't work, Apache startup still fails.

It's driving me nuts! Any help appreciated.

---

