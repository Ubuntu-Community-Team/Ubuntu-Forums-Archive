---
title: "verify pgp signature online?"
date: 2007-02-11
forum: Server Platforms
---

### Post by towsonu2003 on 2007-02-11
is there an online tool that can verify pgp / gpg signatures. I am looking for something for the following use case:

1. Receive a gpg signed email on a Windows computer where you cannot install any software, has no gpg installation

2. Go to this website

3. Input signed text:
```

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

this is a test
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

iD8DBQFFz3WfLM1JzWwJYEYRAnPpAJ40JVdlaLCjURYwY4tZq4vN+VKzYACbBEpz
buNaNgYrskAB5lwEopRD6M8=
=sq3j
-----END PGP SIGNATURE-----

```

4. Click on submit

5. Website provides:
```

gpg: Signature made Sun 11 Feb 2007 02:59:27 PM EST using DSA key ID 6C096046
gpg: Good signature from "towsonu2003 <...>"

```

---

### Post by jtc on 2007-02-11
Instead of answering your question I'll ask you something in return. I hope you don't mind too much.

For what purposes do you want to check signatures and what trust can you put into such a service ran by total strangers? True, the chances are pretty good they are honest, but on the other hand, chances are pretty good that you can trust an email without its signature as well.

What I guess you could do is build your own web-based signature checker. When it comes to PGP/inline-messages (as in your example) it should be a piece of cake. PGP/MIME might be slightly trickier.

---

### Post by tribaal on 2007-02-11
Seconded.

I know it's a mess to use gpg, but that's the only method you can rely on.

- trib'

---

