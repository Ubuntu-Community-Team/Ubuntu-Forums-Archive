---
title: "SSL/TLS with thunderbird"
date: 2009-07-24
forum: Security
---

### Post by sefs on 2009-07-24
Hey there,

I have my email set up in Thunderbird like the attached image.

Look at the Secure settings section.  For all the time I was using this email address it has been like this.

Does this mean that when I connect to my providers pop3 email server that my password is sent in the clear for anyone to hijack?

I have wireshark and was looking to see, but I am not sure what to look for.  I see the smtp traffic and some emails of the src and dest, but not my password.

I just want to be certain that my password is not going out in clear text.

My provider does not seem to offer ssl/tls on their mail server.

Thanks for any help given.

---

### Post by XCan on 2009-07-24
Yes, it seems like you are sending your password in clear text. What's more rediculess is that many providers (including mine both at home and work) support SSL/TSL but not at authorization, which means passwords are sent in clear text and the data transmission is encrypted, how stupid can people get?

---

### Post by The Tronyx on 2009-07-24
Your provider should have an SSL/TLS only port that forces SSL/TLS authentication.

---

### Post by sefs on 2009-07-24
I'm told that they are older servers and don't have tls/ssl or anything such.  Just simple connection to standard ports.

---

### Post by Alias1407 on 2009-07-24
Just try putting in port 465 of 993 for SSL/TLS

---

### Post by sefs on 2009-07-24
Tried, but it times out.

---

