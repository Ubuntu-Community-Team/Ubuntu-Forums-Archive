---
title: "Not being able to store X.509 certificates"
date: 2013-08-24
forum: Security
---

### Post by Seemant_Shankar on 2013-08-24
I have uBuntu Linux ver. 12 LTS installed in a server grade machine. I am trying to use VLC media player as a media sharing server software. I have to pick up a media file from a https:// address and stream it back to another player on the internet using http://

My problem is that I have installed the https:// certificate manually (Which are not well created, authorized by a CA and is also expired). Since I have added them manually they should not create a problem. When I run VLC it gives me a warning about the issues with the certificate but asks me whether I want to accept the certificate for 24 hours or permanently. Since I trust the site, I instruct VLC to accept the certificate permanently but is not being able to do so and asks me this question every time I connect to the https:// site. 

I was able to extract the logs and here is what I got...

gnutls error: cannot load trusted Certificate Authorities: An unimplemented or disabled feature has been requested.
gnutls error: Certificate verification failure (0x0042)
gnutls error: * Certificate not verified
gnutls error: * Signer not found
gnutls error: cannot store X.509 certificate: An unimplemented or disabled feature has been requested.
gnutls error: Certificate does not match "10.0.161.77"
gnutls error: cannot store X.509 certificate: An unimplemented or disabled feature has been requested.

if you notice it is not able to store the X.509 certificate in its trusted store which is why it keeps asking me to accept the certificate every time. I have also executed the command sudo apt-get install gnutls-bin to check if it is the latest version and the kernel states that the gnuTLS that I have already installed is up to date and the latest version. I have also tried reinstalling VLC from their nightly builds but it did not change the situation for me. 

Can you please help me in understanding that could be wrong? VLC forums may not be able to help me too much as it does not seem to be a VLC problem but more of a gnuTLS problem. 

Am I at the right place to seek assistance regarding this issue? Thanks!

---

### Post by neel3 on 2014-03-05
probably related to this...
[http://arstechnica.com/security/2014/03/critical-crypto-bug-leaves-linux-hundreds-of-apps-open-to-eavesdropping/](http://arstechnica.com/security/2014/03/critical-crypto-bug-leaves-linux-hundreds-of-apps-open-to-eavesdropping/)

---

### Post by open2reason on 2014-03-05
Seemant_Shankar,
Using 12.04lts I had a security update for [https://launchpad.net/ubuntu/precise/amd64/libgnutls26](https://launchpad.net/ubuntu/precise/amd64/libgnutls26) [https://launchpad.net/ubuntu/precise/amd64/libgnutls26/2.12.14-5ubuntu3.7](https://launchpad.net/ubuntu/precise/amd64/libgnutls26/2.12.14-5ubuntu3.7) this morning which to my untutored eyes this may well relate to your problem.

---

