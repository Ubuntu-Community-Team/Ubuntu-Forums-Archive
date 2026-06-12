---
title: "SSH Keys"
date: 2009-02-10
forum: Security
---

### Post by vorgusa on 2009-02-10
I am sure I am thinking to much about this, but can one SSH Key be used for multiple computers to connect to one server.  I am using software that only allows one SSH Key for connecting without a password.

---

### Post by bodhi.zazen on 2009-02-10
yes.

When you generate a key you have 2 files, one public and one private.

You put the key.pub on on the server and keep the private key

You can use the private key on any client or as many as you like, you can import it to windows and use it on putty.

If you need to learn how to make and use keys, use google, you will find several tutorials.

I have a very *brief* tutorial here :

[http://bodhizazen.net/beginners/SSH.txt](http://bodhizazen.net/beginners/SSH.txt)

---

