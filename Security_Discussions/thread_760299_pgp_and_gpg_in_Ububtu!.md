---
title: "pgp and gpg in Ububtu!"
date: 2008-04-20
forum: Security Discussions
---

### Post by Ziggy72 on 2008-04-20
I didn't know that both pgp and gpg encoding was available in Ubuntu but this seems to be so.

For example:
I have a file called test.txt which contains a few lines of text.

I use either a command line using gpg or I use the Gnu Privacy Assistant to encrypt it. Both methods produce a file called test.txt.gpg. That's as expected.

Now I use seahorse-tools to encrypt the file. This produces a file called test.txt.pgp. That's not really what I expected. The .gpg and .pgp files are different sizes.

gpg from the command line will extract the .gpg file *and* the .pgp file. This is true for both seahore-tools and Gnu Privacy Assistant as well..

So I'm assuming that seahorse-tools produces 'real' .pgp files - which I find a little surprising since pgp is not available via synaptic, and it is also very interesting to note that both gpg and seahorse-tools  can decrypt both .gpg and .pgp files.

Every day I learn something new!

---

### Post by p_quarles on 2008-04-20
GPG is just the Gnu implementation of OpenPGP, so this is all working as expected. They're not different protocols.

---

