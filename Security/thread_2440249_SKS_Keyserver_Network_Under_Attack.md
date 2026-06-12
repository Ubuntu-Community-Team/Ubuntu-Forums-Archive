---
title: "SKS Keyserver Network Under Attack"
date: 2020-04-07
forum: Security
---

### Post by the-jay on 2020-04-07
This is my first post and I figured this might be the right place to ask my question, if not please let me know.

I read this article [https://gist.github.com/rjhansen/67ab921ffb4084c865b3618d6955275f](https://gist.github.com/rjhansen/67ab921ffb4084c865b3618d6955275f) and I has hoping to find some mitigations solutions from the Ubuntu team for my system, unfortunately I have not found a single thread relating the SKS poisoning, or an official response from Ubuntu/Canonical as to what is doing to address this issue. As I understand it, it affects everyone that uses PGP to verify ISO's, packages email, etc. So I'm hoping a Ubuntu DEV (if they hangout here) or a knowledge personal can comment as to what steps if any Canonical is taking to address this issue. 
What steps a user can take to be confident that if we synch PGP keys from Ubuntu SKS server that they have not been poisoned?
Can we still trust in verifying the ISO through the SKS infrastructure to verify our downloads?
How can we check if any PGP keys that we might have downloaded could be corrupted?

Thanks

---

### Post by EuclideanCoffee on 2020-04-07
This is exactly the question I was asked. Are we colleagues?

The article you posted is a bit vague in describing the actual problem. It's biased too. Here's a real attempt to resolve the SKS problem.

[https://blogs.gentoo.org/mgorny/2019/07/04/sks-poisoning-keys-openpgp-org-hagrid-and-other-non-solutions/](https://blogs.gentoo.org/mgorny/2019/07/04/sks-poisoning-keys-openpgp-org-hagrid-and-other-non-solutions/)

Since Debian / Ubuntu distribute their keys on various servers and on the distribution, it is less likely SKS will actually affect the packages each distribution is responsible for securing and sending. There are also secure apt, that checks layers of signatures: [https://wiki.debian.org/SecureApt](https://wiki.debian.org/SecureApt)

With so much complexity, you'll likely see something amiss when you're running `apt install` before you're compromised.

But things do go wrong. This is why you should enable apparmor.

Snap also may be Ubuntu's ultimate solution, as it distributes software differently than apt.

---

### Post by the-jay on 2020-04-08
> **EuclideanCoffee said:**
> This is exactly the question I was asked. Are we colleagues?

The article you posted is a bit vague in describing the actual problem. It's biased too. 

thanks for the reply. Well I guess its good someone is asking, but no we are not colleagues. The article I listed is the original one from one of the devs who got his PGP keys spammed. Have you by any chance made the key server change as per the recommendation from the article?I read the article from Gentoo, really good and informative.

I didn't know that about Debian will have to do some reading today, in the meantime apparmor and secure apt from Debian the same thing?

By snaps you mean this [https://ubuntu.com/tutorials/create-your-first-snap#1-overview](https://ubuntu.com/tutorials/create-your-first-snap#1-overview)

---

### Post by EuclideanCoffee on 2020-04-08
Ubuntu is a downstream distribution, so it uses Debian's software. Everything that is Debian is what Ubuntu is, essentially. Ubuntu builds ontop of Debian with various patches, which they document on their wiki.

Yes, that tutorial will give you some ideas. Check out the official website: [https://snapcraft.io/](https://snapcraft.io/)

Concerning the server, I have made no changes personally, but I don't think Ubuntu needs to make changes, as they distribute keys very differently.

---

### Post by the-jay on 2020-04-09
> **EuclideanCoffee said:**
>  Concerning the server, I have made no changes personally, but I don't think Ubuntu needs to make changes, as they distribute keys very differently.

Can you elaborate more? I though for example if verifying the ISO it would all be done through the keyserver network

---

### Post by EuclideanCoffee on 2020-04-09
> **the-jay said:**
> Can you elaborate more? I though for example if verifying the ISO it would all be done through the keyserver network

You certainly could, but ISO is verified with an encryption hash. Every file can be checked this way. It's called a checksum.

Then all packages are verified with a key that is preloaded into the ISO installation.

---

