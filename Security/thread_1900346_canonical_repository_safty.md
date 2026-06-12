---
title: "canonical repository safty"
date: 2011-12-26
forum: Security
---

### Post by yashar on 2011-12-26
could i say ubuntu canonical repository near 100% safe? i installed many games from it!!

---

### Post by haqking on 2011-12-26
> **yashar said:**
> could i say ubuntu canonical repository near 100% safe? i installed many games from it!!

99.9%.

Nothing is 100% safe or secure in a networked world.

Anything can become compromised, however there has to be a certain level of trust or networks would never exist.

You SHOULD? be fine ;-)

---

### Post by jerome1232 on 2011-12-26
Well, because of our use of key signing you can be assured what your getting is what Canonical put out there for you to get. I suppose the rest is how paranoid you feel about canonical wanting to pwn their users computers.

In other words I agree with haqking, 99.9999% safe.

---

### Post by a2j on 2011-12-26
is there a threat from MITM attack?

---

### Post by Lars Noodén on 2011-12-26
Minimal threat.  The list of package MD5 checksums is PGP signed.

---

### Post by haqking on 2011-12-26
there is a demo here from dangertux on the subject

[http://dangertux.wordpress.com/2011/11/29/trusted-respitories-not-so-trustworthy/](http://dangertux.wordpress.com/2011/11/29/trusted-respitories-not-so-trustworthy/)

be wary of mirrors ;-)...well not wary but just an example of easy it can be and how things can easily be compromised

---

### Post by Dangertux on 2011-12-26
To answer the question about MITM haqking already posted my article, but I explained the issue with the checks done on the packages there and why MITM is still extremely effective there (as well as in the comments section when someone else asked for clarification).

I would say as long as you're sure it's ACTUALLY Canonical's repo it's fine.

---

### Post by Lars Noodén on 2011-12-26
Am I correct in interpreting the article that the checksum fields are not mandatory in the .deb packages?

---

### Post by Dangertux on 2011-12-26
> **Lars Noodén said:**
> Am I correct in interpreting the article that the checksum fields are not mandatory in the .deb packages?

Correct, if there is a checksum provided it will be checked, if they are not they will not be. Also they are easily altered.

[http://www.debian.org/doc/debian-policy/ch-controlfields.html](http://www.debian.org/doc/debian-policy/ch-controlfields.html)

---

### Post by jerome1232 on 2011-12-26
AFAIK, that is wrong, the packages themselves are signed with a pgp key, only people that have the private key can sign them, if the packages are not found to be signed with the proper key, apt-get will warn you that the packages are unauthenticated.

---

### Post by Telengard C64 on 2011-12-26
> **jerome1232 said:**
> the packages themselves are signed with a pgp key, only people that have the private key can sign them, if the packages are not found to be signed with the proper key, apt-get will warn you that the packages are unauthenticated.

^ this

Cryptographically signed packages aren't a perfect and complete solution, but as part of a larger system of checks they make the overall system much more secure. It's one of the important reasons I stay with *buntu systems; some other distros allow unsigned packages in their main repos.

This is also a good reason to be aware and use caution when adding PPAs. I don't think there is much if any review by Canonical, so it comes down to how much you trust the entity offering the PPA.

Of course if you don't trust Canonical, then you shouldn't be using *buntu anyway.

---

### Post by Dangertux on 2011-12-26
The repository uses a public key for identification, it's stored in the top level directory for anyone who is willing to borrow it. The packages themselves can be signed by you if you modify them. Since the server hosting the key is affected by the MITM condition you are providing the endpoint validation. Try it yourself it's quite amusing. ;-)

Bottom line. Blind trust will always be an easy target.

Oh and if you're still in doubt : [http://www.ubuntu.com/usn/usn-1283-1/](http://www.ubuntu.com/usn/usn-1283-1/)

---

### Post by Telengard C64 on 2011-12-26
> **Dangertux said:**
> The repository uses a public key for identification, it's stored in the top level directory for anyone who is willing to borrow it. The packages themselves can be signed by you if you modify them. Since the server hosting the key is affected by the MITM condition you are providing the endpoint validation. Try it yourself it's quite amusing. ;-)

I was very careful not to imply that the system in place is unassailable. Attacks are possible. It just seems to me that what we have is much better than nothing at all. If you think it could be better, then I'm interested in reading your specific recommendations.

> Bottom line. Blind trust will always be an easy target.

Well ... um ... yeah. PEBCAK seems to be a constant.

---

### Post by jerome1232 on 2011-12-26
> **Dangertux said:**
> The repository uses a public key for identification, it's stored in the top level directory for anyone who is willing to borrow it. The packages themselves can be signed by you if you modify them. Since the server hosting the key is affected by the MITM condition you are providing the endpoint validation. Try it yourself it's quite amusing. ;-)

Bottom line. Blind trust will always be an easy target.

Oh and if you're still in doubt : [http://www.ubuntu.com/usn/usn-1283-1/](http://www.ubuntu.com/usn/usn-1283-1/)

I am not quite following you. You need the private key to sign the package, the public key can only be used to verify that the package was indeed signed by the private key. You cannot use a public key to sign the package.

That bug you linked was only related to apt-get not correctly verifying the host, and it was fixed over 3 months ago.

---

### Post by haqking on 2011-12-26
all debate aside over this and that, the point is nothing is 100% secure, as stated earlier Canonicals repos are likely trustworthy 99.999999% but in a networked world.

The point for the OP was can it be trusted, yes, 99.999999% not 100.

---

