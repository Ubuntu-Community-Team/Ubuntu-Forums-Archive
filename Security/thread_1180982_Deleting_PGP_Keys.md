---
title: "Deleting PGP Keys"
date: 2009-06-07
forum: Security
---

### Post by etdsbastar on 2009-06-07
Hello Friends,

I am using Jaunty. I had created some PGP keys using "Encryption and Keyrings" from the Applications Menu and published them on the keyserver of ubuntu.

But, after some days I created a new "Encryption and Signing" key. But, I want to delete those old keys present on the keyserver.

Is there any way to delete those keys present on the keyserver unnecessarily.

Please help.

---

### Post by tubbygweilo on 2009-06-07
etdsbastar, I believe that the keys are on the server for ever. You could revoke your keys by applying the key revocation certificate created when you created the keys or create one now and apply it.

Additional information:
[How to revoke a key]("http://ubuntuforums.org/showthread.php?t=1140391&highlight=key+revocation")
[How Do I make a Key Revocation Certificate in Seahorse?]("http://ubuntuforums.org/showthread.php?t=1004289&highlight=key+revocation") 
[GPG and PGPG question]("http://ubuntuforums.org/showthread.php?t=709839&highlight=key+revocation") 
[The GNU Privacy Handbook]("http://www.gnupg.org/gph/en/manual.html#REVOCATION")

Hope this helps.

---

### Post by etdsbastar on 2009-06-07
Friend,

There's a problem, I deleted those keys from my "Passwords and Keyrings Applications", I am only having the new PGP key. 

One more thing, I can get the Key ID of the old PGP keys through the servers. 

How can I delete or revoke those keys, only through the Key ID

---

### Post by kevdog on 2009-06-07
Unless you saved the revocation certificate you can not delete the keys from the keyserver.

---

