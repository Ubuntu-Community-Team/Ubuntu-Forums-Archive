---
title: "Enable seufing on my own secured sites"
date: 2016-06-06
forum: Ubuntu Phone and Tablet
---

### Post by spam9 on 2016-06-06
Hi, 

I have an Aquarius tablet and was very excited when it arrived. Sadly I am unable to even login to one of the most important sites in the world, my own installation of FreshRSS. I am using a secure set up  with an own CA to sign the server certificate that is not accepted by the tablet-mode browser.

When I visit the site it fails to login. exactly the same way Chrome failed when it decided the encryption key was to weak. 


I would probably like to install my CA certificate or public key so that the browser accepts. I have tried to add each possible certificate or key I have available for the CA one at a time with no success. I add the certificate in /etc/ca-certificates.cfg and run update-ca-certificates. (I do not have the tabled hooked up right now so bear with me for spelling errors in the description). The browser does not accept my certificate as to be signed by an recognized CA. 

Any hints someone?


Sadly this works well in Firefox but then Firefox does not work very well in tablet-mode and a tablet with a mouse is the worst combination for lap-surfing :(

---

