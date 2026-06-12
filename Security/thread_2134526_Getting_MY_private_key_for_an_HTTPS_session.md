---
title: "Getting MY private key for an HTTPS session?"
date: 2013-04-11
forum: Security
---

### Post by azzamite on 2013-04-11
Hello there

I wish to get the private key used by my browsed (Opera or FireFox) during an HTTPS communication.

I know I cannot get the server's private key, but I wish to get at least my own private key and decrypt with it what my browser displays in the screen.

Any idea on how to get it?

---

### Post by CharlesA on 2013-04-11
As far as I know the client doesn't have a "private key" it uses, but it checks the server's public key against the list of CA's who issue certificates.

This might be worth reading:
[http://pic.dhe.ibm.com/infocenter/tivihelp/v2r1/index.jsp?topic=%2Fcom.ibm.itame2.doc_5.1%2Fss7aumst18.htm](http://pic.dhe.ibm.com/infocenter/tivihelp/v2r1/index.jsp?topic=%2Fcom.ibm.itame2.doc_5.1%2Fss7aumst18.htm)

---

### Post by azzamite on 2013-04-12
That will make things harder :(

Thanks for the link, it's very interesting.

---

