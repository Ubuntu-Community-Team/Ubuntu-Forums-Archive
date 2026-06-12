---
title: "problems with my SSL cert need help fixing it."
date: 2008-12-20
forum: Server Platforms
---

### Post by kustomjs on 2008-12-20
Alright Guys,
I was able to get my ssl to work last night on my server but when I go to firefox I get this:
"Secure Connection Failed

secure.jbodyconnection.com uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for server1
The certificate expired on 10/17/2008 1:45 AM.

(Error code: sec_error_expired_issuer_certificate)
    * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.

    * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.
          Or you can add an exception…"

I want to know how I can fix this and not get that warning/error message.

---

### Post by RealPSL on 2008-12-21
The browser is rejecting your certificate for SSL because it is not signed by a certificate authority like Verisign etc. The certificate is also expired. The browser rejects these for security reasons the same way you check the expiration date on the milk before drinking it.

If you are just using this for testing you can continue using the expired self signed certificate. However if you are going to have other people use the site you will need a real certificate. A link with instructions for this is below:

[https://help.ubuntu.com/8.10/serverguide/C/certificates-and-security.html]("https://help.ubuntu.com/8.10/serverguide/C/certificates-and-security.html")

---

