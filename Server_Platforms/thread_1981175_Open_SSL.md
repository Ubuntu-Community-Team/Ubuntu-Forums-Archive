---
title: "Open SSL"
date: 2012-05-16
forum: Server Platforms
---

### Post by maverickaddicted on 2012-05-16
Hi,

I created a server certificate using this

[http://www.tc.umn.edu/~brams006/selfsign.html](http://www.tc.umn.edu/~brams006/selfsign.html)

and modified the Apache accordingly.

However, I have one question whenever I open the URL using https, why does it shows the cross line on https and this message -

```
The identity of this website has not been verified.
 &#8226; Server's certificate is not trusted.

The identity of the server you are connected to cannot be fully validated. 
You are connected to a server using a name only valid within your network, which an external certificate authority has no way to validate ownership of. 
As some certificate authorities will issue certificates for these names regardless, there is no way to ensure you are connected to the intended website and not an attacker.
```

---

### Post by SeijiSensei on 2012-05-16
Did you accept the certificate in your browser?  Once you've done that you shouldn't see that message any more.

Public-key systems like SSL rely on a "chain of trust."  Having a certificate is only part of the process; the certificate itself must be signed by a Certificate Authority that your browser recognizes as legitimate.  Browsers come with a collection of CA certificates, e.g., from Network Solutions, so if a certificate is signed by a CA whose certificate you possess, you'll get connected without a complaint.  Self-signed certificates have no such independent validation so your browser will complain that the certificate cannot be validated.  The browser should give you the option of accepting the certificate anyway, after which you won't see any further complaints.

---

### Post by maverickaddicted on 2012-05-16
> **SeijiSensei said:**
> Did you accept the certificate in your browser?  Once you've done that you shouldn't see that message any more.

Public-key systems like SSL rely on a "chain of trust."  Having a certificate is only part of the process; the certificate itself must be signed by a Certificate Authority that your browser recognizes as legitimate.  Browsers come with a collection of CA certificates, e.g., from Network Solutions, so if a certificate is signed by a CA whose certificate you possess, you'll get connected without a complaint.  Self-signed certificates have no such independent validation so your browser will complain that the certificate cannot be validated.  The browser should give you the option of accepting the certificate anyway, after which you won't see any further complaints.

Yes, I accepted it and works fine in Firefox, but why it shows like this

```
You are connected to openserver which is run by unknown. and also - This website does not supply ownership information.
```

However, it does not show cross line on https in Firefox. The above things are happening in Firefox browser.


And the problem with cross line on https, which I mentioned in previous post is happening on Google Chrome. It does not show any option for accepting the certificate.

---

### Post by FatFrog on 2012-05-16
If you are using a self signed cert, you are likely to see the "The site's security certificate is not trusted!" error regardless of what you do. Chrome, FF and IE have this set as a security feature. I'm not sure of a work around, but I do know that importing the cert to your browser usually help mitigate the issue. though, I also have seen this not work.
You should still be able to click through and view the site though

---

### Post by SeijiSensei on 2012-05-16
Firefox won't complain about a self-signed certificate once you've accepted it.  I don't know about other browsers.  However it looks like from the error that you didn't actually fill in all the required fields when you generated the certificate.  Did you give it values for state/province, organization name, etc. when prompted?

---

### Post by kennethconn on 2012-05-16
For IE (no idea about other browsers), if you used your own CA you will need to run the Certificates snap-in in MMC (manage certificates for Computer) and import the CA cert to the Trusted Root Certification Authorities -> Certificates section.
 
This will prevent any error messages similar to what you are getting. I am presuming it is only a test environment and not a production server.

---

### Post by maverickaddicted on 2012-05-17
> **SeijiSensei said:**
> Firefox won't complain about a self-signed certificate once you've accepted it.  I don't know about other browsers.  However it looks like from the error that you didn't actually fill in all the required fields when you generated the certificate.  Did you give it values for state/province, organization name, etc. when prompted?

Yes, I did. I provided all the information.

---

### Post by SeijiSensei on 2012-05-17
Try Kenneth's approach then.  I've never created a CA and used that to sign my own cert.  I've just created the self-signed server certificate.  Maybe if you start by creating a CA, you need to put its certificate in your browser as he suggests.

---

### Post by kennethconn on 2012-05-17
A self-signed certificate would be the same procedure, the reason why I mentioned the CA cert was that some people use their own CA, import the server cert and cannot understand why they still have errors about untrusted / invalid certificates.

---

