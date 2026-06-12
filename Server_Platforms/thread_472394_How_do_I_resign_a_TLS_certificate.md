---
title: "How do I resign a TLS certificate?"
date: 2007-06-13
forum: Server Platforms
---

### Post by ocdude on 2007-06-13
Well, I made the big move and am now hosting my own server. The apache stuff I have covered, but it's the e-mail server stuff that's annoying the hell out of me.

Anyway, my question is if there is a way to resign the TLS certificate. At the moment, it's signed as the host "localhost" (which I vaugely remember doing because it was not a live server when I first brought it online) and I need to have it signed as the domain name that I have set up for this server. Any help would be greatly appreciated.

---

### Post by MJN on 2007-06-13
You'll need a new certificate, with the new hostname listed on it, and then that'll get re-signed by your private key. Any attempt to modify the current hostname listed will of course break the hashed signature.
 
Basically, just start your certificate creation process again.
 
Mathew

---

