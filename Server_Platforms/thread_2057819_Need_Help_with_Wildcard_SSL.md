---
title: "Need Help with Wildcard SSL"
date: 2012-09-14
forum: Server Platforms
---

### Post by mespork on 2012-09-14
Hello,

I am trying to use a wildcard ssl certificate on an ubuntu server. The wildcard is (unfortunetly) installed on a windows server. I exported the certificate as a PFX file and then used openssl to creat the pem (and later crt and key) files. However when after copying the crt and key file to the appropriate directories, I am getting this error when trying to view the site:

[I]Secure Connection Failed

You have received an invalid certificate.  Please contact the server administrator or email correspondent and give them the following information:

Your certificate contains the same serial number as another certificate issued by the certificate authority.  Please get a new certificate containing a unique serial number.

(Error code: sec_error_reused_issuer_and_serial)

  The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
  Please contact the website owners to inform them of this problem. Alternatively, use the command found in the help menu to report this broken site.

[/I]

Did I miss a steop to generate the correct crt and key combo?

---

### Post by jasonmoran on 2012-11-03
Hi, I thought this was an interesting question and actually have the same problem. I noticed no one answered this question so I've gone ahead and reposted to the ssl.com Q&A board at [http://answers.ssl.com/2908/need-help-with-wildcard-ssl](http://answers.ssl.com/2908/need-help-with-wildcard-ssl) :confused:

---

