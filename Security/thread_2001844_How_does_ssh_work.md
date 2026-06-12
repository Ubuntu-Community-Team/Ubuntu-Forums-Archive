---
title: "How does ssh work"
date: 2012-06-11
forum: Security
---

### Post by piriton on 2012-06-11
[LEFT]How does ssh work?

[/LEFT]
I know that it's a "set of [computer programs]("http://en.wikipedia.org/wiki/Computer_program") providing [encrypted]("http://en.wikipedia.org/wiki/Encryption") communication sessions over a [computer network]("http://en.wikipedia.org/wiki/Computer_network") using the [SSH]("http://en.wikipedia.org/wiki/Secure_Shell") protocol."


But I am looking for deeper technical information on the internals, including some information on the key exchange and encryption protocols.


I am not looking for a list of the features, that is easy to find.

---

### Post by sanderj on 2012-06-11
See [http://en.wikipedia.org/wiki/Secure_Shell#Internet_standard_documentation](http://en.wikipedia.org/wiki/Secure_Shell#Internet_standard_documentation) and [http://www.linuxjournal.com/article/9566](http://www.linuxjournal.com/article/9566)


HTH

---

### Post by Cheesemill on 2012-06-11
There's some good info here:
[https://en.wikibooks.org/wiki/OpenSSH](https://en.wikibooks.org/wiki/OpenSSH)

Also for the full specification you can go to the Open SSH web site:
[http://www.openssh.org/specs.html](http://www.openssh.org/specs.html)

---

### Post by papibe on 2012-06-11
Hi piriton.

For a deeper description of the SSH protocol, you can go to the OpenSSH project home page. There you can find the [SSH protocol specifications]("http://www.openssh.org/specs.html").

Another step would be to read and analyse the source code itself which can be obtain either on the same site, or at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") (for the specific version that you may be using).

I hope that helps.
Regards.

---

### Post by HermanAB on 2012-06-12
It is all in the Snail book:
[http://www.snailbook.com/](http://www.snailbook.com/)

---

