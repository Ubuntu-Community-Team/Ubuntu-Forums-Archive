---
title: "the best Control Panel for hosting..."
date: 2007-09-08
forum: Server Platforms
---

### Post by bss on 2007-09-08
What is the best control panel for multiple domain hosting?
I have tried ISPConfig and it has a bad thing ( no users with same username for multiple domains..). So I was wondering if any of you guys know of any other good control panel that works with ubuntu..

thx

Blaž

---

### Post by HermanAB on 2007-09-08
Virtualmin

---

### Post by bss on 2007-09-09
Does Virtualmin allow the usage of (Postfix's) Maildir insted of preconfigured mailbox...?

Regards

Blaž

---

### Post by HermanAB on 2007-09-09
Virtualmin is 1000% configurable.  You are only limited by your own abilities.

Cheers,

H.

---

### Post by bss on 2007-09-16
Does any of you know any good guides or howtoos/tutorials to configure postfix to recive mail with Maildir/.

thx in advance..

cya!

---

### Post by HermanAB on 2007-09-16
AFAIK you just add a '/' somewhere - search the postfix .org web site.  The answer is in there Sculley...

Cheers,

H.

---

### Post by bmathis on 2007-09-16
> **bss said:**
> Does any of you know any good guides or howtoos/tutorials to configure postfix to recive mail with Maildir/.

thx in advance..

cya!

try adding home_mailbox = Maildir/ to your main.cf file.

---

