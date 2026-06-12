---
title: "Encrypted home: Use same encryption parameters on two machines"
date: 2013-07-11
forum: Security
---

### Post by kkjaergaard on 2013-07-11
How can I encrypt two different home directories (on two different machines) with the same encryption parameters?

I want to to this because the two machines are synchronised using Unison ([http://www.cis.upenn.edu/~bcpierce/unison](http://www.cis.upenn.edu/~bcpierce/unison)), and now I add an off-location backup service (3rd machine). If I use the same encryption parameters, the encrypted files would look the same (right?), and I can just synchronise the encrypted files without decryption-encryption processing. Any security issues I should be aware of regarding this?

---

### Post by sudodus on 2013-07-11
The simple solution is to start with a cloned copy. If you have desktop Ubuntu flavour systems, and avoid (or remove) any proprietory drivers, the system is portable. If you want to make the systems different afterwards, more than the MAC address, you can change the computer name in /etc/hostname (and /etc/hosts if it is there).

If the computers are ubuntu servers, it might be more difficult, at least I know that the network settings are not directly portable.

---

