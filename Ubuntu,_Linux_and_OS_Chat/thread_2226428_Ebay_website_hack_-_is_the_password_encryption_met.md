---
title: "Ebay website hack - is the password encryption method similar for all websites?"
date: 2014-05-27
forum: Ubuntu, Linux and OS Chat
---

### Post by cwmoser on 2014-05-27
Regarding the recent Ebay website hack where Ebay suggests everyone change
their Ebay password and if you used the same password on other sites to change
those passwords too.  Passwords are stored in their encrypted form.  So are
passwords encrypted with the same algorithm for same type of server software?
Looks to me like every website ought to incorporate a little "salt" in the encryption
process.  Or is this just a Microsoft "feature" for the passwords to be encrypted the same?

Carl

---

### Post by 3rdalbum on 2014-05-28
If the attacker discovered the eBay salt, they could generate rainbow tables and compare hashed passwords with known starting cleartext. Thus, discovering passwords.

It doesn't matter what security procedures other sites use, once the cleartext password is known for a given e-mail address, that password can be tried on other websites. Manually, in a web browser, if necessary.

However I think it's likely eBay never salted the passwords. Remember, it's an old site, and old habits die hard.

---

