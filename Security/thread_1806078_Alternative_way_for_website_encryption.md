---
title: "Alternative way for website encryption?"
date: 2011-07-17
forum: Security
---

### Post by TimeDistort12 on 2011-07-17
I don't care for domain 'authentication' by an "Authority". I don't trust no one, so CA's to me are as trustworthy as the gypsy in the park.

I can use a self-signed certificate, but the problem is most browsers makers are Fn idiots that say the connection is not secure, when it actually it, but because I did not folk out cash, it makes my website look bad.
I can understand the need for a 3rd party to verify the domain host to prevent man in the middle attacks, but I do not care for this.. and browser makers should take more responsibility and introduce different padlocks for types of authentication, rather than saying "this connection is encrypted, but not secure because its self-signed". What a load of horse s***!

How many times does people stop to read certificate authoraties? I sure don't. I only care weather or not the connection has been encrypted.. so, I am looking for a way for simply providing encryption for my website.

From what I understand, when you submit a CSR to a CA, it includes the private key, meaning that the CA would be able to see the encrypt data, should they get hold of it. This is not acceptable for me.

Is there anything other way to use encryption other than the SSL model that is used typically amongst HTTPS browsers today?

All inputs are welcome, so long as you don't criticize my ideology, because I could not care for your opinion in regards to that.

Thank you!

---

### Post by Lars Noodén on 2011-07-17
You can get a free of charge certificate issued to you via [CA Cert, Inc.](http://www.cacert.org/).  That will help some.

---

### Post by TimeDistort12 on 2011-07-17
Thanks,

I looked into it. Their websites certificate which was issued by themselves was not recognized as a trusted CA by my browsers Opera.

---

### Post by TimeDistort12 on 2011-07-17
Please close and delete this thread. I will be creating a new one, written much more professionally.

[http://ubuntuforums.org/showthread.php?t=1806136](http://ubuntuforums.org/showthread.php?t=1806136)

---

