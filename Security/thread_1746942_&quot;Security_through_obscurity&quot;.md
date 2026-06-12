---
title: "&quot;Security through obscurity&quot;"
date: 2011-05-02
forum: Security
---

### Post by Blutkoete on 2011-05-02
Hello!

This question might sound a little bit stupid ... ok.

Most people state (and I agree with them) that security through obscurity is a bad thing. But where is the border line between "security through obscurity" and good "algorithm-built-in" security?

I mean, even the greatest non-revertable algorithm that encrpyts my mail with a 200-digit-password is kind of "security through obscurity" as it's only secure as long as I keep something (my password and/or private key) hidden, which is - on a very theoretical, but fundamental level - kind of the same as keeping the encryption algorithm hidden. In both cases I'm hiding something that is elementary for the decryption process.

I know that in the one case only I'm compromised while in the other case everyone using the system is compromised, but still: Isn't in the long run every encryption or security system "security through obscurity" because in the end all those systems work by (sometimes more, sometimes less) requiring some knowledge to be obscure for the attacker?

I know, this question has not much to do with real-life security, but I was thinking about it lately.

Thank you,

Blutkoete

---

### Post by mikewhatever on 2011-05-02
It really depends on how far you chose to abstract things. Normally, security through obscurity doesn't apply to simply concealing something, but rather to situations when developers know about security flaws, but won't fix them, because, supposedly, these flaws are obscure enough.

---

### Post by Blutkoete on 2011-05-02
> **mikewhatever said:**
> It really depends on how far you chose to abstract things. Normally, security through obscurity doesn't apply to simply concealing something, but rather to situations when developers know about security flaws, but won't fix them, because, supposedly, these flaws are obscure enough.

Ah, ok. Thank you for the clarification! I always thought security through obscurity is more the "Our cave is secure 'cause noone knows where it is and even if they find it, they'll have to say 'Open Sesame'!". What you say sounds more like "Hey, of course the backdoor is never locked, but noone knows that.".

---

### Post by rookcifer on 2011-05-02
> **Blutkoete said:**
> I mean, even the greatest non-revertable algorithm that encrpyts my mail with a 200-digit-password is kind of "security through obscurity" as it's only secure as long as I keep something (my password and/or private key) hidden, which is - on a very theoretical, but fundamental level - **kind of the same as keeping the encryption algorithm hidden.** 

No, it's not the same thing.  Any encryption algorithm whose strength depends on keeping the algorithm itself secret violates one of the most important maxims in cryptography known as [Kerckhoff's principle.]("https://secure.wikimedia.org/wikipedia/en/wiki/Kerckhoffs%27s_Principle")

> I know that in the one case only I'm compromised while in the other case everyone using the system is compromised, but still: Isn't in the long run every encryption or security system "security through obscurity" because in the end all those systems work by (sometimes more, sometimes less) requiring some knowledge to be obscure for the attacker?

Crypto, by definition, means one is trying to keep something confidential from other people.  And in order to keep something enciphered one must have a key to unlock it (if you can't unlock it, what's the point?)  There's no way around that.  

> I know, this question has not much to do with real-life security, but I was thinking about it lately.

No, it's a good question and one that cryptographers are well aware of.  That's why any cryptographer worth his salt will tell you that a good cryptosystem depends solely on the secrecy of the **key** and not the algorithm itself.  As the God of information theory, Claude Shannon, said "the enemy knows the system."  We always have to work under that assumption.

---

### Post by blind2314 on 2011-05-02
> **Blutkoete said:**
> Ah, ok. Thank you for the clarification! I always thought security through obscurity is more the "Our cave is secure 'cause noone knows where it is and even if they find it, they'll have to say 'Open Sesame'!". What you say sounds more like "Hey, of course the backdoor is never locked, but noone knows that.".
 
 
He is right, but in a way so are you. The way I've always thought about it and had it explained to me, "security through obscurity" is a means of saying "Hey, don't worry. While it's true that 75% of our security measures are nearly worthless, there are so many of them that the vulnerability is practically hidden. Also, those other 25% will keep them out, so why worry?".
 
Usually security by obscurity is used in moderation with "security through design", which actually takes the steps to harden and/or fix the vulnerabilities known either in the design process itself or with patches once the product is released. A good mix of a both is what a lot of developers and companies follow.

---

### Post by pricetech on 2011-05-02
My understanding of "security through obscurity" is best explained with an example or two;

I don't want my FTP server hacked so I put it on port 50021.
I'm concerned about VNC's weak security so I configure it to use 55900

My FTP server / VNC server is no more secure, but maybe you won't find it.

I don't think it's a bad idea to use non standard ports per se, just don't count on that as a means of securing your server.

Planting a hedge in front of a side entrance keeps it from being seen, but is not an acceptable substitute for locking the side door.

---

### Post by aysiu on 2011-05-02
The two are conceptually different.

Security by obscurity means that the target itself is unknown or seen to be not worth the effort for the malicious parties.

It doesn't mean that a password is unknown.

---

### Post by brian_p on 2011-05-03
> **blind2314 said:**
> 
 
Usually security by obscurity is used in moderation with "security through design", which actually takes the steps to harden and/or fix the vulnerabilities known either in the design process itself or with patches once the product is released. A good mix of a both is what a lot of developers and companies follow.

Intellectual and commercial dishonesty is alive and well, then. Pretend security is mixed with (possible) real security and we are expected to trust an industry which promotes such a practice.

---

### Post by blind2314 on 2011-05-03
> **brian_p said:**
> Intellectual and commercial dishonesty is alive and well, then. Pretend security is mixed with (possible) real security and we are expected to trust an industry which promotes such a practice.
 
Whether it can be called "pretend" or not is another issue; however, the fact is that it works if it is done correctly. At the company I'm currently employed with we use the latter approach (security by "design") because we have the resources and means available to us to do so. At the few conferences I've been to (note please, *few*) I met quite a few lecturers on security that don't consider it a bad practice, or something that is dishonest. The main caveat to their point, and mine, is that it must be done correctly. If you build your entire security around smoke and mirrors and the fact that surely no one will notice it (Sony?), then you're absolutely right, the customer should not trust them.

---

### Post by rookcifer on 2011-05-03
> **blind2314 said:**
> Whether it can be called "pretend" or not is another issue; however, the fact is that it works if it is done correctly. At the company I'm currently employed with we use the latter approach (security by "design") because we have the resources and means available to us to do so. At the few conferences I've been to (note please, *few*) I met quite a few lecturers on security that don't consider it a bad practice, or something that is dishonest. The main caveat to their point, and mine, is that it must be done correctly. If you build your entire security around smoke and mirrors and the fact that surely no one will notice it (Sony?), then you're absolutely right, the customer should not trust them.

I think this conversation has gotten off-topic a bit from what the OP was asking.  It appears to me he was asking specifically about passwords and encryption algorithms, not software development.  I think I answered his question about as well as could be answered with my explanation of Kerckhoff's principle.  Basically: security through obscurity is no security at all.  Security through obscurity has absolutely *no place* whatsoever in crypto.

---

