---
title: "Firefox security risk pop-up issues"
date: 2009-12-03
forum: Security
---

### Post by whitehaint on 2009-12-03
I connect at school via their public network, and I get a warning that the certificate is not valid, I add an exception but it will not proceed if the box is checked to remember.  Is there a fix for this since I can't update firefox?

---

### Post by cdenley on 2009-12-03
> **whitehaint said:**
> I connect at school via their public network, and I get a warning that the certificate is not valid, I add an exception but it will not proceed if the box is checked to remember.  Is there a fix for this since I can't update firefox?

What do you mean "will not proceed"? You get a warning like that if the certificate is not signed by a trusted certificate authority, the common name does not match the domain you are using to access the page, or the certificate is expired. If the certificate should be signed by a CA and valid, then this message usually means the site you are attempting to access is being spoofed.

The ideal solution would be to replace the site's certificate with a valid one. If you don't administer the site, and you want to trust the certificate is valid, you should be able to permanently allow the exception. That exception would be stored in your firefox profile.

---

### Post by doas777 on 2009-12-03
this problem will not be fixed by an FF update so far as i am aware. I get the same warnings with the latest greatest firefox on windows7 as well.

we get this at work when running our external facing web apps internally, becuase the interface by which we hit the server is on our internal domain, not our external one (the one cited in the certificate) so we always get a domain mismatch error.

not sure why you can't tell it to confirm and remember the exception, but you may be able to set up one manually under Preferences->Advanced->Encryption->view Certificates->Servers-> Add Exception

---

### Post by cdenley on 2009-12-03
SSL certificate exceptions work properly for me.

firefox-3.5 (3.5.5+nobinonly-0ubuntu0.9.10.1)

It sounds like maybe your connection is being routed to a captive portal, which is basically spoofing the server you are attempting to access, so you should receive a warning, then perhaps the captive portal is redirecting you to the server you intended to originally connect to, which would perhaps conflict with the captive portal's certificate if you stored it as an exception for the domain. Either way, it sounds like a network/server issue, not a firefox issue.

---

### Post by whitehaint on 2009-12-03
> **cdenley said:**
> SSL certificate exceptions work properly for me.

firefox-3.5 (3.5.5+nobinonly-0ubuntu0.9.10.1)

It sounds like maybe your connection is being routed to a captive portal, which is basically spoofing the server you are attempting to access, so you should receive a warning, then perhaps the captive portal is redirecting you to the server you intended to originally connect to, which would perhaps conflict with the captive portal's certificate if you stored it as an exception for the domain. Either way, it sounds like a network/server issue, not a firefox issue.

Sounds about right as it will pop up once I try to connect to an outside server.  The issue is that I cannot permanently store this exception.  When I say cannot proceed, I mean that I check the box and click "confirm", and nothing happens.  Interestingly when I look at the certificate, it is valid until 2011 and the pop up box says it could not be validated for an unknown reason!

*UPDATE*

Alright, I see it is saying the certificate is not trusted because it hasn't been valified by a recognized authority.  The main issue still though is that it will not permanently store the exception.  I did try going into preferences and I get the same results.

---

### Post by cdenley on 2009-12-03
> **whitehaint said:**
> Sounds about right as it will pop up once I try to connect to an outside server.  The issue is that I cannot permanently store this exception.  When I say cannot proceed, I mean that I check the box and click "confirm", and nothing happens.  Interestingly when I look at the certificate, it is valid until 2011 and the pop up box says it could not be validated for an unknown reason!

*UPDATE*

Alright, I see it is saying the certificate is not trusted because it hasn't been valified by a recognized authority.  The main issue still though is that it will not permanently store the exception.  I did try going into preferences and I get the same results.

So when you select to permanently store the exception, it does not appear under "servers" in the certificate manager? Does the connection timeout, is an empty page returned, or does the browser not attempt to load the page? Perhaps the lack of response from the server has nothing to do with the SSL certificate or warning.

Does this happen when you attempt to connect to any encrypted site, or just a particular one. Does it happen after you visit an unencrypted site first?

---

### Post by doas777 on 2009-12-03
there are several classes of warnings that you cannot create a persistent exception for. I believe they included self signed certs, and unverifiable certs. 

[http://lwn.net/Articles/295810/](http://lwn.net/Articles/295810/)

---

### Post by cdenley on 2009-12-03
> **doas777 said:**
> there are several classes of warnings that you cannot create a persistent exception for. I believe they included self signed certs, and unverifiable certs. 


You can create exceptions for self-signed certificates. I've never encountered a certificate I couldn't create an exception for. I suppose firefox may refuse to accept a malformed or expired one. Do you have a reference for this? Your link doesn't mention such a scenario.

---

### Post by doas777 on 2009-12-03
gimme a minute. it made big news when FF3 came out.

ok, i can't find any verification that you cannot create permenent exceptions for certian kinds of errors. I stand corrected/
I did find several folks with simmilar issues, but no solutions.

---

### Post by whitehaint on 2009-12-03
> **cdenley said:**
> So when you select to permanently store the exception, it does not appear under "servers" in the certificate manager? Does the connection timeout, is an empty page returned, or does the browser not attempt to load the page? Perhaps the lack of response from the server has nothing to do with the SSL certificate or warning.

Does this happen when you attempt to connect to any encrypted site, or just a particular one. Does it happen after you visit an unencrypted site first?

It appears, but only stored temporarily.  The warning comes up when I try to connect to the web.  I check the permanent box and the button changes to active, but for some reason it will not accept my clicking.  I had this warning come up when I had Jaunty, but with Koala it is giving me this problem.
If I just select to add exception temporarily it will proceed as normal, but attempts to store permanently fail because the certificate is not in the trusted list from mozilla.  The certificate is signed by a recognized group, it just has an unknown name so this leads me to believe it's some bug with the window for permanently storing exceptions.

---

### Post by cdenley on 2009-12-03
I did some testing. If you access a site which requires an exception for the certificate, then the certificate (or server) changes for that domain, you will have to restart firefox before you can create an exception for the new certificate.

---

### Post by whitehaint on 2009-12-03
> **cdenley said:**
> I did some testing. If you access a site which requires an exception for the certificate, then the certificate (or server) changes for that domain, you will have to restart firefox before you can create an exception for the new certificate.


I may not have made it clear, but this is an issue with connecting through the schools network to the outside.  When I initially open Firefox it shoots me to a page served by the schools server that requires me to accept the terms of use for their network, but during the initial redirect it pops up with the unsafe site warning.

---

### Post by cdenley on 2009-12-03
> **whitehaint said:**
> I may not have made it clear, but this is an issue with connecting through the schools network to the outside.  When I initially open Firefox it shoots me to a page served by the schools server that requires me to accept the terms of use for their network, but during the initial redirect it pops up with the unsafe site warning.

Exactly. You go to [https://mysite.com](https://mysite.com). Their captive portal provides an SSL certificate with a common name that doesn't match. You make an exception. They redirect you to the real [https://mysite.com](https://mysite.com). The real server provides the real self-signed certificate which requires another exception. You won't be able to make a new exception for [https://mysite.com](https://mysite.com) until you restart firefox.

---

### Post by whitehaint on 2009-12-03
> **cdenley said:**
> Exactly. You go to [https://mysite.com](https://mysite.com). Their captive portal provides an SSL certificate with a common name that doesn't match. You make an exception. They redirect you to the real [https://mysite.com](https://mysite.com). You won't be able to make a new exception for [https://mysite.com](https://mysite.com) until you restart firefox.


I tried that with the same results, the button to permanently store the exception is active, but fails to accept the click.
I tried the manual override and get it returns with "No information available. Unable to obtain identification status for the given site."

---

