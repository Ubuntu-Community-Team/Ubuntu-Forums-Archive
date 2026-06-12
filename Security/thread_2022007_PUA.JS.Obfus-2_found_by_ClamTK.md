---
title: "PUA.JS.Obfus-2 found by ClamTK"
date: 2012-07-10
forum: Security
---

### Post by aligator12 on 2012-07-10
Hi guys, today I scanned my Ubuntu with ClamTK and it found "PUA.JS.Obfus-2" in a firfox profile I created yesterday (I only visited youtube and google in this profile).

Now I have had issues with ClamTK giving me false positives in the past so I am safe to assume this is another time? Because I am not going to delete it if it is.

---

### Post by aligator12 on 2012-07-10
Well I deleted the cache, cookies, history, etc in the profile and now clamtk says it is gone, am I safe to say this was a false pos?

---

### Post by aligator12 on 2012-07-10
Anyone?

---

### Post by Dave M on 2012-07-10
The "PUA" stands for Potentially Unwanted Application. In other words, it may or may not be malicious.  Some javascript is packed for various reasons, and this can trigger certain alerts.

Anyway, you're probably safe now since you've deleted it from your cache.

---

### Post by aligator12 on 2012-07-10
But do you think this was a false positive? As I said before the only sites I visited was google and youtube. And could any of my logins be compromised?

---

### Post by OpSecShellshock on 2012-07-11
It's highly unlikely that there was any compromise. Also, it's I suppose technically not a false positive in the sense that it actually was a packed and obfuscated script. However, it was not necessarily malicious. The clam engine just couldn't make a determination one way or the other due to the packing/obfuscation. In those cases the clam application is choosing to consider anything inconclusive to be at least suspicious and alerting on it.

---

