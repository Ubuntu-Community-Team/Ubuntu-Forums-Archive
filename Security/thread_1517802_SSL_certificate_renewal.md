---
title: "SSL certificate renewal"
date: 2010-06-25
forum: Security
---

### Post by Trismegister on 2010-06-25
I have been sent a new SSL certificate by the CA who issued the original last year.
I am confused as to what to do to maintain my apache2 https site on Ubuntu 10.4

a) it's a .cert filewhereas I installed a .pem file last year
b) will it automatically relate to the private key I set up last year or do i need a new private key?
c) what do I do with the .cert file to generate a new .pem file?

---

### Post by Ryan Dwyer on 2010-06-25
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

Scroll down to the part titled "Installing the certificate".

---

### Post by Trismegister on 2010-06-26
Many thanks for replying Ryan. Again I really appreciate the help I get from this forum and the Ubuntu help documentation.

Of course I had already read the referenced page before asking the question on the forum.
But it still doesn't answer my original three questions above ... I am reluctant to proceed without not knowing what i am doing. It's a production system.
The article describes installing a self-signed certificate rather than one that was issued a year later by the CA ... and may have lost the relationship with the original private key.

OK, then let me ask 2 other questions ... 1) is there some way of validating (before running a transaction through the production system...  that requires PayPal interactions and potentially diagnostics that worry users) that the (old) private key and the newly-issued .crt file are properly matched and 2) that the password won't be required by httpd

---

### Post by Ryan Dwyer on 2010-06-26
I found this on Wikipedia about .pem files: [http://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions](http://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions)

Looks like a .pem file is just a base64 encoded .cer file.

If you want to test the certificate I suppose you could set up a test machine, make it listen on the correct hostname, install the certificate then change your client's hosts file so your domain resolves to the test server instead of the production server. If the certificate is correct and the hostname matches correctly the client's browser shouldn't give any warnings.

And as always with production server config, make a backup of your previous configuration. Update the config, test, and if it fails you can revert immediately.

---

