---
title: "exim4 no longer does PAM based auth / howto tls with auth PAM?"
date: 2009-06-19
forum: Server Platforms
---

### Post by hanasaki on 2009-06-19
2009-06-20 

I have out of the box exim4 heavy daemon running and had it configured to do PAM auth against all connections and require TLS for non-local domains (ex: outside the company and using thunderbird over tls to auth before sending mail on port 25 TLS)

seems that running PAM requires exim to run as root and running as root is a bad idea.   Exim even notes "fixed_never_users" if the exim user is set to root.

So... how does one get exim4 to:
1. run over TLS 
2. require auth for all connections
3. auth against PAM
4. allow relay of mail from authenticated connections only

Thanks!

---

