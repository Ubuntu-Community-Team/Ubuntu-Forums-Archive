---
title: "Certificate Issurer not Recognised"
date: 2010-07-27
forum: Security
---

### Post by velinion on 2010-07-27
Installed Ubuntu on my girlfriends computer, but am having an odd problem. On some websites, I get the following error when setting up a secure (https) connection in Firefox. (Have not tested in other browsers.)
> 
The certificate is not trusted because the issuer certificate is unknown.


If I go to Add Exception, then View Certificate, the top of the certificate window displays the following error in bold.
> 
Could not verify this certificate for unknown reasons


The certificate I pulled this off was for a bank, and issued by Verisign, within a valid date range, and works on this computer under windows (duel boot), and other computers (tryed on mine in both Win and Linux with no errors.)

So far, I have tried 
```

sudo apt-get install --reinstall ca-certificates
sudo apt-get install --reinstall firefox

```
without any improvements.

Any ideas?

EDIT: Sorry, realize I posted this in the wrong section of the forum: that's what I get for posting at 1AM I guess. Could a passing mod please move it to an appropriate location? Thanks!

---

### Post by cdenley on 2010-07-27
Are you sure the entire certificate is exactly the same as the one which is used by the other systems which don't complain about it?

---

### Post by www2 on 2010-08-15
I heft the same problem with Verisign certificates

---

