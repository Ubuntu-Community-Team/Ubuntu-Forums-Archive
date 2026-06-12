---
title: "Should I change permission of pubring.kbx to use with Git?"
date: 2019-11-26
forum: Security
---

### Post by kingle01 on 2019-11-26
When I attempt to create a new gpg key with **gpg --full-gen-key**, I keep receiving this error:
```

[SIZE=2]gpg: no writable public keyring found: Not found
Key generation failed: Not found[/SIZE]

```
So I added **sudo** in front of the command and was able to create the key. Then I added the key to Github and set the signing key to Git.  However, when I tested the key with a new commit, it gave me this error:
```

[SIZE=2]error: gpg failed to sign the data
fatal: failed to write commit object[/SIZE]

```
I check the permission of **pubring.kbx** and it was root. I'm not sure whether I should change its permission so I created a **pubring.gpg** file and created a key there instead. My commits are now verified but I want to know if it's better to change permission of **pubring.kbx** instead of having two keyrings?

---

