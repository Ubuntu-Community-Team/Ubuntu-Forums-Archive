---
title: "Heartbleed and gpg"
date: 2014-04-15
forum: Security
---

### Post by jsvidyad on 2014-04-15
Hello,
    
    I read news articles on the web about the heartbleed openSSL vulnerability affecting SSL. I read that this could have compromised SSL certificates and signatures. Does that mean that gpg signatures and keys could have been compromised? Do the gpg signatures and keys need to be revoked? Will websites such as the ubuntu iso download sites and the ubuntu repositories be using new gpg keys to sign and validate the iso images and packages held on those sites?

---

### Post by slickymaster on 2014-04-15
Please refer to this thread [How the Heartbleed bug affects users]("http://ubuntuforums.org/showthread.php?t=2216096&highlight=heartbleed"), here in the forum.

---

### Post by jsvidyad on 2014-04-17
> **slickymaster said:**
> Please refer to this thread [How the Heartbleed bug affects users]("http://ubuntuforums.org/showthread.php?t=2216096&highlight=heartbleed"), here in the forum.

Hello,

    I read that stuff. But, it doesn't say anything about gpg. Does that mean that the heartbleed vulnerability does not affect gpg? I mean, is the cryptography used in gpg invulnerable to the heartbleed vulnerability?

---

### Post by SeijiSensei on 2014-04-17
The Heartbleed bug only affects SSL connections, and only connections with servers running OpenSSL.  It was a flaw in the "heartbeat" code added to OpenSSL in March of 2012.  It has nothing to do with GPG or the signed binaries in the repositories.  

I suggest you read heartbleed.com to see exactly what was involved.  Basically you could exploit the bug to get the server to ship you 64K chunks of its memory.

---

