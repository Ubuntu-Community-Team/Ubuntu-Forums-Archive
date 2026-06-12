---
title: "Live CD + SSH = Insecure?"
date: 2009-02-14
forum: Security
---

### Post by Vincoor on 2009-02-14
Since a major vulnerability of SSH is the initial connection (before the encryption begins you're vulnerable to a "man-in-the-middle" interception), wouldn't it be unwise to us a live CD for SSH connections? Every time you connected it would be like the first time. Talking client side of course.

If you were to sit down in a Starbucks and connect to some SSH proxy every day for a year, you'd be giving a potential MITM 365 great opportunities to impersonate the server.

---

### Post by HermanAB on 2009-02-14
Even with a live CD you can still save data on a memory stick or HDD.

Cheers,

H.

---

### Post by dfreer on 2009-02-15
EDIT: Whooops, totally misread your original post. Anyways, yeah, if you save the server's public key along with your personal private key on some type of removable media (which you would need to do anyways if you want to be able to connect to the server each time), you will be able to confirm it is indeed the original server you are talking to.

---

