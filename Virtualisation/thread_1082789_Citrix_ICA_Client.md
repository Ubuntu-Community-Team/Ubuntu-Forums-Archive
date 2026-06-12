---
title: "Citrix ICA Client"
date: 2009-02-28
forum: Virtualisation
---

### Post by Blutrille on 2009-02-28
I have installed and am running the Citrix ICA Client for Linux successfully as far as the install. I run into a kink when trying to use security certs. 

I have exported the security cert from firefox and renamed it with .crt as instructed and placed it in the cacerts folder. I now get this error when trying to connect:

The security certifiicate "*.cetrom.net" could not be validated. (SSL provider code: 20, error 86)

The cert is valid and once by means unknown to me I was able to get the web interface to work although this did not seem to change my issues in the client itself. Since then I have been unable to duplicate the web interface working.

---

### Post by niekko on 2009-03-02
Just a guess, but should you put the CA certificate (that has been used to sign this current certificate) to the cacerts folder, too?

---

