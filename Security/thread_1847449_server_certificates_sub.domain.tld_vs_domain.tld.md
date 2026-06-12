---
title: "server certificates sub.domain.tld vs domain.tld"
date: 2011-09-20
forum: Security
---

### Post by trorion on 2011-09-20
I'm playing around with a web server on an old box and wanted to set up secure pages.  I created a self-signed certificate to *.domain.tld which is fine from [https://www.example.com](https://www.example.com) but show invalid from [https://example.com](https://example.com)

If I sign with domain.tld then I get an error at [https://www.example.com](https://www.example.com)

Is there a way to correct this?  My understanding is that certificates for ssl are IP specific so I can't have one for domain.tld and one for *.domain.tld on the same IP address.

---

### Post by jerenept on 2011-09-21
> **trorion said:**
> I'm playing around with a web server on an old box and wanted to set up secure pages.  I created a self-signed certificate to *.domain.tld which is fine from [https://www.example.com](https://www.example.com) but show invalid from [https://example.com](https://example.com)

If I sign with domain.tld then I get an error at [https://www.example.com](https://www.example.com)

Is there a way to correct this?  My understanding is that certificates for ssl are IP specific so I can't have one for domain.tld and one for *.domain.tld on the same IP address.

The problem is that the certificate is self-signed. For security reasons, no browser accepts self-signed certs without complaining, and Chrome doesn't allow them at all.

---

### Post by trorion on 2011-09-21
true.
But that's not the problem I'm looking at.  In this case I accepted the self signed certificate and (admittedly it's just IE behavior) the browser shows acceptable certificate for [https://www.domain.tld](https://www.domain.tld) and a red banner with danger! for [https://domain.tld](https://domain.tld)

I'm considering just re-building and then rerouting all requests to [www.domain.tld](www.domain.tld) but I'd like to find a more elegant solution.

---

