---
title: "Firefox: System76 untrusted connection"
date: 2011-11-04
forum: System76 Support
---

### Post by ubuntu27 on 2011-11-04
I always visit System76 frequently to fantasize what will be my next purchase.

Today, upon visiting system76, I found that Firefox considers System 76 to be untrustworthy because of invalid security certificate:

This is what shows in Firefox: 


> This Connection is Untrusted
            
        
          You have asked Firefox to connect
securely to [www.system76.com](www.system76.com), but we can't confirm that your connection is secure.
          Normally, when you try to connect securely,
sites will present trusted identification to prove that you are
going to the right place. However, this site's identity can't be verified.
        
        
        
          What Should I Do?
          
            If you usually connect to
this site without problems, this error could mean that someone is
trying to impersonate the site, and you shouldn't continue.

Technical Details
          [www.system76.com](www.system76.com) uses an invalid security certificate.

The certificate is not trusted because it is self-signed.
The certificate is only valid for exodus76

(Error code: sec_error_untrusted_issuer)

So, this is just a heads-up. :)

---

### Post by lovinglinux on 2011-11-04
Which version of Firefox are you using?

---

### Post by ubuntu27 on 2011-11-04
Firefox 7.0.1. 

Looks like System 76 staff fixed the issue. It is working today. :popcorn: yay!

---

### Post by isantop on 2011-11-04
You'll want to make sure that you aren't using a plugin that forces HTTPS connections. The public areas of our site aren't set up for SSL, and while we do use it exclusively on any pages containing sensitive customer information, other areas (like the system specs pages) don't. Forcing https on these pages will throw an error.

---

