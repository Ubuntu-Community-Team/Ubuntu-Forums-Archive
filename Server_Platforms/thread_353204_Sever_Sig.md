---
title: "Sever Sig"
date: 2007-02-04
forum: Server Platforms
---

### Post by esaym on 2007-02-04
How do I edit the server sig?  I want to change it to a custom one.  I know it is possible but I can't find documentation ](*,)

---

### Post by jtc on 2007-02-04
What kind of server signature? The message you get while logging in through SSH? The version-information Apache displays in the bottom of fileindexes and error-messages?

---

### Post by esaym on 2007-02-04
> **jtc said:**
> What kind of server signature? The message you get while logging in through SSH? The version-information Apache displays in the bottom of fileindexes and error-messages?

Oh I forgot to add that. Yes the info displayed on error pages and indexes.

---

### Post by jtc on 2007-02-04
Will [Servertokens]("http://httpd.apache.org/docs/2.0/mod/core.html#servertokens") do the trick, or do you want to be more creative?

---

### Post by esaym on 2007-02-04
> **jtc said:**
> Will [Servertokens]("http://httpd.apache.org/docs/2.0/mod/core.html#servertokens") do the trick, or do you want to be more creative?


Hey thats it!  Thank you!

---

