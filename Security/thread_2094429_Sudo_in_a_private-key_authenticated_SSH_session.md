---
title: "Sudo in a private-key authenticated SSH session"
date: 2012-12-13
forum: Security
---

### Post by algernon83 on 2012-12-13
I've got SSH set up on my home server to allow private-key authentication only to log on. Can Sudo be configured to re-check the authentication key instead of prompting for a password? Or would there be no security benefit to this, and I should just disable passwords for Sudo?

---

### Post by CharlesA on 2012-12-13
I do not think it can be configured to prompt for your key again.

In any case, once someone is connected via private key, they would still need to know the user password in order to use sudo, so it's two layers of security.

---

### Post by JKyleOKC on 2012-12-13
Remember that all of the SSH traffic is encrypted, so when you type in your password for sudo, it does **not** go over the wire in plain text. Thus it's still fully secure.

---

