---
title: "Ubuntu Security Notices and PGP signing"
date: 2006-10-12
forum: The Cafe
---

### Post by nocturn on 2006-10-12
I received an USN yesterday that did not come from Martin as most do.

It came from Kees Cook and it was PGP signed (which is commendable).

Yet, I did not have his key in my keyring, so I fetched it from a keyserver (no big deal here).  But after that, there came the trust issue.

It was not signed with any trusted signature (not even Martin's).  I checked out the signatures, and there seems no central canonical signature in it.

So I think it would be good to have a key-signing key that signs the keys for the people that send out USN's so we know they really do belong to canonical/Ubuntu (not that I have doubts in this case, but it should be obvious).

What do you guys think about this?

---

### Post by nocturn on 2006-10-13
bump, no opinions on this?

---

### Post by John.Michael.Kane on 2006-10-13
Sound fair,and right to me.

One question who would be in charge of the key-signing key. I don't think you would just anyone having that kind of power. not that there should be any trust issues,however.you never know.

Just my thoughts

---

### Post by nocturn on 2006-10-13
> **SD-Plissken said:**
> Sound fair,and right to me.

One question who would be in charge of the key-signing key. I don't think you would just anyone having that kind of power. not that there should be any trust issues,however.you never know.

Just my thoughts

It should be someone inside Ubuntu/Canonical and a special key-signing-key should be used.

Secondly, the security key should be signed by the others (Martin etc) to give it a trace.

These kinds of things are quite difficult, but without the web of trust, a PGP signing key is useless.  This is currently the case for the key used on that USN, I cannot verify any path back to canonical/Ubuntu.

---

