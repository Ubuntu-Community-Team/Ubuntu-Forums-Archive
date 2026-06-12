---
title: "OpenSSL certificates with 128 bit serial numbers"
date: 2015-06-18
forum: Security
---

### Post by Steve_Melcher on 2015-06-18
I am running an OpenSSL CA on 14.04.  The certificates are being created by default with an 8 bit serial number.  It appears as if this might be messing with Windows machines using the certificates (the subordinate online CA's).  Is there a spot in the .conf file, or an OpenSSL command switch that can tell it to create the certificate with a larger certificate?

I found a forum that says us -create_serial but that does not seem to make any difference.

---

