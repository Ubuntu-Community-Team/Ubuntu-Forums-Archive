---
title: "Develop custom cipher"
date: 2009-05-20
forum: Security
---

### Post by dstempfley on 2009-05-20
I want to venture into adding support for custom ciphers to my system.  For now it's just an exercise to work on the integration of the cipher into the system and make sure I can create devices that encode and decode properly.  

Without consideration to the practicality of including a custom, non-tested cipher how difficult is it to integrate the code so that it would be supported by dmcrypt?  Is there any reference that might help, or am i looking at pooring over code?

For arguments sake, let's say I want to develop a rot13 cipher and use dmcrypt to manage devices that are rot13 encoded. 

Any thoughts?

/Dion

---

### Post by HermanAB on 2009-05-20
Howdy,

All the ciphers are in the OpenSSL project.  Go to their web site and start reading.

---

### Post by dstempfley on 2009-05-21
That's what I needed thanks.

/Dion

---

